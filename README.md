Statusboard [![Build Status](https://secure.travis-ci.org/assimovt/statusboard.png)](http://travis-ci.org/assimovt/statusboard)
===========

Statusboard is a simple Sinatra/SQLite powered application to track availability of remote nodes.
The remote node can be any application that responds with 200/4xx (up/down) HTTP status.

Application currently supports:

* Calculation of uptimes of individual nodes and total.
* Retrieval of RSS feed from any external service explaining the reason of the downtime.
* Viewing the past uptimes defined by a date range (date picker).
* Sending a "panic" email when there is a downtime.

**Note:** Downtime means when all nodes are down at a given time.


## Screenshots

### When the service is up

![status_board_status_up](http://github.com/assimovt/statusboard/raw/master/public/images/status_board_status_up.png)

### When the service is down

![status_board_status_down](http://github.com/assimovt/statusboard/raw/master/public/images/status_board_status_down.png)

### Service uptime

![status_board_uptime](http://github.com/assimovt/statusboard/raw/master/public/images/status_board_uptime.png)

## Quick start

* Clone the repository:

`git clone git://github.com/assimovt/statusboard.git`

* Copy and configure `status.yml` following comments in the file:

`cp config/status.yml.sample config/status.yml`

* Configure cron job to fetch the statuses:

```
# fetch status of the nodes every 5 minutes
*/5  * * * * cd PATH_TO_THE_APP && RACK_ENV=production rake status:update
```

* Export `production` environment variable:

`export RACK_ENV=production`

* Run bundle and database migrations:

```
bundle install
rake db:migrate
```

* Start the app:

`bundle exec rackup`

* The app should be running on port 9292 at configured host (status.yml).


## License

(The MIT License)

Copyright © 2011 Tair Assimov, Maxim Dolgobrod, Tommi Siivola

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

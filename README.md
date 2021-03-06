# ngx_http_reqstat_module
This is compatible with nginx from tengine http_reqstat_module. You can refer to [tengine document](http://tengine.taobao.org/document_cn/http_reqstat_cn.html)
or config as the following:

````
http {

    req_status_zone server "$host,$server_addr:$server_port" 10M;
    req_status_zone_add_indicator server $limit;

    server {
        location /us {
            req_status_show;
            req_status_show_field req_total $limit;
        }

        set $limit 0;

        if ($arg_limit = '1') {
            set $limit 1;
        }

        req_status server;
    }
}
````

Compatibility
-----------
Unfortunately, tengine forked by nginx has changed some core data source of nginx. These feature are not allowed as the following:

0. bytes_in
1. bytes_out

Contributing
------------

To contribute to ngx_http_reqstat_module, clone this repo locally and commit your code on a separate branch.


Author
------

> GitHub [@detailyang](https://github.com/detailyang)

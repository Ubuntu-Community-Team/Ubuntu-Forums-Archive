---
title: "Error log: upstream timed out (110: Connection timed out) on Nginx"
date: 2015-09-29
forum: General Help
---

### Post by Nayara on 2015-09-29
[FONT=Helvetica Neue][COLOR=#676767][FONT=proxima-nova]Please... I need help!!! My script don't works! My script in php only load for serveral time and afterwords appears that message:[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]---------------------------------------------------------------------[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]An error occurred.[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]Sorry, the page you are looking for is currently unavailable.[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]Please try again later.[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]If you are the system administrator of this resource then you should check the error log for details.[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]Faithfully yours, nginx.[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]---------------------------------------------------------------------[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]In /var/log/nginx/nginx_error.log show me that error:[/FONT][/COLOR]


[COLOR=#676767][FONT=proxima-nova]---------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova][error] 2019#0: *1 **upstream timed out (110: Connection timed out) while reading response header from upstream, client: x.x.x.x, server: localhost, request: "GET /sistema-10-reais/ HTTP/1.1", upstream: "fastcgi://unix:/var/run/php5-fpm.sock", host: "x.x.x.x.x"**[/FONT][/COLOR][B]
[COLOR=#676767][FONT=proxima-nova]root@server:/var/log/nginx#[/FONT][/COLOR][/B]
[COLOR=#676767][FONT=proxima-nova]---------------------------------------------------------------------[/FONT][/COLOR]


[COLOR=#676767][FONT=proxima-nova]when is x.x.x.x is IP.[/FONT][/COLOR]

[COLOR=#676767][FONT=proxima-nova]I am using nginx on ubuntu 14.04.[/FONT][/COLOR][/FONT]

---


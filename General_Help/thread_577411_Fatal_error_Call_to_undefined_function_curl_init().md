---
title: "Fatal error: Call to undefined function curl_init()"
date: 2007-10-16
forum: General Help
---

### Post by nikolas22t on 2007-10-16
I got this error, any idea what may cause it ? the same script on another server is working fine....



> Fatal error: Call to undefined function curl_init() in /var/www/public_html/modules/mod_euro_exchangerate.php on line 31



if i give the curl command for a website the site is responding

> root@pc2:~# curl -I [www.mplampla.com](www.mplampla.com)
HTTP/1.1 200 OK
Date: Tue, 16 Oct 2007 12:23:23 GMT
Server: Apache
X-Powered-By: PHP/5.2.4
Set-Cookie: 5a5a7ebbd8968e9d4856e60e9a38f079=-; path=/
Expires: Mon, 26 Jul 1997 05:00:00 GMT
Last-Modified: Tue, 16 Oct 2007 12:23:23 GMT
Cache-Control: no-store, no-cache, must-revalidate
Cache-Control: post-check=0, pre-check=0
Pragma: no-cache
Set-Cookie: JATheme=mplampla; expires=Sun, 05-Oct-2008 12:23:23 GMT; path=/
Set-Cookie: ColorCSS=default; expires=Sun, 05-Oct-2008 12:23:23 GMT; path=/
Set-Cookie: ScreenType=wide; expires=Sun, 05-Oct-2008 12:23:23 GMT; path=/
Set-Cookie: FontSize=3; expires=Sun, 05-Oct-2008 12:23:23 GMT; path=/
Connection: close
Content-Type: text/html


---


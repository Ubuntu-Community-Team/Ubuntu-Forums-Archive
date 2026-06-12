---
title: "Nginx, rewrite extension, seeking advice"
date: 2018-05-17
forum: General Help
---

### Post by Drenriza on 2018-05-17
Hi all
I currently seek advice to reverse proxy (Nginx) rewrite and forward to tomcat 8.5.
I also have the question at [https://serverfault.com/questions/912012/nginx-rewrite-jsp-extension-and-proxy-to-tomcat](https://serverfault.com/questions/912012/nginx-rewrite-jsp-extension-and-proxy-to-tomcat) but so far i have not had luck with receiving any feedback / advice / help at all,
and hope someone here has some Nginx experience and can help me out a bit.

Currently i am using Nginx as my reverse proxy to serve .jsp pages from Tomcat.
Nginx takes care of HTTPS termination, GZIP, serve requests to Tomcat and more.

What i am trying to do now, is to remove my .jsp extension from the url when serving the response to the client.

The issue
Step 1
Nginx needs to check the URL on all requests, and see if this contain a .do as the extension.
If it does, Nginx substitutes .do with .jsp and serve it to Tomcat.

Step 1.1
Also If the URL has no extension, Nginx needs to add .jsp as the extension

Step 2
On the response from Tomcat Nginx removes the .jsp extension and serves it to the client.

I have tried to solve this myself, but have not really achieved this.

Code
```

server {
        listen 443 ssl;
        server_name www.test.local test.local;

        location / {
                if ($request_uri ~ ^/(.*)\.jsp$) {
                        return 302 /$1;
                }
                try_files $uri.jsp @proxy;
        }

        location @proxy {
                proxy_pass http://websites/;
                include proxy_params;
        }
}
```

Nginx removes the .jsp extension by forcing the client to make a total of two requests, but Nginx also sends the request to  Tomcat without the .jsp extension,
so tomcat does not know what to look  for and returns a 404.


  As far as i can tell, Nginx is not asking Tomcat **do you have a $uri.jsp page** but is instead asking
if Tomcat [B]has a $uri page (without .jsp extension).
[/B]

  As far as i can read and understand try_files syntax is

  ```
try_files [Location[file, folder]] [fallback[file, folder, HTTP code]]


```  But the official documentation does not say (as far as i can find)  how to instruct Nginx to (in this case) ask the proxy for the
different  files and folders to **try**, but is instead quering its own local root location for $uri.jsp and than using @proxy as fallback.

Any and all advice would be most welcome

---

### Post by dino99 on 2018-05-17
The nginx is a malware, also known as browser hijacker. Usually, most of the search engines are legitimate and not harmful; however, most of the browser hijackers are developed with one goal, which is to generate advertising revenues. Innocent users will be tricked into clicking on displayed ads or advertising banners, and the owners of malware will earn a fee for every click. You may find a lot of reports about the nginx and how it changes browser setting, installs unwanted toolbars without users&#8217; consent, and how hard is to remove it from the system. All of that is done in order to guarantee the advertising earnings for the search engines.

---

### Post by Drenriza on 2018-05-17
Weeee talking about the same thing? :)

> nginx - small, powerful, scalable web/proxy server

---


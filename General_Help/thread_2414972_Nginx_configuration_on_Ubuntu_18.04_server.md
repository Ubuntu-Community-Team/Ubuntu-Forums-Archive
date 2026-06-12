---
title: "Nginx configuration on Ubuntu 18.04 server"
date: 2019-03-18
forum: General Help
---

### Post by mathewfer2 on 2019-03-18
Hi 

I am running Nginx on Ubuntu 18.04. I have the below starting configuration which will take HTTP to HTTP. This is working fine for webmail on this server.

Current working configuration:

```
# HTTPserver {
    # Listen on ipv4
    listen 80;

    server_name _;

    # Redirect all insecure http:// requests to https://
    return 301 https://$host$request_uri;
}
```


Now I want to change it so that any traffic to mail.mydomain.net from HTTP to HTPS and [www.mydomain.net]("http://www.mydomain.net") to different IP/server on the same network. I change the Nginx configuration like below but it did not direct the [www.mydomain.net]("http://www.mydomain.net") to that "webserver_IP_Address".

How can I change this configuration to get this done?

New code that did not work still:

```
# HTTPserver {
    # Listen on ipv4
    listen 80;


    server_name mail.mydomain.net;
    # Redirect all insecure http:// requests to https://
    return 301 https://$host$request_uri;


    # Redirect www to diffrent IP running a different server
    server_name www.mydomain.com;
        location / {
                proxy_pass http://<webserver_IP_Address>:80;
                proxy_set_header Host www.mydomain.net;
        }
}
```

Mathew

---

### Post by TheFu on 2019-03-18
I'm surprised the 1st config works. There are problems with it that would break my server.

Not enough information to help. Sorry.  Any other websites involved? Any other ports being listened?  Any reverse proxying?

You can use the -T switch to see the order that config files are loaded under nginx.
For example, 

```
sudo nginx -c /etc/nginx/nginx.conf -T
```

You'll need multiple stanzas. Some people would setup different sites-available/ config file for each server, each port.  That is up to you.  I put the 80-->443 redirect and the 443-SSL stuff into a single file.  If the webapp is on the same system, my configs are different than if they are on another machine, perhaps one that doesn't have direct internet access.  

Things can get complicated, quickly.

Also, may want to hold off on using the 301 redirect until everything is working.  Use a 302 for now.  It will make troubleshooting much easier since the client-side won't think the redirect is permanent while you are working through the reconfiguration.  Once the client sees a 301, it will directly try to go to the redirect page, skipping the original.  Makes troubleshooting next to impossible.

Also, use curl, not a browser, to follow the redirections.  Much easier to see what is really happening.
And check the log files. You're nginx config didn't setup any log files - might want to setup access and error logs. Hard to troubleshoot without those too.

---


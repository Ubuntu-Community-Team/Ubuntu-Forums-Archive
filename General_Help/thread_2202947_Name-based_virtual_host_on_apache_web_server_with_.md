---
title: "Name-based virtual host on apache web server with static ip address"
date: 2014-01-31
forum: General Help
---

### Post by adamjedgar on 2014-01-31
i have read a little about running multiple websites in a **namebased virtual host** environment using **apache2.** However, what if i am running a test system here at home on my **_static ip address_**?

How do i host multiple test websites at home with my static ip address?

System specs

static ip address
Win 7x64 host
Vm-virtual box + Ubuntu 13.04x64 + Apache 2

I have two Wordpress test sites i am developing for clients. 

I would like clients to be able to access those websites during development so they may have input prior to uploading finished product to webhosting provider.

---

### Post by btindie on 2014-02-01
I suppose you're actually asking "How do I expose my internal web server to the internet?" ?

Is your Ubuntu VM running under NAT on VB? Or does it have an IP address on the same network as your windows box?

If your Ubuntu VM is on your internal network you'll just need to configure your router to forward port 80 (or alternative port) to it's internal IP and port 80. If on the other hand, VB is doing NAT, you need to configure your router to forward port 80 to your windows box and get VB to forward that to your VM's NAT'ed IP. That'll set up your IP connectivity.

If you've got shell access to a server on the internet, you'd be able to test the connectivity with "curl http://1.2.3.4:8080" which would just request the default page from the default site on Apache. Another handy thing with *curl* is that you can override or fake what would be returned by DNS. So you could do "curl --resolve dev.mydomain.com:8080:1.2.3.4 http://1.2.3.4:8080" to test that it's returning the correct page without having to set up DNS first.

You may want to use an alternative port for external access, such as 8080, depending on your router, but that can still be forwarded to port 80 on your web server. So from home you wouldn't need to specify the port.

Then you just need to configure Apache for named based virtual hosts - this is what appears in the HTTP GET Host header that's sent to the server.

You'll also need to set up DNS entries for it using your static public IP address. And so you can access it locally, just add an entry for the hostname (e.g. dev.mydomain.com) and your private IP to your /etc/hosts file, or on windows which is a bit more convoluted - see [here]("http://helpdeskgeek.com/windows-7/windows-7-hosts-file/"). That overrides the public DNS entry so it uses your internal private IP for that hostname.

---

### Post by SeijiSensei on 2014-02-01
You don't need to expose the server to the Internet just to test out name-based virtual hosting.

First, you should read the relevant sections of the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/web-servers.html") and the [documentation at apache.org]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

If you stay on your local network, you'll need to use entries in /etc/hosts so that whatever server name you give to the virtual host can be reached by your local computers.  (Windows clients would use its [equivalent host file]("http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system").)  Suppose your server is on 192.168.1.1.  Then in a client's /etc/hosts, you'd want entries like:
```
192.168.1.1  www.mydomain.net  www.myotherdomain.com 
```
Then if the server is configured correctly with separate <VirtualHost> definitions for each name,  you should be able to enter [http://www.mydomain.net/](http://www.mydomain.net/) into the client's browser and see the appropriate web site.

---


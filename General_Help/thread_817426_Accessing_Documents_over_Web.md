---
title: "Accessing Documents over Web"
date: 2008-06-03
forum: General Help
---

### Post by DiGiTY on 2008-06-03
I have a Ubuntu 7.10 home server. I've been playing with Windows Home Server a little bit and I was wondering how do I go about setting up my Linux server to access My Documents remotely like WHS does with a Web UI (web based file manager over HTTP/HTTPS)??

---

### Post by nhandler on 2008-06-04
You can set up an Apache2 webserver on ubuntu very easily. Either use Synaptic or enter 'sudo apt-get install apache2' in a terminal. This should install the server. Now, you can place the files you want to access remotely in /var/www (you can change the folder the server looks for files in in /etc/apache2/apache2.conf). Now, assuming your firewall is configured to allow inbound traffic on port 80, you should be able to enter 'localhost' or your IP address in the address bar of firefox (or any other browser). You should then see a list of files in /var/www. You can then click on a file to either download it or view it in the browser (it depends on the type of file).

---

### Post by DiGiTY on 2008-06-07
i have apache already set up, I'm not talking about that. I'm talking about making my own personal web based file mananger or personal online storage system like a .Mac account (which is a web UI over WebDAV) or like box.net, xdrive, idrive, Amazon S3, mediamax, etc.

ya digg?

---

### Post by komputes on 2008-07-05
I can digg it ma brotha check this super fly link out:
[https://wiki.ubuntu.com/Webuntu](https://wiki.ubuntu.com/Webuntu)

---


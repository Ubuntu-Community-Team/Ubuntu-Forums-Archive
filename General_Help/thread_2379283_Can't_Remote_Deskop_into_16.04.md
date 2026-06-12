---
title: "Can't Remote Deskop into 16.04"
date: 2017-12-03
forum: General Help
---

### Post by mjwestkamper on 2017-12-03
The install was the default options from the LTE image. 
I am trying to set up the RDT to allow me to access the desktop. I have done this many times with older versions, however with 16.04 I can't seem to make it work.
I have tried several of the work-around's to no avail. I have chased this problem thru the usual web searches and forums. Apparently its a known issue. My request then is: Can this version be made to work? If not is there a newer version that works well. In the end this box gets sent half way around the world and operated remotely. Any guidance will be greatly appreciated. -Mike

---

### Post by gemmathetechie on 2018-01-01
Would you consider using SSH over a remote desktop connection?
Yes you won't be able to use the GUI based applications but for basic usage (dependant on your terminal knowledge) this may be a viable solution!

---

### Post by HermanAB on 2018-01-02
Sure you can use GUI apps over ssh:
$ ssh -Y -C -c blowfish user@server "gedit filename"

---

### Post by dragonfly41 on 2018-01-02
Here is one experiment to try instead of remote desktop  ... but note that some pro administrators consider webmin to be a vector for hackers.

Install webmin on your remote server ... sudo apt install webmin

Install PuTTY on your local desktop.

read tip here ... [https://blog.jamesbayley.com/2014/02/02/accessing-webmin-as-httplocalhost10000-through-an-ssh-tunnel/](https://blog.jamesbayley.com/2014/02/02/accessing-webmin-as-httplocalhost10000-through-an-ssh-tunnel/)

Manage remote webmin through [https://localhost:10000](https://localhost:10000) on your local desktop.

In fact I also use webmin for local development.

...

Another approach would be to use ansible scripts.

---


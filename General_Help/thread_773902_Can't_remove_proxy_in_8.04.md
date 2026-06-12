---
title: "Can't remove proxy in 8.04"
date: 2008-04-29
forum: General Help
---

### Post by 130R on 2008-04-29
When I installed 8.04 I went into advanced and setup a proxy, however now I don't need one so I have done:

System - Preferences - Checked "direct internet connection"

And in Synaptic Package Manager:

Settings - Preferences - Network - Checked "direct connection to the internet"

However when I try and reload in Synaptic Package Manager:

"Failed to fetch [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) ... Unable to connect to proxy.whatever 8080"

Why is it still trying to use the proxy!? 

Is there some file I can manually edit with vi or whatever to remove this proxy permanently? I can't see anywhere else to do it in using the GUI?

:confused:

---

### Post by 130R on 2008-04-29
Ok got it:

sudo vi /etc/apt/apt.conf

Delete the Acquire::Http::Proxy line.

I think this is a bug because this should surely be removed by the Synaptic Package Manager when you change the network settings.

---

### Post by kirenpillay on 2008-12-26
This bug is still in 8.10.

---

### Post by brunods on 2009-02-26
It still searches thr proxy even after I removed it from apt.conf

No idea

---

### Post by loneowais on 2009-04-20
It's in Jaunty Beta too...

---

### Post by kewp on 2009-05-07
i've had the same problem in 8.04 and 8.10.

the problem is that the http_proxy environment variable is set each time you run apt-get. you can force it not to use it by saying 'http_proxy= sudo apt-get install ...' but i don't know how stop it permanently (saying 'env -u http_proxy' doesn't work)

---

### Post by ovcica on 2009-07-21
I have the same problem in 9.04. 
Removing the line from /etc/apt/apt.conf file helps for some applications.

---

### Post by tkoWD on 2009-11-13
SOLVED(tested on 9.04):

to show proxy type (no qoutes): "set | grep -i proxy"
to remove type(no qoutes): "http_proxy="

---


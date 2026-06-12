---
title: "webmin, how do you use it what URL to type in?"
date: 2008-05-22
forum: General Help
---

### Post by sdowney717 on 2008-05-22
[http://www.webmin.com/docs.html](http://www.webmin.com/docs.html)

cant find this anywhere. The basic simple stuff is ignored and kept secret. I feel like people just assume you know how to put the key in the ignition, but if you have never been in a car this is impossible.
I was looking to try this out vsftpwebmin, but dont have a cluse how to even make it start up.

[http://freshmeat.net/projects/vsftpdwebmin/](http://freshmeat.net/projects/vsftpdwebmin/)
[http://www.debianadmin.com/fast-and-secure-ftp-server-with-vsftpd-in-debian.html](http://www.debianadmin.com/fast-and-secure-ftp-server-with-vsftpd-in-debian.html)

---

### Post by wdaniels on 2008-05-22
Well, first you need to install it:

```
wget http://kent.dl.sourceforge.net/sourceforge/webadmin/webmin_1.410_all.deb
sudo dpkg -i webmin_1.410_all.deb
```

By default webmin will listen on port 10000 using https, so you can use a browser to go to:

[https://localhost:10000](https://localhost:10000)

...from there you can login and install that webmin module you want to use (or maybe it's part of the default set, I don't know).

---

### Post by sdowney717 on 2008-05-22
It is not right that documentation has to be drawn from all over the web to try and figure out how to get something working

[http://www.sitepoint.com/article/webmin-linux-administration-1](http://www.sitepoint.com/article/webmin-linux-administration-1)
yes, I found out I can login using 
[https://scott-desktop:10000/](https://scott-desktop:10000/)
I had to permanently override a security certificate setting to proceed.

Ok, it is running, now I wonder how to get that vsftpd webmin module installed?

---

### Post by wdaniels on 2008-05-22
> **sdowney717 said:**
> It is not right that documentation has to be drawn from all over the web to try and figure out how to get something working

Maybe, but it's also not right that everybody should write step-by-step instructions for every level of user experience and distribution all of the time - the webmin site points to a debian package and from there on it's a relatively generic process. The deb package itself (and also the tar.gz source installation I seem to recall) tells you the URL you need at the end of the installation - perhaps you don't see this if you used a GUI package installer or something, I don't know, but it's clearly not a case that the information is hard to find.

Accepting the self-signed certificate is nothing to worry about - there is no reason that anybody would want or need to pay for a 3rd party verified certificate for something running on their own machine. The point of webmin using a secure protocol is only so that nobody could capture your admin password just by monitoring packets on your network.

As for installing the module you want, there is some menu option for webmin configuration, you go to modules section and there is an install option somewhere from there. You should be able to just give it the link to download the module itself and when it's done you'll see the new module available in the relevant menu.

---

### Post by sdowney717 on 2008-05-22
using the package manager, you dont see any of this.
anyway, it is bad to not give clear instructions on how to do something.

You run into this a lot, sites written by programmers that assume basic understanding of their program when really, you get a new person coming in and it is impossible even if they have the key to put the key in the ignition since they cant even find the key hole..

found you can install this from the *.gz file into webmin

after you install the vsftpd module, hit the refresh modules button and it will show up under servers

---

### Post by wdaniels on 2008-05-22
> **sdowney717 said:**
> you get a new person coming in and it is impossible even if they have the key to put the key in the ignition since they cant even find the key hole..

True enough, but you did find the keyhole easily enough just by asking didn't you? You shouldn't expect people who are doing stuff purely for the joy of it to lay everything out plain and ready for you. Most try to anyway, but it's not a lot to ask that you might need to mix a little of your own labor into it.

If you want to comment to the Webmin developers that following the process you took, it is not then clear what URL to use, I'm sure they will take the input on-board. Probably it has been mentioned before but often it's just a case of catching the attention of the right person at the right time to get something done about these things.

But when you launch immediately into a complaint and say that something is "not right" or "bad" it only tends to get people's backs up. A fairly trivial matter of tone perhaps, but also a general courtesy toward people who are only trying to give something back.

---

### Post by sdowney717 on 2008-05-22
I appreciate the effort these are free programs after all.

Say, do you know why my vsftpd is not listing any files when I go to the url in firefox?
It shows only the headers

config file in /etc/vsftpd.conf
served files are in /var/ftp
I did sudo chmod -R 755 /var/ftp

# Access rights
anonymous_enable=YES
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000
# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
# Performance
one_process_model=YES
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000

---

### Post by bodhi.zazen on 2008-05-22
> **sdowney717 said:**
> using the package manager, you dont see any of this.
anyway, it is bad to not give clear instructions on how to do something.

You run into this a lot, sites written by programmers that assume basic understanding of their program when really, you get a new person coming in and it is impossible even if they have the key to put the key in the ignition since they cant even find the key hole..

found you can install this from the *.gz file into webmin

after you install the vsftpd module, hit the refresh modules button and it will show up under servers

> **sdowney717 said:**
> It is not right that documentation has to be drawn from all over the web to try and figure out how to get something working

[http://www.sitepoint.com/article/webmin-linux-administration-1](http://www.sitepoint.com/article/webmin-linux-administration-1)
yes, I found out I can login using 
[https://scott-desktop:10000/](https://scott-desktop:10000/)
I had to permanently override a security certificate setting to proceed.

Ok, it is running, now I wonder how to get that vsftpd webmin module installed?

Good points. Are you willing to be part of the solution ? If so, now that you have it figured out, you could contribute to the cause by writing a how-to on the ubuntu wiki. We would all benefit.

Otherwise I suggest you bring your concerns re: documentation to the webmin project.
 There is a ton of information re webmin :

[http://swelltech.com/support/webminguide/](http://swelltech.com/support/webminguide/)

The beauty of linux servers is they can be managed from the command line. Most servers are configured by editing the config files which you can do via ssh ...

---


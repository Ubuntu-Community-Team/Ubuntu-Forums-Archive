---
title: "removing nginx from Feisty"
date: 2007-05-24
forum: General Help
---

### Post by spoken4 on 2007-05-24
Just wondering why I can't remove nginx by apt-get. (R51 IBM Laptop)
Same thing happened with Moodle on Dapper,

I stopped the service with cbe@LAP-cbe:~$ sudo /etc/init.d/nginx stop
Stopping nginx: nginx.

then tried to remove it, but I get error exits - see below

cbe@LAP-cbe:~$ sudo apt-get -f remove nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nginx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 528kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 116441 files and directories currently installed.)
Removing nginx ...
Stopping nginx: invoke-rc.d: initscript nginx, action "stop" failed.
dpkg: error processing nginx (--remove):
 subprocess pre-removal script returned error exit status 1
Starting nginx: nginx.
Errors were encountered while processing:
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)


Ive done all the update, upgrade options for apt-get but still no luck :(

---

### Post by geira on 2007-05-30
I had the same problem. Looks like the nginx package is broken. It didn't install properly, it won't uninstall, and whenever you try to install some other program it tries to rerun the postinstall configuration and fails miserably.

What seems most peculiar is that it insists on *starting* nginx before it can be removed. I hacked this by adding an "exit 0" to the top of /etc/init.d/nginx, then it doesn't complain when using apt-get remove.

Shame, because nginx is a great program, but for the moment I believe it's better to compile from source.

---

### Post by oliver369 on 2007-05-30
I had the same problem after trying to install Ruby on Rails on my Ubuntu 7.04 Server. I managed to get nginx off the machine with the following commands:

rm -rf /etc/nginx/
rm -rf /usr/sbin/nginx
rm /usr/share/man/man1/nginx.1.gz
apt-get remove nginx*

This worked fine for me just let me know if it does for you guys!;)

---

### Post by sixsixone on 2007-06-06
Thanks for that, I had the same problem after foolishly installing it with my rails setup on Feisty. I was getting sick of killing the process and reloading apache!

---

### Post by hifiguy36 on 2007-06-22
Thanks for the info, Oliver369, worked for me as well.

I'm going to try XAMPP for developing my Ruby on Rails apps.

---

### Post by sgudibanda on 2007-07-05
I also hacked into intiscript of nginx by adding exit 0. apt-get remove nginx* worked after that. 
Thanks Guys.

Sandeep G

---

### Post by slimjimflim on 2007-10-22
hi, i'm having the same problem. i tried all the things you said above, and it's still there. here's what i get.


   1.
      *@*:/usr/share/cups/model$ sudo aptitude remove nginx
   2.
      Reading package lists... Done
   3.
      Building dependency tree
   4.
      Reading state information... Done
   5.
      Reading extended state information
   6.
      Initializing package states... Done
   7.
      Building tag database... Done
   8.
      The following packages have been automatically kept back:
   9.
        libfaac0 xserver-xorg-input-synaptics
  10.
      The following packages have been kept back:
  11.
        konversation tzdata
  12.
      The following packages will be REMOVED:
  13.
        nginx
  14.
      0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
  15.
      Need to get 0B of archives. After unpacking 528kB will be freed.
  16.
      Writing extended state information... Done
  17.
      (Reading database ... 169193 files and directories currently installed.)
  18.
      Removing nginx ...
  19.
      Stopping nginx: nginx.
  20.
      /var/lib/dpkg/info/nginx.prerm: 39: Syntax error: "else" unexpected
  21.
      dpkg: error processing nginx (--remove):
  22.
       subprocess pre-removal script returned error exit status 2
  23.
      Starting nginx: nginx.
  24.
      Errors were encountered while processing:
  25.
       nginx
  26.
      E: Sub-process /usr/bin/dpkg returned an error code (1)
  27.
      A package failed to install.  Trying to recover:
  28.
      *@*:/usr/share/cups/model$

---

### Post by Railsbuntu on 2007-12-12
Do you still have issues with nginx? I am currently reviewing http server solutions, and nginx is one of them.

---


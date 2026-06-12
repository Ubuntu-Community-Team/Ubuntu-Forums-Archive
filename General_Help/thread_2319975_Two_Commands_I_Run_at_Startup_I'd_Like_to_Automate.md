---
title: "Two Commands I Run at Startup I'd Like to Automate"
date: 2016-04-09
forum: General Help
---

### Post by benjamin-selzer on 2016-04-09
Greetings. First, let me say I'm very new to Linux and Ubuntu, so go easy :)

Secondly, I am using Ubuntu 14.04 on a Chromebook Pixel 2 via chroot; I'm not sure if that makes a difference as to what I can do/not to in Ubunty.

OK, so here goes:

I have two Terminal commands that I must run every time I start up. It's not the end of the world, but I'd love to get them automated somehow.

1.) **sudo /etc/init.d/cups start**

No matter what I try I cannot get CUPS to start upon startup. I have added it to the startup applications using both "/etc/init.d/cups start" and "/etc/init.d/cups -start", but nothing happens upon startup. I still have to open a Terminal and type the command each time.

2.) **[COLOR=#383838][FONT=gotham]sudo sysctl -w fs.inotify.max_user_watches=524288[/FONT][/COLOR]**
I use Insync to sync Google Drive. Works very well, except that my default system Max User Watches is 8192! I have even edited the file /etc/sysctl..conf and amended the last line:

**# added by Insync**
**fs.inotify.max_user_watches=524288**

But now that I think about it, that number was set higher before I edited it

For some reason my system is defaulting to 8192, which is essentially useless. Any way to change the system default, because editing the last line of sysctl.conf doesn't work.

3. ) _Alternative solution_: If I can't make these two startup changes the "right" way, is there a way to program a script to run these two terminal commands upon startup?

Thanks for all your help in advance! :)

-Benjamin

---

### Post by ajgreeny on 2016-04-09
Have a look at the first lines of the cups.conf file by using the command ```
cat /etc/init/cups.conf
```
This is what I see which, if yours is the same, means that cups should start with the filesystem automatically.  
```
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and (started dbus or runlevel [2345]))
stop on runlevel [016]

respawn
respawn limit 3 12
```
If it does not start with the filesystem we will have to look for the reasons why.

---

### Post by SeijiSensei on 2016-04-09
You can add the second command to /etc/rc.local, but omit the "sudo" prefix since everything in that file is run with root privileges by default.  rc.local is the last script to be run at boot.

---


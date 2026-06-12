---
title: "Cant start Ubuntu!"
date: 2004-11-23
forum: General Help
---

### Post by andbert on 2004-11-23
I've just installed Gdesklets (dont know if that matters), and when rebooting, the following error message occurs:

"There already appears to be an X server running on display :0. Should I try another display number? If you answer no, I will attempt to start the server on :0 again. (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7. X servers usually run on consoles 7 and higher.) "

What does this mean? Any input how to fix.
Im a noob, so any help will be appreciated.

---

### Post by arctic on 2004-11-23
maybe this info helps. i found it a wlug-wiki and think that it is quite similar, as it also has to do with the x-server freakin' around.

>  There already appears to be an X server running on display :0.  Should I try another display number?

gdm prints this out after trying to start more than one XServer on :0. (It also prints "Display :0 is busy. There is another X server running already" into the syslog). I got this after upgrading gdm to version 2.4.something in debian testing. This message persisted, even after the laptop was rebooted. I eventually got rid of it - however I'm not entirely sure which of the following fixed it:

    * I upgraded the libgtk2.0-0, libgtk2.0-common and libbonobo2 packages.
    * After killing gdm and all X servers, I started "gdm" manually from the command line and then killed it.

After doing these two steps, gdm behaved properly when started from /etc/init.d/gdm. If you determine how to fix it, please edit this page!

2004-05-14 9:43 EST The correct way to deal with this problem is:

    * Enable "debug" in your /etc/gdm/gdm.conf file under:

 [debug]

# This will enable debugging into the syslog, usually not neccessary and it creates a LOT of spew of random stuff to the syslog. However it can be useful in determining when something is going very wrong.

 Enable=true

Then your messages will be logged to /var/log/syslog.

    * GDM has to always restart X with an entry like the following in gdm.conf:

 [daemon]
 AlwaysRestartServer=true

    * and finally, make sure that you have the following under the same daemon section:

# Automatic VT allocation. Right now only works on Linux. This way we force X to use specific vts. turn VTAllocation to false if this is causing problems.

 FirstVT=7
 VTAllocation=false

# Should double login be treated with a warning (and possibility to change vts on linux systems for console logins)

 DoubleLoginWarning=false

That should be enough to at least know what the source of the problem is. Please note that the latest Debian gdm as of this writing, has issues with udev. So if you have udev generating /dev/vc* block files for you (and removing them when you close X), gdm can't get a hold on running X servers and it let's them running, trying to launch another one in a different vts! Therefore, you will have a few servers running in vt6, vt7, vt8, ..., vtN. The way to "kill them" without having to login in a console (vty1) is to "CTRL+ALT+FN", where N is the number of the vt. Say, for vt8: CTRL+ALT+F8. Once you are there, if you see an X server running (you will be able to move the mouse, but no other application might be running), hit CTRL+ALT+BACKSPACE to kill it. Do the same with the others you may find.

Hopefully somebody else might be able to write a better solution for this ;-). Or I'll come back once I find a more concrete answer. If you are the kind who avoids typing, you might want to make a copy of the factory-gdm.conf file, found under /etc/gdm. 

---

### Post by andbert on 2004-11-23
Didnt quite understand how to perform these actions.
When I boot in recoverymode im at root@ubuntu...
No files or folders there except som fonts and stuff.....

Im not able to enter the GUI at all. Booting stops after Gnome Display manager tries to load.

---

### Post by andbert on 2004-11-24
ok i found the folders and the file.
But it seems like i dont have permission to write to it!

How do i change permission to gmd.conf........?

---

### Post by arctic on 2004-11-24
sorry, i am in a hurry.... read this howto, section 7.1.3. it explains everything you need to know better than i can do it in 10 minutes.
one note: when changing permissions with chmod, do not forget to use the sudo command in ubuntu. in case you have set up a root account you can log in as root, then you do not need the sudo command.
[http://www.debian.org/doc/manuals/debian-tutorial/ch-files.html](http://www.debian.org/doc/manuals/debian-tutorial/ch-files.html)

good luck.

---

### Post by andbert on 2004-11-24
Ok thanks so far. Ive managed to do the corrections in gdm.conf....
But when rebooting the problem still occurs....

---

### Post by uggeli on 2004-11-27
Today I face same problem (haven't installed gdesklets or enything else), Same errormessage as mentioned in first message.

I try to choose first yes, it didn't work and everything seems just freeze and I have to restart. After restarting I choose "no" and I press Ctrl-Alt-F6 to get myself in commandline mode.

In commandline I tried startx but error came up again and said something abou /tmp/.X0-lock. Anyway I was figuring out that tmp is temp and it's safely to remove it as there was mentioned that you should remove it if you don't use t anymorre or something like that. Well I first created copy of the file and then removed the "original" with command sudo rm /tmp/.X0-lock and after that startx did start my x-window system.

My question is that have I done something I shouldn't done? I'm newbie here so I can't know that for sure.

I tried to restart computer and error was there again! I tried to edit gdm.conf,  but  that didn't remove my problem, as it didn't remove  andberts.. Strange hassle with such a basic thing as starting computer straight to x :(

---

### Post by HungSquirrel on 2004-11-27
I am having this problem as well.  Just started recently.

---

### Post by swoon on 2004-11-27
[QUOTE=uggeli]Today I face same problem (haven't installed gdesklets or enything else), Same errormessage as mentioned in first message.

I try to choose first yes, it didn't work and everything seems just freeze and I have to restart. After restarting I choose "no" and I press Ctrl-Alt-F6 to get myself in commandline mode.

In commandline I tried startx but error came up again and said something abou /tmp/.X0-lock. Anyway I was figuring out that tmp is temp and it's safely to remove it as there was mentioned that you should remove it if you don't use t anymorre or something like that. Well I first created copy of the file and then removed the "original" with command sudo rm /tmp/.X0-lock and after that startx did start my x-window system.

My question is that have I done something I shouldn't done? I'm newbie here so I can't know that for sure.

I tried to restart computer and error was there again! I tried to edit gdm.conf,  but  that didn't remove my problem, as it didn't remove  andberts.. Strange hassle with such a basic thing as starting computer straight to x :([/QUOTE]

i did the very same thing and have the very same problem upon reboot. bleh

---

### Post by haocheng on 2004-11-28
I had the same problem after upgrading to Hoary yesterday...

I did as someone said in another thread:

First, choose recovery mode.
Second, do this as root:
```

apt-get install gdm

```

Then, I rebooted and everything worked again.

Hope this helps  :wink:

---

### Post by uggeli on 2004-11-28
Unfortenately that didn't help me. After typing apt-get install gdm it said that there is allready newest gdm installed an no new packages are installed. Should I remove gdm first and then reinstall it? And if I remove it what settings will I lose? Just curious cause when trying startx -- :X (where X is 0,1,2,3,4) only 0 (and notmal startx) opened, x with background image I have set and even in gaim there wasn't user account when it started without my settings. So will I face thiskind of problems if I remove and reinstall gdm?

Edit: I upgraded to hoary and after that it let me install new gdm and things are working atleast at the moment.. :)

---

### Post by ulrich on 2004-11-28
**apt-get install --reinstall gdm **would also do the trick :)

---

### Post by swoon on 2004-11-28
[QUOTE=haocheng]I had the same problem after upgrading to Hoary yesterday...

I did as someone said in another thread:

First, choose recovery mode.
Second, do this as root:
```

apt-get install gdm

```

Then, I rebooted and everything worked again.

Hope this helps  :wink:[/QUOTE]

huzzah!

i don't remember upgrading to hoary though. i guess i shouldn't of upgraded evolution?

---

### Post by Jesper on 2004-12-21
When I run "apt-get install --reinstall gdm" I get the following message:
> Unpacking replacement gdm ...
Setting up gdm (2.6.0.3-1ubuntu20) ...
* Reloading GNOME Display Manager configuration...
* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
what to do?

---

### Post by Bagleemo on 2004-12-23
I get same: invoke-rc.d: initscript gdm, action "reload" failed.
error when try this in safe mode.

---

### Post by Smash on 2004-12-23
I have the same problem  :cry:  ](*,)

---

### Post by nicotin1030 on 2007-05-15
> **Smash said:**
> I have the same problem  :cry:  ](*,)


[Google Paris Hilton blood pressure Cash Advance Debt Consolidation](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---


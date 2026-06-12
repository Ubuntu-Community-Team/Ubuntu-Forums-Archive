---
title: "Typing Break in 14.04?"
date: 2014-04-25
forum: General Help
---

### Post by a-web on 2014-04-25
I have been a very regular user of the typing break included in System Settings up until my install of 14.04.  It's now gone... what happened?  Is there a way to reinstal a typing break?  Many thanks!!

---

### Post by bab1 on 2014-04-25
> **a-web said:**
> I have been a very regular user of the typing break included in System Settings up until my install of 14.04.  It's now gone... what happened?  Is there a way to reinstal a typing break?  Many thanks!!

See here: [http://askubuntu.com/questions/63999/how-can-i-install-typing-break]("http://askubuntu.com/questions/63999/how-can-i-install-typing-break")

---

### Post by a-web on 2014-04-26
Thanks bab1,

I had been using drwright in 13.10 with no problem...  and when I follow the instructions at the link you sent this is the message I get:
> :~$ sudo apt-get install drwright
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package drwright is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'drwright' has no installation candidate

Any insight?

---

### Post by a-web on 2014-06-07
The article referenced above ([http://askubuntu.com/questions/63999/how-can-i-install-typing-break](http://askubuntu.com/questions/63999/how-can-i-install-typing-break)) was recently updated - in order to install in 14.04 we need to use old repositories.

So I did that, and installed drwright.  But I don't see it in System Settings (after reboot).  If I search via the launch bar it finds "Typing Break" but launching that only opens up System Settings...

---

### Post by sudodus on 2014-06-07
Have you tried to start it from a terminal window

```
drwright
```

or can you find it via the dash?

If it does not work can also make something own like what is described in this thread

[Need a command which reminds me every five minutes when I use my system]("http://ubuntuforums.org/showthread.php?t=2228165")

---

### Post by a-web on 2014-06-07
From a terminal I get "command not found".

Via the dash it finds "Typing Break" but only opens up System Settings.

---

### Post by sudodus on 2014-06-07
Try to search for the program file with this command

```
sudo find / -name "drwright*"
```

It might be installed somewhere, that is not in path.

---

### Post by a-web on 2014-07-04
Thanks sudodus.  This is what I get from searching:
```
/usr/share/lintian/overrides/drwright
/usr/share/doc/drwright
/usr/lib/drwright
/usr/lib/drwright/drwright

```
I'm not sure what that tells me, though.

---

### Post by sudodus on 2014-07-04
There seems to be no instance of drwright in any directory in PATH. I don't think any of those four instances you found is an executable file (program or script), but I am not sure. You can make a long list for each of them

```
ls -l /usr/share/lintian/overrides/drwright /usr/share/doc/drwright /usr/lib/drwright /usr/lib/drwright/drwright

```

Maybe you can try to remove/purge it and install again, so try again with the tip by bab1 in post #2.

The problem is probably that this program is not [yet] made to work with Ubuntu 14.04. If you try again after a period of time you might find a version that works. You can also search the internet for information about ***drwright and 14.04***

---

### Post by a-web on 2014-07-05
Thanks.  I removed and then reinstalled drwright, but no change in outcome.

Here's my long list:
```
/usr/lib/drwright:
total 4
drwxr-xr-x 2 root root 4096 Jul  5 06:31 drwright

/usr/lib/drwright/drwright:
total 48
-rwxr-xr-x 1 root root 47304 Jun  6  2012 gnome-typing-monitor

/usr/share/doc/drwright:
total 44
-rw-r--r-- 1 root root    36 Nov 18  2010 AUTHORS
-rw-r--r-- 1 root root   175 Jun  6  2012 changelog.Debian.gz
-rw-r--r-- 1 root root 27100 Jun  4  2012 changelog.gz
-rw-r--r-- 1 root root  1100 Apr 23  2012 copyright
-rw-r--r-- 1 root root   765 Jun  4  2012 NEWS.gz

```

And I haven't been able to find anything else from internet searches (which surprises me!)

---

### Post by sudodus on 2014-07-05
It seems the executable file is ***gnome-typing-monitor***

in the directory **/usr/lib/drwright/drwright**

Try what happens when you launch the command

```
/usr/lib/drwright/drwright/gnome-typing-monitor
```

---

### Post by a-web on 2014-07-06
I get a blinking cursor....  nothing else.

---

### Post by sudodus on 2014-07-06
Unless you find some text about it, that can help you fix the problem, I think this program is buggy in 14.04.

---

### Post by a-web on 2014-07-13
I've switched to workrave ([http://www.workrave.org/](http://www.workrave.org/)) and given up on drwright.  So what is the etiquitte on marking this thread as "solved"?  I haven't solved the problem, just given up.  Thanks for all the help!

---

### Post by sudodus on 2014-07-13
If workrave does the thing, then you have a solution for the problem stated in the title 'Typing Break in 14.04?', so I suggest that you mark this thread as SOLVED :-)

---


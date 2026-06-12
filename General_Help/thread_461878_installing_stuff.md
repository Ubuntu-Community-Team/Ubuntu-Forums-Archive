---
title: "installing stuff"
date: 2007-06-02
forum: General Help
---

### Post by Irti on 2007-06-02
where does all the installed stuff go in ubuntu..???? i mean which folder is it stored on....?? also i wanted to watch over the disk space i use.....windows was pretty easy...just right click and check...wut do i do over here..???

---

### Post by Brucevdk on 2007-06-02
> **Irti said:**
> where does all the installed stuff go in ubuntu..???? i mean which folder is it stored on....??

There's a useful table comparing the GNU/Linux way of organizing files with that of Windows over at [polishlinux.org]("http://polishlinux.org/first-steps/filesystem-and-disks/"). Here's a real-life example (gaim, nowadays pidgin):

```

/usr/share/menu/gaim		# gaim applications menu entry (the start menu thingy)
/usr/share/doc/gaim		# some gaim documentation
/usr/bin/gaim			# the actual gaim program (executable)
/usr/lib			# a whole bunch of libraries gaim needs to function
/usr/lib/gaim 			# and some really specific gaim ones

```

However gaim depends on another package gaim-data which installs some more files such as icons and sounds. 

```

/usr/share/man			# manual pages for the command line
/usr/share/pixmaps/gaim		# all sorts of images such as icons and smileys
/usr/share/sounds/gaim		# all the sounds included with gaim

```

You have to realize though that this isn't really important to the end-user (i.e. you), anything relevant to the end-user can be found in the home folder (albeit in hidden directories). You should never have to manually modify anything in these folders (which is why they're owned by the root user). Just look where gaim stores its logs and user preferences, that's right in */home/<username>/.gaim*

> **Irti said:**
> also i wanted to watch over the disk space i use.....windows was pretty easy...just right click and check...wut do i do over here..???

The easiest way to do this is using the *gnome-system-monitor*, see the tab File Systems. You can also use the Disk Usage Analyzer (baobab) which is  included by default in Feisty. The file manager itself (Nautilus) really doesn't offer that much information.

---

### Post by eggdeng on 2007-06-02
If you need to know where a programme is installed, there's a nifty command called which. Example ```
eggdeng@LAPTOP:~$ which xine
/usr/bin/xine
``` The diskfree command ```
df
``` outputs at-a-glance partition info.
```
eggdeng@LAPTOP:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda3             63163940  39297592  20657768  66% /
varrun                  516784       100    516684   1% /var/run
varlock                 516784         4    516780   1% /var/lock
udev                    516784       140    516644   1% /dev
devshm                  516784        16    516768   1% /dev/shm
lrm                     516784     18316    498468   4% /lib/modules/2.6.15-27-686/volatile
/dev/sda1             25647736  18588540   7059196  73% /media/winxp
/dev/sda5              5106680        68   5106612   1% /media/exchange
``` Type ```
man df
``` to see more options.

---

### Post by Irti on 2007-06-02
thanx ppl...i am a complete newbie to linux....just tryin to understand how it works....

---

### Post by Lanky Juggler on 2007-06-03
on the note of df, it gets a lot prettier if you add a -h handle to it.  like so:  df -h .  The -h thing works with a few programs that show quantities of space, and it shows everything in appropriate (**h**uman) units, ie megabytes and gigabytes rather than kb.

---

### Post by strabes on 2007-06-03
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---


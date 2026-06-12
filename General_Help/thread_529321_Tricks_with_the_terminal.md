---
title: "Tricks with the terminal"
date: 2007-08-19
forum: General Help
---

### Post by PmDematagoda on 2007-08-19
I am just curious but could anyone tell me how i can:-
1)Get the terminal without accessing it through the main menu
2)Shutting down the system using the terminal
3)Hibernating using the terminal
4)Logging off using the terminal and
5)Locking the screen using terminal

I would really appreciate any answers to these questions as i really am eager to use linux to it's full potential which includes using the terminal as much as possible as i got tired of using windows and its slow and boring processes and methods.Thanks.:)

---

### Post by eentonig on 2007-08-19
1)Get the terminal without accessing it through the main menu
- <Alt>+<2> and enter "gnome-terminal"
- install "Tilda" so you can have a quake like terminal which is one key combination away.
2)Shutting down the system using the terminal
> sudo shutdown now
3)Hibernating using the terminal
4)Logging off using the terminal and
> sudo /etc/init.d/gdm restart
5)Locking the screen using terminal

---

### Post by aysiu on 2007-08-19
All my answers assume you're using Ubuntu (Gnome) as opposed to Kubuntu or Xubuntu > **PmDematagoda said:**
> 1)Get the terminal without accessing it through the main menu Alt-F2 ```
gnome-terminal
``` Or, create a keyboard shortcut for it in System > Preferences > Keyboard Shortcuts
> 2)Shutting down the system using the terminal ```
sudo shutdown -h now
``` > 4)Logging off using the terminal ```
gnome-session-save --kill
```

---

### Post by PmDematagoda on 2007-08-19
I tried the shutdown method you suggested but did not shutdown properly, it closed all the applications but in the end only another terminal came up from which i couldn't do anything.

---

### Post by PmDematagoda on 2007-08-19
Thanks Aysiu your shutdown method worked properly along with the other commands, but thanks to eentonig for helping me out as well. But isn't there any command for Hibernating or locking the screen?

---

### Post by aysiu on 2007-08-19
> **PmDematagoda said:**
> I tried the shutdown method you suggested but did not shutdown properly, it closed all the applications but in the end only another terminal came up from which i couldn't do anything.
Try mine. ```
sudo shutdown -h now
``` The *-h* means *halt*.

---

### Post by aysiu on 2007-08-19
> **PmDematagoda said:**
> Thanks Aysiu your shutdown method worked properly along with the other commands, but thanks to eentonig for helping me out as well. But isn't there any command for Hibernating or locking the screen?
I haven't tested this myself, but according to [the Gnome Power Manager FAQ](http://live.gnome.org/GnomePowerManager/FAQ), it would be ```
dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate
``` And according to [this HowTo](http://www.linuxforums.org/forum/linux-desktop-x-windows/64208-howto-windows-key-l-lock-screen.html), the command for locking is ```
gnome-screensaver-command --lock
``` I found both of those by searching in Google for ```
command hibernate gnome power manager
``` and ```
command "lock screen" gnome
```

---

### Post by Dark Star on 2007-08-19
Thanks for tricks aysiu :D

---

### Post by eentonig on 2007-08-19
Thanks Aysiu, 

I forgot the -h parameter.

---

### Post by PmDematagoda on 2007-08-19
Sorry for the thanks Aysiu but was out for sometime. Thanks for the tricks they are brilliant.

---

### Post by PmDematagoda on 2007-08-19
Excuse me but does anyone have any way of shutting down ubuntu if the system hangs up(in a safe way) i wasn't sure if it applies to the use of the terminal or not.

---

### Post by PmDematagoda on 2007-08-19
By the way does anyone now how to initiate a format of a drive using the terminal?

---

### Post by Anzan on 2007-08-19
> **PmDematagoda said:**
> Excuse me but does anyone have any way of shutting down ubuntu if the system hangs up(in a safe way) i wasn't sure if it applies to the use of the terminal or not.

The keyboard is your friend:

ALT SysRq + k will kill the Gnome session and restart so you can log back in. If you wait a few moments after restarting, most of your applications will come back up.

ALT SysRq + r then s then e then i then u then b (Raising Skinny Elephants Is Utterly Boring) will safely shut down everything.

---

### Post by PmDematagoda on 2007-08-19
Thanks Anzan.

---

### Post by PmDematagoda on 2007-08-19
Also since this is usually done with the terminal, i'm asking. How do you perform a disk check in ubuntu and fix any errors it finds, also what will it do to bad sectors, will i be able to recover anything that were on them?:confused:

---

### Post by Anzan on 2007-08-19
> **PmDematagoda said:**
> By the way does anyone now how to initiate a format of a drive using the terminal?

To format an external drive for example, you would first have to figure out the device name

   df -k /media/disk

That *should* have only two lines of output and should looks something like this:

--------------------

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112420772  83649824  23060244  79% /

---------------------

The "/dev/sda1" portion is what we care about, though your USB drive will probably have a number like "/dev/sdc1".  

So, first, become root:

--------------
sudo -s
---------------

Then, unmount the drive:

---------------
umount /media/disk
----------------

Then create the filesystem:

------------------
mkfs.ext3 devicename  

( in this case mkfs.ext3 /dev/sdf1)
-----------------

Again, please be careful that you have the device that is mounted on top of /media/disk.  If the device is "sda", then it is almost certainly your internal disk, and that will break your PC.

Type the "sync" command twice (just to be sure that the blocks got flushed to disk):

---------------------------
sync
sync
----------------------------

And, if the drive hasn't already remounted itself, unplug it (or switch off) and plug back in.  It should automatically come up.

sudo chown -R yourname /media/disk

---

### Post by PmDematagoda on 2007-08-19
Can't you format the internal hards as well?

---

### Post by anaconda on 2007-08-19
> **PmDematagoda said:**
> I am just curious but could anyone tell me how i can:-
1)Get the terminal without accessing it through the main menu


tilda is a good program just for this. Needs a bit configuring though.. I have one terminal with F1 and other tilda terminal with F2

---

### Post by PmDematagoda on 2007-08-19
How do you configure tilda? (Sorry for the many questions but i am a noob user and i want to know as much about ubuntu as possible.)

---

### Post by Anzan on 2007-08-19
> **PmDematagoda said:**
> Can't you format the internal hards as well?

Sure. Just get the name right.

---

### Post by PmDematagoda on 2007-08-19
Can't you scan the hards for disk errors?

---

### Post by PmDematagoda on 2007-08-19
This is just a suggestion but how about making this thread a sticky, it could help lot of people get over  certain problems such as crashes.

---

### Post by Anzan on 2007-08-19
> **PmDematagoda said:**
> Can't you scan the hards for disk errors?

fsck. 

(Pronounced fusk or thereabouts. Filesystem consistency check and interactive repair.)

---

### Post by g2g591 on 2007-08-19
how to shut down with a terminal command:  sudo shutdown -P now
also instead of now you can specify a time (24hr format) so, to shut down at 4pm: sudo shutdown -P 16:00

---

### Post by PmDematagoda on 2007-08-19
When i type in fsck to a terminal this appears:

fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Is this warning true?

---

### Post by dpar on 2007-08-19
This post has some good links if you like to play with terminal.:)

[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

---

### Post by oldos2er on 2007-08-19
>Is this warning true?

 Yes, it's not lying to you. Only run fsck on unmounted partitions.

---

### Post by Old *ix Geek on 2007-08-20
> 1)Get the terminal without accessing it through the main menu
I didn't see this mentioned in any of the current replies, so here goes.  This is much faster than typing a command in order to open a terminal: Just assign a shortcut to its entry in your menu.  (NOTE: I use KDE and have no idea if Gnome offers the same functionality, but I can't imagine that it doesn't.)  Here's how it works in KDE:

. from the KDE menu, find the entry for the terminal you want to use
. right-click on it
. choose 'edit item'
. select the button next to 'current shortcut key'
. enter the key (or combination of keys) you want to assign as the shortcut
. save the menu and you're done

Now you can simply press the key(s) you assigned as a shortcut and terminal will start up.

---

### Post by PmDematagoda on 2007-08-20
Then how do you check the main disk( The one with ubuntu feisty) for disk errors?

---

### Post by aysiu on 2007-08-20
> **PmDematagoda said:**
> Then how do you check the main disk( The one with ubuntu feisty) for disk errors?
It'll be checked every thirty reboots automatically.

---

### Post by PmDematagoda on 2007-08-20
Now since i know there are bad sectors on my hard containing ubuntu(I knew about it before installing ubnutu on it), what does ubuntu do to these bad sectors and can any data on them be recovered?

---

### Post by PmDematagoda on 2007-08-25
I tried formatting my USB pen drive the way Anzan told me to but when the format was finished i found that the file system was converted to ext3(Not a problem) and also that the owner of the drive was changed to the root which means that i can't do any changes to the drive or put any files to it or anything(This is the real problem). Does any one know how to solve the problem?Not necessarily the file system one as i fixed it with gnome partition manager and it was very interesting.

---


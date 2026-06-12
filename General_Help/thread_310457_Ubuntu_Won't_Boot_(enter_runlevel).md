---
title: "Ubuntu Won't Boot (enter runlevel)"
date: 2006-12-01
forum: General Help
---

### Post by shironeko on 2006-12-01
This morning when I boot up my computer I discover that something strange happened... well, I just see a: Enter Runlevel Screen instead of directly login into my desktop.
I try with runlevel 5, but it freezes. It says: INIT: Entering runlevel 5. Then I try with runlevel S or recovery mode, and it works, well, I get a console/terminal mode:

The problem is that it says that de "Filesystem" is "Read only", and I can't login into my normal user (shironeko), because when I try entering the password It tells me: Permision denied.

What can I do, in order to repair this issue?

Summing up:

- When I start I get a "Enter Runlevel" screen
- runlevel 5 doesn't work
- That's when I enter with Runlevel S, or Recovery Mode
- Can't install, uninstall, or Write anything. It says read Only filesystem.
- Can't login with my user, it says: Permission Denied.

And... well... Maybe I should say that yesterday, before this happened I installed sysv-rc-conf and disabled some services (But not important one, just, for example, some Dial-up needed services), and no, I didn't turn off the GDM.

Thank you.

---

### Post by koenn on 2006-12-01
sysv-rc-conf - that's System V Resource Control, and the run-level mechanism is closely tied with it so probably something got re- or mis-configured there.

What happens if you choose runlevel 2 (ubuntu's default runlevel) ? 
Does it still work ?

Have a look at /etc/inittab, eg by executing the command
```
less /etc/inittab
```
(you can then scroll through the text with up and down arrows of your keyboard)

See if there is still something like this there:
```

# The default runlevel.
id:2:initdefault:

```
The "2" indicates the default runlevel, and
then the following tells your system what to do when it goes to a given runlevel:
```

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6


1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6


```

---

### Post by shironeko on 2006-12-01
Ok, I checked! Here's what I did and what I found:

First I booted normal, and as usually it asked me to enter a runlevel. I entered "2" and nothing happened.
Then I ran the recovery mode, and was able to check the inittab file as you told me.

There was only:
> 
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

**NOTHING ELSE**

Well, afterwards, I tried to run runlevel 2.
I wrote init 2, and it switched to runlevel2.

Once inside it asked me to login.

I wrote my username and my password, and then it printed this:

> - bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
- bash: /dev/null: Acces Denied
(Many times)

Any clues?
I'd like to repair, or rewrite the inittab file, but I can't login in order to do so.
When I try to change something without login it tells me that the filesystem is "ReadOnly".

I still have the CD, maybe I can re-install or repair with the CD, is that possible?

---

### Post by koenn on 2006-12-01
that doesn't look too bad on first sight. Most (maybe all) of the problems you encountered can be explained by the incomplete inittab. 
To restore a copy, you could run a live CD, mount the partition where your system is installed, and try to edit inittab from there. 
That means that from a Live CD session, you'd be looking for /media/hda1/etc/inittab instead of /etc/inittab.
In fact, you could probably copy from /etc/inittab because that would be the inittab of the live CD session, i guess, and probably just what you need. 

I think a Ubuntu Live CD will automatically mount the partitions on your computer - you may have to set them to read&write in stead of readonly, and you need to be root. 

I suppose you could also do this by logging in to recovery mode, and use vi or vim as editor, but that's harder if you're not used to it, and you'd have to actually type the inittab. I'd try the live CD first.

---

### Post by shironeko on 2006-12-01
Thank You very much! I'm relieved it's not a serious problem.

Well, I tried booting de Live CD, but it doesn't mount the HardDisk, any tips?
Well, meanwhile I'll try figuring out myself searching on google or something.

Thanks!

---

### Post by koenn on 2006-12-01
try mounting it by hand: The command is 'mount [-t fstype] something somewhere'. so you probably want something like
```
mount -t ext3 /dev/hda1 /media/hda1
```
more help with 'mount --help' or complete instructions with man mount


If Ubuntu Live CD won't let you do this, see if you can get a Knoppix cd. 
Knoppix does mount any partition on the host system. They'll be mounted readonly but that's easy to change (from a context menu if you rightclick the icon, if i remember correctly)

---


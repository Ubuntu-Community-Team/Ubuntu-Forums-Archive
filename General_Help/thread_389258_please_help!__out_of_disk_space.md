---
title: "please help!  out of disk space"
date: 2007-03-20
forum: General Help
---

### Post by ilovelinux on 2007-03-20
HI this is my 1st post...need help!!  I run only Linux and operate on Ubuntu.  My computer told me I was out of space and should free some up--so I did and was about to burn a bunch of files onto CD...my computer froze up so I shut down and when I booted up again it won't let me log in says" your out of disk space and can't log in-contact admin support" I can't get in on any Session Log In's to delete to run system properly.  Please help!!  

I am running off Ubuntu Install Disk to get online

---

### Post by IcemanV9 on 2007-03-20
It has happened to me for the first time a couple days ago. When you are at GDM login, go to console (Ctrl+Alt+F1). Login as normal. Type ```
sudo aptitude autoclean
``` It'll free up a few megabtyes. Then, go back to GDM login (Ctrl+Alt+F7). Login as normal.

---

### Post by taurus on 2007-03-20
Or boot into recovery mode from GRUB menu and at the prompt, run

```
sudo aptitude clean
df -h
```

---

### Post by ilovelinux on 2007-03-20
thank you for the tips...however I tried this is did free up 870kb....this is the message I am still getting

[COLOR="Red"]GDM could not write to your authorization file.  This could mean you are out of disk space OR that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact Admin. Support
[/COLOR]
Now what??  Thank you in advance for helping me.

---

### Post by IcemanV9 on 2007-03-20
Not much to free up some spaces, eh? Ok, next thing would be find out how many kernel do you have on your box. You can either find out at the boot time where it shows the menu or look at /boot/grub/menu.lst file. If you have more than 2 kernel, then you can remove the oldest kernel.

This is an example for Dapper box. (I do not know what's yours)
```
sudo aptitude purge linux-image-2.6.xx-xx-686
```

It'll free up even more space (could be from 65Mb to 75Mb).

---

### Post by taurus on 2007-03-20
Or look in /var/backup to see if you have a backup of your system daily.

From recovery mode again:
```
du -h /var
```

---

### Post by ilovelinux on 2007-03-20
AAGGHH!  Did the commands you suggested looks like it cleared up some space around 70mb...however still getting the above posted error!!  Is their anything I can about the "home directory not being able to open to write"? thank you....

---

### Post by hikaricore on 2007-03-20
This is just a guess I could be completely wrong.

There was a bug some time ago with X and system logs that allowed the .xsession-errors file to grow to insane sizes.  You should check the output of:

```
ls -la ~/.xsession-errors
```

For example mine is:

> 
-rw-r--r-- 1 hikaricore hikaricore _19872_ 2007-03-20 18:22 .xsession-errors


Which is roughly 18kb, but at one point when I was affected by the issue I mentioned, I had a 10gig .xsession errors file.  O.o

In worst case you can softlink this file to /dev/null, only if it turns out to be the issue, several fixes for this were discussed on the forums previously.

---

### Post by Virgo53 on 2007-03-20
I was getting the same message at bootup - refer to my thread "Ubuntu- Unable To Login"
or search the posts made by me.

Good luck!
Virgo53

---

### Post by xadder on 2007-03-21
To remove space, go into /tmp and see if anything can be removed. As far as I know sudo rm /tmp/*  is pretty safe to do, although I am usually a bit more explicit/careful with such commands.

Check your /var/log/messages, syslog and kernlog files. I had a situation where these
are filling up with 25 error messages per minute, completely filling my / disc.
(Reported on launchpad). Removing older /var/log/message files (e.g. messages.x.gz) can also help give some space if you are in a tight spot. These files may also let you know if something strange is going on with your system.

---

### Post by nikhilk on 2007-03-21
I guess the problem is that you have run out of disk space on your /home partition. The commands like 'aptitude clean' etc will free space on your / partition. Same goes for clearing up '/tmp' and '/var/log'. But this wont help if you have / and '/home' as seperate partitions (which is true in most cases). So try to free up space in your '/home' partition by moving/deleting stuff.

---


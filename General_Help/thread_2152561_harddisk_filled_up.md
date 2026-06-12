---
title: "harddisk filled up"
date: 2013-06-08
forum: General Help
---

### Post by ELMIT on 2013-06-08
I have a 3 TB harddisk and it filled up over the year to 2.1 TB. After upgrading to 13.04 the problems started:

Last few days however, it filled up complete.
I deleted 800 GB !!! and  one day later it was filled  up again.

How can I figure out which process fills the hard disk and how can I stop it.

sudo -i 
baobab shows me the usage, but  nothing what I could use for that.

df   shows the disk is full 

any ideas?

bye

Ronald

---

### Post by ELMIT on 2013-06-08
something I just noted yet:
there are two processes in top 
/usr/lib/evolution/evolution-source-registry
/usr/lib/evolution/evolution-addressbook-factory

which use 98% cpu

I don't know why they are running, since I use Thunderbird as  my mail program.

---

### Post by oldfred on 2013-06-08
Is it a run away log file with some errors or data in a hidden folder in /home?

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)


 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h

---

### Post by localhost8080 on 2013-06-08
I use this blog post I wrote a while ago to do things like this:

[http://jonathansblog.co.uk/how-to-find-the-ten-biggest-files-or-directories-in-linux](http://jonathansblog.co.uk/how-to-find-the-ten-biggest-files-or-directories-in-linux)

first find the biggest files, then find out what created them (it might be an error log, etc) and go from there

---

### Post by ELMIT on 2013-06-08
I found the growing file:
~/.xsession-errors    1.4 TB !!!!

It contained mostly    PM Authentication defered - ignoring client message

I used cp /dev/null .xsession-errors to clear out the file
and I stopped Vinno Desktopsharing! That might have added above messages.

Now the file is still growing, but in acceptable speed. The messages now in that files are

(thunderbird:11081): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.36.0/./gobject/gsignal.c:3429: signal name `selection_changed' is invalid for instance `0x7fe2ff056450' of type `MaiAtkType3'

(process:16090): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed



How to fix that?

---

### Post by oldfred on 2013-06-08
I do not use Unity, but use gnome-panel.

Similar issue but no real solution:
[http://askubuntu.com/questions/287525/thunderbird-missing-from-messaging-menu-dash](http://askubuntu.com/questions/287525/thunderbird-missing-from-messaging-menu-dash)

---


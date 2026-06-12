---
title: "After trying to wipe faulty ext hdd, gui is gone"
date: 2018-08-06
forum: General Help
---

### Post by viktor03 on 2018-08-06
Running kubuntu 18.04 in lenovo ideapad y700  I was trying to wipe an ext hdd that isn't working. Gparted got stuck. With disks I saw the drive was in /dev/sdc. i continued to try to wipe it with : Sudo dd if=/dev/zero of=/dev/sdc1bs=1MB  I removed the disk before the command was complete because I thought it wasn't working. I got a system error message that my home folder has no more free disk space while the command was still running (never had that before)  After restarting the computer i only get a black screen and a cursor.  I can get a console and i also have a live os on usb.  Please help if you can

---

### Post by HermanAB on 2018-08-06
Hmm, the good old Disk Destroyer...

If the below is really what you typed, then you missed a space after 'sdc' and wrote a bunch of cruft to '/dev', so now the 'sda' disk is full and the machine cannot boot right:
dd if=/dev/zero of=/dev/sdc1bs=1MB

Try to boot with an install CD or memory stick, navigate to /dev and delete the file called something like "sdc1bs=1MB" to free up the space again.

---

### Post by viktor03 on 2018-08-06
Dear Herman,

Thank you for your reply.

I don't believe I made the same typo when I was trying to wipe the external drive. There's also no such file in /dev, and /dev is only 12mb large.

So that's not it. I've also tried to clear the cache and disconnect the batt to clear the ram. But that doesn't do anything either.

---

### Post by dragonfly41 on 2018-08-06
Check on your last commands by running command ..
```
history
```

---

### Post by HermanAB on 2018-08-07
So, if /dev/sda is full:
a. Confirm whether it really is full with '# df'
b. Delete the log files in /var/log.  You can delete everything in there - important log files will be automatically recreated when you boot again.
c. You can find the top ten largest files in the system with '# du -a / | sort -n -r | head -n 10'

---

### Post by viktor03 on 2018-08-07
i posted a reply with the output of those commands... but it seems to have disappeared. the dd command was first input correctly.

anyway, it worked! it must have been rm the logs. the computer boots back into my GUI with everything in it. 
I can't thank you enough. i was getting afraid i might not be able to fix this problem without reinstalling some stuff. which would be hard because i'm at sea and the internet connection here wouldn't really allow that.

i'm not sure if i should / could put this in the same thread, because the previous info is still relevant. I'd like to try again to reformat or repair the faulty external disk. But without breaking my computer.
Any advice?

Maybe it would be safer to use the same live OS? It should also be possible to dump the output of disk destroyer so it won't fill the logs, but i don't know how to do that? Or maybe another way, not involving dd might be better?

thank you again,
Viktor

---

### Post by HermanAB on 2018-08-07
Do, do a search for big files.  A problem file may still be there somewhere.

In general, dd is best avoided, not because there is anything wrong with it, but simply because the syntax is arcane, causing many unintended fat finger problems.

You can wipe a disk with cat, just as efficiently as with dd:
$ sudo cat /dev/zero > /dev/sdc


BTW, to make a messed up drive usable again, you usually need not erase the whole thing, just the initial few MB, which you can only do properly with dd (or with cat and press ctrl-c after a few seconds):
$ sudo dd if=/dev/zero of=/dev/sdc bs=1M count=10

(Note that it is sdc, not sdc1)

After that, you should be able to format it again with gparted (or fdisk and mkfs if you are a masochist).

---

### Post by viktor03 on 2018-08-07
this is the big file search, does it look ok?

viktor@viktor-buntubox:~$ sudo du -a --human-readable / | sort -n -r | head -n 10
du: cannot access '/home/viktor/Documents': Permission denied
du: cannot access '/home/viktor/Pictures': Permission denied
du: cannot access '/proc/13809/task/13809/fd/4': No such file or directory
du: cannot access '/proc/13809/task/13809/fdinfo/4': No such file or directory
du: cannot access '/proc/13809/fd/3': No such file or directory
du: cannot access '/proc/13809/fdinfo/3': No such file or directory
1020K   /var/spool/cups/d00021-001
1020K   /var/spool/cups/d00020-001
1020K   /var/spool/cups/d00019-001
1020K   /var/cache/apt/archives/plasma-discover_5.12.5-0ubuntu0.1_amd64.deb
1020K   /usr/share/stellarium/translations/stellarium-planetary-features/en.qm
1020K   /usr/share/stellarium/nebulae/default/ic443-vasey.png
1020K   /usr/share/doc/HTML/pt_BR/kcontrol
1020K   /usr/lib/x86_64-linux-gnu/libQt5QuickTemplates2.so.5.9.5
1020K   /usr/lib/x86_64-linux-gnu/libliveMedia.so.62.0.2
1020K   /usr/lib/ruby/vendor_ruby

---

### Post by HermanAB on 2018-08-07
It looks clean enough.

---

### Post by viktor03 on 2018-08-07
Okay, thanks again for the help

---


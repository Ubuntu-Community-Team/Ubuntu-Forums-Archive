---
title: "BusyBox ... ( but ... by the normal way , i didn't get any problems ) ..."
date: 2007-11-25
forum: General Help
---

### Post by 135798642 on 2007-11-25
After installing ubuntu 7.10 with Wubi 7.10 alpha , i went to the OS screen , chose ubuntu-linux and i got a message :

Busy Box v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands 
                               :confused:
But ... by the normal way ...     :KS  

                                :confused:
...   plz tell me how to fix it ??? :(    i hate using ubuntu's bootloader , creating a partition , ...  plz   ... + + i'm a newbie , plz help ...

---

### Post by ago on 2007-11-25
type 

cat /casper.log

and report here any error message (scroll with shift + pgup/down)

---

### Post by 135798642 on 2007-11-26
:confused: 

cat: /casper.log: No such file or directory

:confused:

---

### Post by ago on 2007-11-26
When does that happen?
After the first reboot or the second reboot (after the progressbars)?

---

### Post by 135798642 on 2007-11-26
hix , after the progressbars  :(

---

### Post by ago on 2007-11-26
edit /ubuntu/disks/boot/grub/menu.lst and add "debug=2" to the lines that start with "kernel"

Now you should have a log in /tmp or /var/log

---

### Post by 135798642 on 2007-11-27
(hd0,1) # kernel	/vmlinuz root=/dev/hda2    ....

Is that line ???  where to put "debug=2" ???  If not right plz let me know what line and where to put "debug=2" ??? Plz ,'m a newbie :(

---

### Post by ago on 2007-11-27
Append it to the first line that starts with "kernel" without the "#"

---

### Post by 135798642 on 2007-11-27
hix , sorry , i'm a newbie , i didn't see that , plz help me :(
[http://www.mediafire.com/?4mxt9di22zs](http://www.mediafire.com/?4mxt9di22zs)

---

### Post by ago on 2007-11-27
Sorry cannot access the URL above, it's firewalled, would you mind posting it somewhere else?

---

### Post by 135798642 on 2007-11-27
thanks , [http://rapidshare.com/files/72653098/menu.lst.html](http://rapidshare.com/files/72653098/menu.lst.html)

---

### Post by Danish989 on 2008-05-04
I'm having the same exact problem.. what do I do?

Hardy Heron worked fine for 2 days, but then I was working in xp one day, and I restarted to boot to Ubuntu, only to get the same error at the same time as this thread starter. I used Wubi to install too .. help :(

---

### Post by ago on 2008-05-04
Try chkdsk /r from windows first on the drive where you installed ubuntu

---

### Post by azizzle on 2008-05-04
> **ago said:**
> Try chkdsk /r from windows first on the drive where you installed ubuntu

I'm also having the same problem. It started happening after I had to hard reboot my pc after it froze. 

I tried cat /casper.log and it said there was no such command or directory. 

cat /proc/partitions displayed this:

8  0  312571224 sda
8  1  312568641 sda1


Any suggestions?


edit: i also tried chkdisk /r and reboot i still get the busybox :(

edit 2: I tried to boot in recovery mode. it gave me 
Alert: /host/ubuntu/disks/root.disk not found. 

But when I log into windows, and navigate to my ubuntu/disks folder, root.disk is in there. What should I do?

---

### Post by ago on 2008-05-05
azizzle

At the busybox check that /host is mounted as the right windows drive. 

ls /host

And check that you can actually see /host/ubuntu/disks/root.disk from there

Then try to mount it manually

mount -o loop /host/ubuntu/disks/root.disk /root

---


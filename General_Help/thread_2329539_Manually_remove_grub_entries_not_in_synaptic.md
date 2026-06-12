---
title: "Manually remove grub entries not in synaptic"
date: 2016-07-02
forum: General Help
---

### Post by 74corvette on 2016-07-02
Hi, I am running ubuntu 16.04, upgraded from 14.04, 13.10.  The problem I have is there are old kernels left kicking around from I think 13.10 and are no longer in synaptic.  I guess during one upgrade the kernels never got cleaned out.  How can I manually remove these old kernels from grub and the OS?  Before I start deleting files in the /boot directory I would like to ask someone more experienced then me so I don't mess something up.  Attached is my boot directory showing the leftover 3.11 kernels I can't remove.

[ATTACH=CONFIG]269902[/ATTACH]

---

### Post by &amp;KyT$0P# on 2016-07-02
Well you can double-check that those files don't belong to an installed package, and it's probably smart to do so.  Run this command in a Terminal:
```
dpkg-query -S /boot/*3.11*
```
For files that are *not* part of an installed package, it will output along these lines:
```
dpkg-query: no path found matching pattern <path>
```

Also double-check that you're not running under a 3.11 kernel:
```
uname -a
```

If all that turns out like expected, you can start removing these leftover files from /boot. (I would recommend you move them elsewhere instead of deleting them, so that you can put them back in case something goes wrong.)

When all those files are no longer present in /boot, be sure to run
```
sudo update-grub
```
And then reboot the computer to check that it worked.

Hope this helps.

---

### Post by grahammechanical on 2016-07-02
What does the printout show when you run the update-grub command? In 16.04 this command will remove all old kernels and leave the 2 latest kernels.

```
sudo apt autoremove
```

In earlier versions of Ubuntu the command is

```
sudo apt-get autoremove
```

but it will only remove one kernel for every time it is run.

Regards.

---

### Post by 74corvette on 2016-07-03
Thanks for the reply's. I ran the synaptic query you suggested and it has confirmed these kernels are no longer in the database.  Here is the terminal output.

[ATTACH=CONFIG]269925[/ATTACH]

I am running the latest 4.4 ubuntu kernel.

When I run grub update, grub finds these kernels and they are added to the boot menu at boot up.  Here is the output from that.

[ATTACH=CONFIG]269926[/ATTACH]

I also ran apt-get autoremove and it did not find anything to remove.

If it is safe to remove the 3.11 files from the /boot dir then I will give that a go.  And I will move the files, not delete them, always good advice. Thanks!

---

### Post by &amp;KyT$0P# on 2016-07-03
You're welcome!

---

### Post by oldfred on 2016-07-03
You may want to check a couple of other places also, when dpkg housecleans it also removes from other locations:

 kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this) 

      
  Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 ls /usr/src
ls /lib/modules
ls /var/cache/apt/archives/linux-image*

---


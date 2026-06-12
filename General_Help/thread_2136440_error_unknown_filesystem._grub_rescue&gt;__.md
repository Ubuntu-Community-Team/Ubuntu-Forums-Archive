---
title: "error: unknown filesystem. grub rescue&gt; _"
date: 2013-04-17
forum: General Help
---

### Post by yekin on 2013-04-17
hi,
my computer is unable to boot and i am getting an error like "Error: unknown filesystem" and dropping to grub rescue.
i searched from the internet and found some solutions like booting from a live CD and reinstalling the GRUB.

I am trying to boot from live CD and USB ,unfortunately my computer does not boots from live CD or USB either :(. 

```
grub rescue> ls
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
```

i don't know what to do, neither fresh reinstall nor live CD works. Please help!!!
Thanks

---

### Post by oldfred on 2013-04-17
Some systems get locked up and need a full power down or cold boot. With laptops it is a bit more difficult, but remove battery & hold power switch to discharge capacitors.
 Laptop full power reset. post #4 hold power on switch
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

Did you have an abnormal shutdown. Often that causes a file corruption and you need to do file checks. 
If Windows partition use Windows repairCD and run chkdsk. 
For Linux run fsck on every ext4 or ext3 partition from liveCD or flash drive installer.


 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by yekin on 2013-04-17
thanks oldfred,

i tried removing battery & holding power switch.. but it didn't work.

i installed the Boot Repair program on a USB and booted from it, it worked and it is ok.
everything works as usual. the problem is solved. :)

---


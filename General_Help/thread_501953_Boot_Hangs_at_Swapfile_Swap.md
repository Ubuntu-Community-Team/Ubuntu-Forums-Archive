---
title: "Boot Hangs at Swapfile Swap"
date: 2007-07-16
forum: General Help
---

### Post by JoFrhwld on 2007-07-16
Hi all.  I've just used the Wubi installer on my Windows XP machine.  The install went smoothly, and Ubuntu setup on reboot went smoothly as well.

Now, at the boot screen, I select Ubuntu, the splash screen pops up, and the status bar fills up about a third of the way along.  Then, it jumps back to the command line, and there it hangs.

The last two lines read:

*Mounting local file systems...        [ok]
*Activating swapfile swap...         

Any suggestions as to what to do?  Thanks a bunch.

---

### Post by ago on 2007-07-16
rename c:\wubi\disks\system.virtual.swap to c:\wubi\disks\system.virtual.noswap

ERRATA CORRIGE:
it should read c:\wubi\disks\swap.virtual.disk to c:\wubi\disks\noswap.virtual.disk

---

### Post by JoFrhwld on 2007-07-16
> **ago said:**
> rename c:\wubi\disks\system.virtual.swap to c:\wubi\disks\system.virtual.noswap

There is no c:\wubi\disks\system.virtual.swap.  There's a swap.virtual.disk in that directory.  Should I rename that noswap.virtual.disk?

---

### Post by JoFrhwld on 2007-07-16
I went ahead and renamed it noswap.virtual.disk and it booted up like a dream.  Thanks much.

---

### Post by dracule on 2007-07-17
tried it, but now it doesnt even get that far, keeps saying please wait, loading.

---

### Post by ago on 2007-07-17
Sorry it was a typo, the only file you have to rename is:

swap.virtual.disk -> noswap.virtual.disk

leave the other files in peace

---

### Post by luishang on 2007-07-17
Happens the same with dracula. It does not load..

---

### Post by zorblek on 2008-11-09
I am experiencing this same problem in Intrepid I have to wait about 5 minutes before it continues. The problem with the first workaround is that it leaves me without a swapfile, which I need because my computer doesn't have a lot of RAM. Will the same thing happen if I rename the swapfile?

---

### Post by Yashiro on 2008-11-10
Uninstall Ubuntu.
Boot in Windows and Defrag your drive.
Install Ubuntu.

---

### Post by zorblek on 2008-11-10
> **Yashiro said:**
> Uninstall Ubuntu.
Boot in Windows and Defrag your drive.
Install Ubuntu.

I actually already tried that after seeing it suggested elsewhere. No luck, unfortunately. I didn't notice any difference.

---

### Post by ago on 2008-11-10
just rename the swap file

---

### Post by Yashiro on 2008-11-10
Did you remove the actual files after the un-install? ( the .disk's)

The bug on the database indicates it's a problem with creating the file on a fragmented NTFS file system.

---

### Post by zorblek on 2008-11-11
> **ago said:**
> just rename the swap file

Will renaming the swapfile cause it to just not use a swap? Because I don't have enough RAM for that.

> **Yashiro said:**
> Did you remove the actual files after the un-install? ( the .disk's)

The bug on the database indicates it's a problem with creating the file on a fragmented NTFS file system.

I did.

---

### Post by el_oscuro on 2009-02-06
> **ago said:**
> Sorry it was a typo, the only file you have to rename is:

swap.virtual.disk -> noswap.virtual.disk

leave the other files in peace

My path is a little different (Ubuntu 8.10)

C:\ubuntu\disks\swap.disk -> C:\ubuntu\disks\noswap.disk

Otherwise, it worked perfectly.  Thanks!

---

### Post by jdwarta on 2009-04-11
> **el_oscuro said:**
> My path is a little different (Ubuntu 8.10)

C:\ubuntu\disks\swap.disk -> C:\ubuntu\disks\noswap.disk

Otherwise, it worked perfectly.  Thanks!

I had the same problem....
This fix worked GREAT for me :KS
My boot time was reduced from about 50 min to 2.5 min

---

### Post by bbrain on 2009-06-14
I have the same problem and windows is nowhere near my system.  The activating swapfile swap message appears followed by[OK] then the system thrashes the disk for ages.

I found that it is in /etc/rcS/S35mountall-bootclean.sh and it is trying to purge my /tmp filesystem.

ls -l on the root shows that /tmp is 6 gig but du -k shows only a few meg in use.  I  recently had a problem with the /tmp system having about 99000 html files from netbeans in it.  I fsck'd the disk and it found errors which I fixed manually.  Seems it didn't fix /tmp.

THE FIX!

as a last resort I logged in and became root......

sudo rm -r /tmp

then rebooted.  Presto problem fixed.  

But, I needed to chmod 777 /tmp and chmod +s /tmp to get the permissions correct.

I hope this helps others as I spent a day trawling through the startup script to find this.

Best of luck

---

### Post by antoniosanct on 2009-08-17
> **bbrain said:**
> I have the same problem and windows is nowhere near my system.  The activating swapfile swap message appears followed by[OK] then the system thrashes the disk for ages.


Few months ago I've occured the same to me, and I don't know how to fix. I thought that I could be that ntfs partitions are fragmented, and deactivating in /etc/fstab has no effect (the sh process hangs about 1 min, are or not in /etc/fstab)

I've attached a bootchart image as sample with ntfs active in /etc/fstab
[http://img37.imageshack.us/img37/4355/antoniojaunty200908043.png](http://img37.imageshack.us/img37/4355/antoniojaunty200908043.png)

and without ntfs active
[http://img406.imageshack.us/img406/9461/antoniojaunty200908172.png](http://img406.imageshack.us/img406/9461/antoniojaunty200908172.png)

Any ideas? Thanks a lot!! Regards!

---

### Post by antoniosanct on 2009-08-17
> **antoniosanct said:**
> Few months ago I've occured the same to me, and I don't know how to fix. I thought that I could be that ntfs partitions are fragmented, and deactivating in /etc/fstab has no effect (the sh process hangs about 1 min, are or not in /etc/fstab)

I've attached a bootchart image as sample with ntfs active in /etc/fstab
[http://img37.imageshack.us/img37/4355/antoniojaunty200908043.png](http://img37.imageshack.us/img37/4355/antoniojaunty200908043.png)

and without ntfs active
[http://img406.imageshack.us/img406/9461/antoniojaunty200908172.png](http://img406.imageshack.us/img406/9461/antoniojaunty200908172.png)

Any ideas? Thanks a lot!! Regards!

Any ideas about this??

Regards!!

---

### Post by ahoule on 2009-08-27
> **bbrain said:**
> ls -l on the root shows that /tmp is 6 gig but du -k shows only a few meg in use.  I  recently had a problem with the /tmp system having about 99000 html files from netbeans in it.  I fsck'd the disk and it found errors which I fixed manually.  Seems it didn't fix /tmp.

THE FIX!

as a last resort I logged in and became root......

sudo rm -r /tmp

then rebooted.  Presto problem fixed.  



Thanks for you message bbrain - it allowed me to go straight to the problem.  I was also working with Netbeans when the /tmp problem happened, causing the "Activating swapfile swap" message to hang forever at boot.

However, your fix did not work for me.  sudo rm -r /tmp, even with the proper permissions on /tmp, was running forever without result.  I finally logged in the Gnome environment and used gksudo nautilus to remove /tmp with nautilus.  I don't know why nautilus is more effective than sudo rm -r /tmp.

Cheers,

Alain

---


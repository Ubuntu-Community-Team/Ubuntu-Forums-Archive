---
title: "Equilivent of this AUFS mount"
date: 2022-07-01
forum: General Help
---

### Post by bonelifer on 2022-07-01
Was trying to figure out a way to mount two drive directory together. Found AUFS online, found example of what I wanted to do. Then found out devs decided to remove AUFS support from kernel.  What's the equivilent of this command with some other mergable(fs). 

```
sudo mount -t aufs -o dirs=/media/william/Data2/TWO=rw:/media/william/DataOrig/ONE/=rw -o udba=reval none /home/william/everything/
```

---

### Post by #&amp;thj^% on 2022-07-01
Have you tried yet with creating a Systemd unit?
Example found here: [https://unix.stackexchange.com/questions/81959/how-to-mount-aufs-file-system-on-boot-in-archlinux/255222](https://unix.stackexchange.com/questions/81959/how-to-mount-aufs-file-system-on-boot-in-archlinux/255222)
Older thread granted but  should still work today.

---

### Post by bonelifer on 2022-07-01
Xubuntu 20.04
Running my command gives me this:
```
mount: /home/william/everything: unknown filesystem type 'aufs'.
```

So I assume that your example wouldn't work for me.

---

### Post by Holger_Gehrke on 2022-07-01
overlayfs might be what you want. At least on 22.04 the module for it is included with the kernel. Details on the options for mounting an overlayfs can be found in the manual for 'mount'.

Holger

---

### Post by #&amp;thj^% on 2022-07-01
> **bonelifer said:**
> Xubuntu 20.04
Running my command gives me this:
```
mount: /home/william/everything: unknown filesystem type 'aufs'.
```

So I assume that your example wouldn't work for me.

Ok, I'll leave you with this for your consideration.
Systemd has native support for mounts (man systemd.mount). In fact systemd reads /etc/fstab, uses it to generate mount units, and mount the filesystems itself.
But I'll take your assumption at face value. ;)

---

### Post by Morbius1 on 2022-07-01
I hate when people answer questions this way but .......

I have never used aufs myself but I find it odd that the "devs decided to remove AUFS support from kernel" yet the aufs-tools package is still avalable in the repositories.

Did you install it?
```
sudo apt install aufs-tools
```

---

### Post by bonelifer on 2022-07-01
As I thought, since Ubuntu no longer has aufs kernel support baked in, systemd has no knowledge of the aufs filesystem. Output from journalctl -xe:

```
Jul 01 13:34:13 william systemd[1]: Mounting AUFS disk...
-- Subject: A start job for unit home-william-everything.mount has begun execution
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit home-william-everything.mount has begun execution.
-- 
-- The job identifier is 5000.
Jul 01 13:34:13 william mount[54811]: mount: /home/william/everything: unknown filesystem type 'aufs'.
Jul 01 13:34:13 william systemd[1]: home-william-everything.mount: Mount process exited, code=exited, status=32/n/a
-- Subject: Unit process exited
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- An n/a= process belonging to unit home-william-everything.mount has exited.
-- 
-- The process' exit code is 'exited' and its exit status is 32.
Jul 01 13:34:13 william systemd[1]: home-william-everything.mount: Failed with result 'exit-code'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The unit home-william-everything.mount has entered the 'failed' state with result 'exit-code'.
Jul 01 13:34:13 william systemd[1]: Failed to mount AUFS disk.
-- Subject: A start job for unit home-william-everything.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit home-william-everything.mount has finished with a failure.
-- 
-- The job identifier is 5000 and the job result is failed.


```

---

### Post by bonelifer on 2022-07-01
Yes, that was the first thing I did. I even restarted my computer to make sure.

```
&#10006; sudo apt-fast install aufs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aufs-tools is already the newest version (1:4.14+20190211-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
william@william:~ took 3s 

```

Apparently this has been a decision coming since from around the Ubuntu 12.xx days. Something about the code for AUFS being too dense and unreadable, with little documentation internally. They are pushing overlayfs. Unfortunately I can't make tails or heads of overlayfs examples. Why they waited this long, who knows.  :(

---

### Post by #&amp;thj^% on 2022-07-01
> **bonelifer said:**
> As I thought, since Ubuntu no longer has aufs kernel support baked in, systemd has no knowledge of the aufs filesystem. Output from journalctl -xe:

```
Jul 01 13:34:13 william systemd[1]: Mounting AUFS disk...
-- Subject: A start job for unit home-william-everything.mount has begun execution
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit home-william-everything.mount has begun execution.
-- 
-- The job identifier is 5000.
Jul 01 13:34:13 william mount[54811]: mount: /home/william/everything: unknown filesystem type 'aufs'.
Jul 01 13:34:13 william systemd[1]: home-william-everything.mount: Mount process exited, code=exited, status=32/n/a
-- Subject: Unit process exited
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- An n/a= process belonging to unit home-william-everything.mount has exited.
-- 
-- The process' exit code is 'exited' and its exit status is 32.
Jul 01 13:34:13 william systemd[1]: home-william-everything.mount: Failed with result 'exit-code'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The unit home-william-everything.mount has entered the 'failed' state with result 'exit-code'.
Jul 01 13:34:13 william systemd[1]: Failed to mount AUFS disk.
-- Subject: A start job for unit home-william-everything.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit home-william-everything.mount has finished with a failure.
-- 
-- The job identifier is 5000 and the job result is failed.


```
Seems your right.
> 

    In light of the concerns about overlayfs being sufficiently cooked in time for Precise, Andy Whitcroft and I have decided to re-enable aufs We will continue to advocate for dropping aufs in favor of a sufficient upstream solution at each development cycle. This means that aufs will disappear in future backported LTS kernels.

    In other words, don't bet your business on aufs.

And This.
> * AUFS is not upstream.  Despite previous efforts from it's
    maintainer, it does not appear it will ever land upstream.
  * AUFS is a maintenance burden for the Ubuntu Kernel Team due to
    the fact that it is not upstream.
  * Support for OverlayFS has been available since Oneiric.  We have
    been encouraging migration to OverlayFS. The installer has
    already transitioned to using OverlayFS (which was done in
    Oneiric). 

So Holger_Gehrke is pointing to it already here.

---

### Post by bonelifer on 2022-07-01
I already knew all that from researching this. My post specifically asks for an equivalent version for another FS. **bonelifer** longs for the days when people didn't "TL;dr" but actually read everything. :(  Thanks though for your example, maybe if I can get an equivalent for another supported FS, I'll be able to use it.

---

### Post by #&amp;thj^% on 2022-07-01
I read it all, but my disbelieve is where I error-ed. ;)
Good Luck

---

### Post by bonelifer on 2022-07-01
I think I have it with:
```
sudo mount -t overlay -o lowerdir=/media/william/Data2/TWO/:/media/william/DataOrig/SPOTIFY/ONE/,upperdir=/media/william/upper/,workdir=/media/william/work/ overlayfs /home/william/everything/
```

Had tried this multiple times, then checked my upper, work directories. Only work existed, thought I had created upper.  

One last question is there a way to make the everything directory writable?

---

### Post by #&amp;thj^% on 2022-07-01
It's been awhile, but someone else asked me this and my mind is bit fogy.
The solution is to use overlayfs in combination with bindfs that allows mount one folder as another folder with different perms/owner/etc.
If you still need help a quick google should turn up somethings or Ideas.

---

### Post by bonelifer on 2022-07-01
The answer found was mergerfs:
```
sudo apt-get install mergerfs
```

```
sudo mergerfs -o allow_other,use_ino /media/william/Data2/TWO:/media/william/DataOrig/ONE /home/william/everything/
```

Now both directories show up as one and the merged directory is still writable(hopefully).

In case you or anyone else is wondering. In our house I'm an the doer of things, maker of happening, the ripper of cd's to music files. Need the files and their contents editable for puddletag, kid3, etc. But want to keep my music and my sister/b-i-l's separate, but still have all the music available to MPD.

---

### Post by #&amp;thj^% on 2022-07-01
Cool let us know if that's the case.

---


---
title: "External USB Hard Drive in ext3: Permissions"
date: 2007-03-18
forum: General Help
---

### Post by pgn674 on 2007-03-18
I have an external USB hard disk drive, newly formatted as ext3. It mounts OK, and I can browse to it in the file browser, but I can't write to it. I don't have the permission to, it says. There's 1 folder in there now, lost+found, but I don't have permission to even view its contents.

In my research, I found that editing fstab might help. So I tried adding this line:
```
/dev/sda1   /media/usbdisk   ext3   defaults   0   0
```
But that seemed to have no effect, even though I unmounted and re-plugged in the HDD.

Changing it to this just made it so that it wouldn't mount:
```
/dev/sda1   /media/usbdisk   ext3   rw,umask=0777,user   0   0
```

So, anybody know how to get an external USB drive formatted as ext3 write-to-able? I'd like it to be permanently writable, so I don't have to run some command each time or something.


Oh, and while we're on the topic, I choose ext3 because it's kind of standard, and has journaling, in case this usb drive is a bit unstable. Does fsck have better luck with ext3? Or would you recommend a different file system? I'll be using this drive mostly for mass storage of not especially critical data.

---

### Post by floke on 2007-03-18
I had this with a USB once - after I tried to use Unison on it. Anyway, I think you have to change the permissions on it using the chown command - am not entirely sure how it works but I think its something like 'sudo chown [device path] [user]:[group]' - so eg sudo chown /media/usbdisk bob:bob

This might not be exactly it - so have a scout around if it doesn't work.

You could also try to change the permissions through the GUI - open nautilus with gksu (NOT SUDO) - so gksu nautilus - then navigate to the USB - right click - and change the permissions to writeable - make sure you select the recursive option to change all files within the USB too.

---

### Post by pgn674 on 2007-03-18
That first one did it, thanks Steve.K :) 

For future forum searchers, here's what I did:
I took off any changes I did to fstab. Then I did this in terminal:
```
sudo chown paul /media/usbdisk
```
Where paul in is login name, and /media/usbdisk is the mount point I think. I got that by looking in /media and seeing a folder named usbdisk. I then unmounted and re-plugged in the drive, and all was working. Even after a restart of the system.

Hope this helps you people from the future. Oh, and I'm not sure if this chown command would have trickled down to any files I already had in the drive; I didn't have any.

---

### Post by Dooglus on 2008-01-26
chown doesn't 'trickle down' unless you use this flag:

	-R, --recursive
		operate on files and directories recursively

see "man chown" for the manual.

---


---
title: "wubi-resize"
date: 2013-03-03
forum: General Help
---

### Post by huynhhuuhieu on 2013-03-03
I installed Kubuntu with Wubi on 10 gigabyte virtual disk
I try resize that virtual disk with  'wubi-resize-1.6' but I get some error. I need help

```
kuapps@ubuntu:~$ cd ~/Templates/wubi-resize-1.6
kuapps@ubuntu:~/Templates/wubi-resize-1.6$ sudo bash wubi-resize.sh 13
wubi-resize.sh:  A new virtual disk of 13 GB will be created. Continue? (Y/N)
y
wubi-resize.sh: Creating new virtual disk (new.disk)...
wubi-resize.sh: Formatting new virtual disk as ext4.
wubi-resize.sh: Copying files - this will take some time.
wubi-resize.sh: Please be patient...
wubi-resize.sh: Copying from root (/)
[U]rsync: read errors mapping "/lost+found/#148185": Input/output error (5)
rsync: read errors mapping "/lost+found/#148185": Input/output error (5)
ERROR: lost+found/#148185 failed verification -- update discarded.
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
wubi-resize.sh: Copying files failed or was canceled. Return code: 23
wubi-resize.sh: Correct errors and rerun with --resume option
wubi-resize.sh: Please wait - cleaning up...
wubi-resize.sh: Operation aborted[/U]
```

---

### Post by Mark Phelps on 2013-03-03
Not a Wubi expert -- as I don't use it -- but since it is installed inside an NTFS partition, I would do a CHKDSK from inside Windows.  To do that, you have to select Computer, right-click on the "drive" (what Windows calls partitions), select properties, and select the option to check for errors.

After that run, you can try again.

---

### Post by huynhhuuhieu on 2013-03-03
thanks
I've done it manually (not 'wubi-resize.sh' ) then succeed

---

### Post by bcbc on 2013-03-03
If rsync is finding errors there's likely ext4 corruption. You could run fsck to correct.

How did you do it manually without rsync (or did you just ignore errors - which is probably okay if it's just your lost & found kicking out errors). But sometimes you could be missing real data if you ignore errors.

(The script doesn't make any judgement calls for obvious reasons. If there are errors it just displays them and exits.)

---

### Post by huynhhuuhieu on 2013-03-05
The intruction's [here]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk#Manual_resize")

---

### Post by bcbc on 2013-03-05
Those manual instructions use the same rsync command so it's a little strange it didn't give you the same errors.

PS... From release 12.10, Ubuntu uses an ACL (access control list) on the /media/<username> directory, which is used as a mountpoint. The ACL won't have been copied over based on the rsync options in either the script or the manual instructions. 

I will get around to updating that soon, but if you find that when you mount a USB you don't have access (only root does) then the easiest fix is to remove the /media/<username> directory and let it get recreated automatically.

```
sudo rmdir /media/<username>
```

PS that won't work if something is mounted. Don't try an rm -rf instead. Just run it when nothing is mounted. 

Reference (this relates to the wubi migration which has been fixed already, but the same problem will be present on the resize): [http://askubuntu.com/q/245586/14916](http://askubuntu.com/q/245586/14916)

---

### Post by huynhhuuhieu on 2013-03-07
thanks for the suggestion

---


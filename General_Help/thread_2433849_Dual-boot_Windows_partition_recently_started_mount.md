---
title: "Dual-boot Windows partition recently started mounting as read-only"
date: 2019-12-26
forum: General Help
---

### Post by jon-carmicheal on 2019-12-26
I've been dual-booting my laptop with Windows 10 and Ubuntu 19.10 for a while, and until recently I've been able to mount the Windows partition in read-write mode (it was like that by default) and write files to it.  I keep most of my pictures there.  But today I discovered that the Windows partition is getting mounted as read-only by default when I click on it in Nautilus, and even if I try to "mount -o remount,rw device mountpath" it returns an error when I try to write a file to it: "No such file or directory."  I'm not sure if it was a recent Ubuntu update or Windows update that caused it to start failing like this.  What could be the cause of this, and what would be the solution?

---

### Post by oldfred on 2019-12-26
Windows updates may turn fast start up back on. Or perhaps an abnormal shutdown corrupted NTFS partition and chkdsk is required.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by yancek on 2019-12-26
I'm not sure from your post if you are putting your pictures on your windows OS system partiton or not.  It would be better to have a separate data partition on which to keep personal files, formatted ntfs would work then you could access from either windows or Linux.  The advantage of this is that if your windows OS crashes for whatever reason and is no longer bootable, you can access personal files from Linux.  I expect the problem you are having is what oldfred mentions above as that is a very common scenario.

---

### Post by jon-carmicheal on 2020-01-02
Fast boot was indeed the issue.  Once I disabled that, I was able to mount it in read-write mode within Linux.  Thanks!

---


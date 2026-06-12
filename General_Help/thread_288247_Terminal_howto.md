---
title: "Terminal howto"
date: 2006-10-29
forum: General Help
---

### Post by evilc on 2006-10-29
I have 2 HD's the 2nd one I use as backup and downloads, when I open Terminal it starts in clive@clive my main drive how do I change from there to access the 2nd drive called drive2. At the moment I d/l to drive2 then move file to drive1 (clive) a bit silly,to use the Terminal.

TIA

---

### Post by jasmuz on 2006-10-29
Hello,

To change to the other drive, you must change your path to where its mounted.
Example

cd /media/drive2

Then you will be in drive2

To move files around using the terminal its as simple as:

mv (move)
cp (copy)

mv /home/user/file.foo /media/drive2

---

### Post by .t. on 2006-10-29
rm (remove)
ls (list directory contents)
aptitude (package manager)
ps (show active processes)
kill (kill process by id)
killall (kill process by name)

Those last three are useful.

All of them have man pages. To learn about man (this is really boring), run "man man". To see a man page, "man <page>".

Read about the fs structure in UNIX. Or learn it, as I did, the hard way.

All of these are very handy.

---

### Post by pdub on 2006-10-29
I have a similar setup with 2 drives, I have created a mount point for the second drive and called it **data**. Follow these steps to do the same:

Open a terminal

**sudo mkdir /data**

Next you need to set permissions, I set myself as the owner of the new folder.

**sudo chown pdub:root** /data  (set your login name instead of pdub)

**sudo chmod 775 /data**

**sudo gedit /etc/fstab**

Add the following to the bottom of the file

/dev/**sdb1** /data **reiserfs** defaults        0       2

Change the drive to match your drive, i.e - if you have IDE drives it will likely be /dev/hdb1 

Also change your file system type to match, mine is reiserfs yours may be ext3 or something else.

Then you can just type cd /data

pdub

---

### Post by evilc on 2006-10-29
> **jasmuz said:**
> Hello,

To change to the other drive, you must change your path to where its mounted.
Example

cd /media/drive2

Then you will be in drive2

To move files around using the terminal its as simple as:

mv (move)
cp (copy)

mv /home/user/file.foo /media/drive2

I'm an idiot forgot drive2 was under /mnt duh. Thanks

---


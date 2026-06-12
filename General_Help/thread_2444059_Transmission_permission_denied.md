---
title: "Transmission permission denied"
date: 2020-05-24
forum: General Help
---

### Post by jlparsons on 2020-05-24
Hi folks, I have a problem that I cannot get transmission to use a mounted btrfs partition (fstab defaults) as download directory no matter what I do.  I previously had the same setup on my Ubuntu Server 16.04 install using an ext4 disk mounted in the same location, now I've got a fresh Ubuntu Server 20.04 install and the disk is using btrfs.

 I've followed the howto ([https://help.ubuntu.com/community/TransmissionHowTo](https://help.ubuntu.com/community/TransmissionHowTo)) very carefully several times, even purging the ppa and packages and reinstalling from scratch twice.  The btfs directory is mounted at ~/bulkstorage and I've been very careful to set the owner as me and permissions as 750, 770 and 777 to no avail.  I've also tried running the transmission/daemon as my user.

If I set the download directory as ~/ it works great, if I set it as any directory on the mounted drive it says permission denied regardless of the owner of that directory, its permission or what user the daemon is run as (even root).  I'm at a loss!

---

### Post by TheFu on 2020-05-24
Is it a snap package?
```
$ snap list
```

Snaps are usually constrained to only allow access to the userid's HOME. For something like Transmission, that's probably a good thing, just create a special userid and set the HOME directory to the location you want files to be saved.  
HOME directories must be native Linux file systems, not NTFS or FAT-whatever.  That's for lurkers.  BTRFS should be fine.

And please don't ever setup any directory with 777 permissions.

---

### Post by jlparsons on 2020-05-24
> **TheFu said:**
> Is it a snap package?
```
$ snap list
```

Snaps are usually constrained to only allow access to the userid's HOME. For something like Transmission, that's probably a good thing, just create a special userid and set the HOME directory to the location you want files to be saved.  
HOME directories must be native Linux file systems, not NTFS or FAT-whatever.  That's for lurkers.  BTRFS should be fine.

And please don't ever setup any directory with 777 permissions.

I don't think so.  Certainly snap list doesn't show anything to do with transmission?
I used the daemon as root and 777 from desparation tbh and only for as long as I needed to check that it was definitely nothing to do with permissions.

---

### Post by TheFu on 2020-05-24
Exactly, how did you start the transmission service? Which userid?

Running some programs with sudo/root will create files in unexpected places and prevent a normal userid from running those tools again.

BTW, I know next to nothing about transmission.  We've just seen a bunch of snap confinement problems recently, so that was a guess.

---

### Post by SeijiSensei on 2020-05-24
You might want to check the integrity of the btrfs filesystem. If a filesystem has errors, Linux will mark it read-only.  Can you write other files to that filesystem using the same username as you're using with Transmission?

---

### Post by jlparsons on 2020-05-24
As described in the howto,
sudo service transmission-daemon start
[FONT=inherit][/FONT]sudo service transmission-daemon stop
[FONT=inherit][/FONT]sudo service transmission-daemon reload

---

### Post by jlparsons on 2020-05-24
> **SeijiSensei said:**
> You might want to check the integrity of the btrfs filesystem. If a filesystem has errors, Linux will mark it read-only.  Can you write other files to that filesystem using the same username as you're using with Transmission?
New partition, new disc, recently scrubbed with no errors.

---

### Post by TheFu on 2020-05-24
> **jlparsons said:**
> As described in the howto,
sudo service transmission-daemon start
[FONT=inherit][/FONT]sudo service transmission-daemon stop
[FONT=inherit][/FONT]sudo service transmission-daemon reload

[LIST]
[*]What userid does the service run under?
[*]What are the permissions for the directories where files are to be stored? **ls -l**
[*]Are the mounts read-only?   Lots of ways to check that. I'd probably use **mount** and grep to filter the output.
[/LIST]

---

### Post by jlparsons on 2020-05-24
> **TheFu said:**
> 
[LIST]
[*]What userid does the service run under?
[*]What are the permissions for the directories where files are to be stored? **ls -l**
[*]Are the mounts read-only?   Lots of ways to check that. I'd probably use **mount** and grep to filter the output.
[/LIST]


I've tried running the service as me, as root and as [COLOR=#333333][FONT=UbuntuMono]debian-transmission.
Directory permissions are all [/FONT][/COLOR]drwxrwx--- but I've also tried 777ing the lot.
No, the mounts are tested read/write.

I've set up transmission a bunch of times on this and other headless boxes and never had this issue.  Literally the only difference this time is that it's 20.04 and the filesystem is btrfs.  FYI I've now also tried with the install on / being btrfs as well, still the same issue arrises.

---

### Post by TheFu on 2020-05-24
drwxrwx--- without showing the owner and group isn't too useful.

---

### Post by jlparsons on 2020-05-24
All me:users (standard for ~/?)

---

### Post by jlparsons on 2020-05-25
Well, adding debian-transmission to users appears to have fixed it.  Odd.  I confess I am still somewhat in the dark;

sudo usermod -a -G users debian-transmission

Edit:  or possibly more likely the fact that transmission 3.0 released yesterday fixed it....

---

### Post by TheFu on 2020-05-25
It was a permissions problem. Seeing the full **ls -al** for the directory would likely have made that clear.
Happy you found the solution and shared that. Please mark this thread as solved - "Thread Tools" button near the top of the page.

---


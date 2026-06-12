---
title: "sudo not working"
date: 2006-10-24
forum: General Help
---

### Post by hakan69 on 2006-10-24
Hello!
I have tried to install an extra hdd, and twice messed up my system beyond use. Now, when I try to sudo I get an error message: *sudo: must be setuid root*. I can't run any administrative tasks, for example if I try to run Disks, after a message "Trying to start disks" nothing happens. Also connection to my lan is down.
The second time, after reinstalling Ubuntu I tried to add an extra hdd. I created a folder in my /home/nih folder and called it Disk2. I then ran disks, browsed to the folder I just created, formatted (ext3)and activated my new disk.
When I tried to open my Disk2 folder, it was locked and I (nih) had no permissions in this folder (Disk2) so in terminal I wrote: sudo chown -R nih:nih / /home/nih/Disk2
This gave me full rights to Disk2, but I also ran into the problems described above.
My group and sudoers files are exactly as in the examples I've been directed to.
Very greatful for any help, I really hate the thought of giving up!

---

### Post by Ramses de Norre on 2006-10-24
Did you really do this: (watch the "/" after "nih")
```
sudo chown -R nih:nih **/** /home/nih/Disk2
```
In that case you've set the ownership for **every file** on your system to nih:nih because you used chown recursively on /.
That would explain your issue and the only fix despite days of searching and changing ownerships will be a reinstall..

---

### Post by threegremlins on 2006-10-24
If your secondary drive is connected when you install ubuntu it should configure it into fstab, don't do it after. 

If you look for it, there's a root-sudo help on the ubuntu website. Look in Support , up there on the right between Community  and Partners.

---

### Post by mssever on 2006-10-24
Here's a tip: Any time that you can't access a disk that you've mounted, the problem is in /etc/fstab (or however the mount options were passed), not the mount point.

---

### Post by Ramses de Norre on 2006-10-24
Ignore this..

---


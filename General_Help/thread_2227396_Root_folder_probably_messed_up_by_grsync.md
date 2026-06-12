---
title: "Root folder probably messed up by grsync?"
date: 2014-06-01
forum: General Help
---

### Post by astronos2007 on 2014-06-01
Hi, guys! I tried today to make a backup of my whole root folder and I found a simple GUI program, called grsync. I used it to backup my root partition (/dev/sda3) and copy everything to /dev/sda5 (both 190GB space). I chose the second option of the program (Sync source with destination) and let it run. I went outside and let it do it's job. When I returned, everything was **cked up! All the programs were gone, nothing was found. I tried to open the terminal but it gave me errors that xfce-terminal could not be found. I tried to relogin, but I was told "xfce-session-logout cannot be found". What the ...??? All my shortcuts were broken and I couldn't even start the file manager. Now system hangs after the boot animation... I am writing now from a live Ubuntu 12.04 CD, because I cannot boot, but I used gParted to look at the partitions... Curiously, the partition in which grsync was supposed to put the root directory is full (190/190GB), but I didn't have a full root partition, I had almost 30 GB free. What happenned? I unmounted other partitions so it didn't copy the mounted folders.

[IMG]http://s23.postimg.org/vyqfmzwd7/Screenshot_from_2014_06_01_23_56_02.png[/IMG]

I entered the sda3 partition (root) and NOTHING appears changed. What **cked up my system? Can you please help me? Thank you!

---

### Post by astronos2007 on 2014-06-02
Update: I entered text mode and tried to login as my user (skynet). The login works but then it doesn't recognise any command I give. Sudo not found, nano not found, reboot not found, etc. And sometimes I get permission denied. Surprisingly, on root account everything works. It is like I now do not have access even to start the OS with my user, probably that is why it hangs at boot? Can somebody give me a suggestion please?

---


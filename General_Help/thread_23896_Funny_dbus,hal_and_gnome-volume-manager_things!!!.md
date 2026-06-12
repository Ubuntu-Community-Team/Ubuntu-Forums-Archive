---
title: "Funny dbus,hal and gnome-volume-manager things!!!"
date: 2005-04-04
forum: General Help
---

### Post by gbil on 2005-04-04
Hello, 
I know that this is my first post here but I have followed the forum for a quite some time because I wanted to change from Suse to Ubuntu. Everything with Ubuntu is fine except the known problems with auto mounting and icons not appearing in the desktop.

Since I had compiled hal, dbus and gvm myself for use in my old Suse machine I have some knowledge over the correct function of these programs so I tried to 'debug' their operation so as to find what causes these problems.

What I found is that the packages distributed with Ubuntu don't follow the original operation like when you install dbus,hal and gvm from source.

For example, when you plug-in an external drive the original function is that hal alters the fstab file according to the options in the fdi's and then gvm mounts the new partitions. So hal adds /dev/sda1 in the fstab and then gvm mounts it.

In the Ubuntu version hal just recognises the partition and creates the mount point as it should BUT it doesn't change fstab and gvm mounts the partitions. This has the disadvantage that if you want to umount the partition throught the 'Computer' location you can't because there is no entry in fstab and in general you can't umount the partition with any way that relies on a fstab entry. 

What I suggest to the Ubuntu people is that they compile hal with the option to alter fstab which is a 'safer' way to do things. I strongly believe that this could solve all the problems with icons not appearing etc.

---

### Post by sig on 2005-04-12
I am having the exact same problem. I upgraded from Warty to Hoary 5.04. In Warty the gnome-volume-manager worked fine and now in the upgrade to Hoary it is broke. I ran tail -f /var/log/messages and ran through the whole issue and came to the conclusion that it is definately the gnome-volume-manager issue. I hope they fix this.

---

### Post by mendicant on 2005-04-12
I can unmount things just fine with the icons that show up on the desktop or in the Computer location in nautilus.  Problems only occur if I unmount it, then manually mount it (to some place not under media).  As long as it is under /media, it can unmount via the icons.  Of course, the command line always works, no matter where I mount things.

---

### Post by artinla on 2005-04-12
I have been battling the exact same thing.  I also have a problem that gives me a "HAL could not be initialized" most of the time when I reboot.

Most people are getting this working by reinstalling all HAL related entries in synaptic.  I wasn't so lucky.

I discovered that if I run the following script twice, things will start working on the second try. I just put a launcher on the desktop and run it twice each time I reboot.

#(this restarts the HAL/DBUS and GVM)
sudo /etc/init.d/dbus-1 restart
wait
gnome-volume-manager

Obviously not the best way, but it works.

Art

---

### Post by mendicant on 2005-04-13
This thread is a little strange.  There are two issues here.  One is that the behavior isn't as expected (the fstab thing of the original poster), and the other is sig's followup which isn't really the same problem.

My own response was to the original poster, and Art's response was to sig.

---

### Post by artinla on 2005-04-13
You are correct, I was responding to Sig, because the original poster was mainly just making a suggestion.. not asking for help.  That post was more than a month old.

Nonetheless, I wish someone would figure out whatever is causing this.

Art

---

### Post by mendicant on 2005-04-13
Yeah, I just wanted to make it clear to the people reading this thread in the future.  The original post isn't that old--April 4th, according to the date on the original post.  Perhaps you need to make a new thread, though, so that it is clear that you have a separate issue--I know that when I look at a post, I look to the original post to see if it is something I'm interested in (or something I can help with).

---


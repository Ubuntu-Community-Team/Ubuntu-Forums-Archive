---
title: "Boot-Repair-Disk Reports / is nearly full"
date: 2013-01-25
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-01-25
I don't have the GRUB Rescue Screen due to a video card exchange. I saw the number of old kernels a few days ago and started deleting about half of them. I was very very careful to not delete my

3.2.0.36-generic-pae ( or very close to those numbers)

or any with matching numbers.

After those 20 or so old kernels were manually deleted, the OS would no longer boot. So here I in LiveUSB and need help in deleting the out of date kernels. I could not perform that in boot-repair-disk session; even though it said I should. Maybe I'm not familiar with how it operates. It's my first use of it. Meanwhile in Boot-Repair-Disk the number of old kernels looked to be around 50, even though I though I manually deleted about half of them. And in another section of the  Boot-Repair-Disk, under the heading GRUB, the old kernels were still there, too. 

How can I get this line to work in LiveUSB (same as LiveCD)

sudo apt-get remove $(dpkg -l|egrep '^ii  linux-(im|he)'|awk '{print $2}'|grep -v `uname -r`)

Above found at: [Remove all unused kernels with 1 command in debian based systems]("http://www.unixmen.com/remove-all-unused-kernels-with-1-command-in-debian-based-systems/")

---

### Post by papibe on 2013-01-25
Hi Mark_in_Hollywood.

What do you mean by 'manually deleted'?

Are you able to boot into recovery mode?

Regards.

---

### Post by Mark_in_Hollywood on 2013-01-26
No "[Recovery Mode]("http://ubuntuforums.org/showthread.php?t=2108382")" due to faulty video card. (I advise: don't ask 'bout that).

I've been without my computer for about 48 hours now. I cannot find the Chrome Browser page from several days ago, but I assure you that 

1 - it's a command line

2 - it is up-to-date for Precise Pangolin ver 12.04 LTS

3 - I did NOT (repeat NOT) tamper with the current kernel and it's associated files.

4 - I have to delete these out of date files (kernels) and found several posts online, but none talk about how to do this while in LiveCD (actually LiveUSB) mode.

5 - I'm sorry I cannot give you more information.

---

### Post by papibe on 2013-01-26
(I read your PM)

This is what I would do.

You can use the Live media to mount and bind the actual partitions of your broken system. Then you can 'chroot' to the broken system.

Once that is set up, you can uninstall packages using apt-get as if you were on your system.

Take a look at the section called 'Fixing a Broken System -> via chroot' in this [tutorial]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot"). Also here you can find [another]("http://aaronbonner.tumblr.com/post/21103731114/chroot-into-a-broken-linux-install") helpful tutorial.

Let us know if you need more help with that.
Regards.

---


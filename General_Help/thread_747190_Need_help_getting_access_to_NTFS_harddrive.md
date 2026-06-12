---
title: "Need help getting access to NTFS harddrive"
date: 2008-04-06
forum: General Help
---

### Post by Maupertus on 2008-04-06
Hi everyone, 

I've got a big problem and I really hope someone can help me.
Today I wanted to do some gaming, so I booted into windows. I wanted to update Daemon Tools (unrelated to gaming, I was just updating a lot because I haven't booted into windows for a long while) and uninstalled it first, then rebooted.

Somehow, this broke my windows install, I thought it shut down correctly, but now when I try to boot windows I get a black screen.

Now normally this wouldn't freak me out to bad as I don't really use XP anymore. But it has one huge drawback. I knew that when windows didn't shut down properly and I started up Gutsy, I couldn't acces my 250Gig shared harddrive with all my data on it.

Now, I can't get into it either, and where I normaly would restart windows and make sure I shut it down correctly, this isn't an option. Can someone please tell me that it is still possible to mount my harddrive correctly! I'm having a lot of trouble at the moment as all my personal files and work-related documents are on the disk.

Thank you for your help.

---

### Post by vanadium on 2008-04-06
The best thing would really be to use Windows. The worst thing in my opinion is to use mount -force: I have become scared of that since I read a post here where the partition table of the drive was damaged after force mounting an ntfs partition. I would take my chance with the linux utility ntfsfix, which can fix most common errors on ntfs volumes. If you do not have the command available, you will need to install the package "ntfsprogs" using Synaptic or apt-get.

---

### Post by Tomatz on 2008-04-06
Put your **xp install disk** in and boot it.

When it has finished loading you should see at the bottom of the screen *"press R for recovery console"* **press R**

log into the console and type at the dos prompt:

**chkdsk /r**


That should fix your ntfs partition/drive ;)

---

### Post by Maupertus on 2008-04-07
Hi guys, thanks for the quick reply, I will try them this evening and keep you posted. 

I've been brooding on my frustration and had this thought:

"Isn't this a good moment to step over to Ubuntu Completely, starting with Hardy Beta, I haven't used XP in ages."

If one of the sollutions poste above shouldn't work, and I did a complete clean install of Hardy, would that help me regain control of my 2nd HD, or would it completely borkify it?


EDIT:  [QUOTE=NTFSProgs website]ntfsfix is quite an old utility.

Its name is quite misleading, as its goal is not to fix the volume, but to mark is as dirty, so that Windows will fix it at the next reboot.

That technique was neccessary in the days of the old kernel_driver (version 1.X), that allowed unsafe writing support. And unsafe mean that it trashed volumes badly. So a way was neccessary to clean the mess afterwards, and Windows was the best tool for doing that at the time (and still quite effective today, although there are some 3rd party tools too, but most of them run on Windows - Sweet Irony).

To find out what driver version you have, type:

modprobe ntfs
dmesg | grep ntfs

If you are using the old kernel_driver (version 1.X), which is usually found in 2.4 Linux kernels (some vendors patch it to update it to the new kernel_driver). Make sure you run ntfsfix after you unmount your volume, or you will face corruption of your volume![/QUOTE]

Would this work as I can't boot Windows?

---

### Post by vanadium on 2008-04-07
Thank you for the info on ntfsfix you looked up. This is one more reason to abandon ntfs if you are not using Windows anymore. To "regain control" you will need to check and fix the drive anyway, whether or not you do a fresh install. There now seems no other linux option than  mount --force, but this is no repair: it just can allow you to read the data nevertheless.

---


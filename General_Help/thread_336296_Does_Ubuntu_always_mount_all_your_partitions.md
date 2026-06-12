---
title: "Does Ubuntu always mount all your partitions?"
date: 2007-01-11
forum: General Help
---

### Post by jincast90 on 2007-01-11
Hello. I have promised my friend to bring a live cd for him, so he can backup all the stuff which is on NTFS and FAT32 partitions, because It won't boot into Windows. Now I was just wondering if Ubuntu always mounts all FAT32 and NTFS partitions on the system, so you can read what is on them, eg. copy what is on them, and paste it onto an external harddrive?

---

### Post by lyceum on 2007-01-11
I have never had a problem w/ external hard drives. Internal, just make sure the jumpers are set correctly. 

As for what it sounds like you are trying to do, recover data, not sure if it will work. May work better if you remove the hard drive and mounts it externally to another PC. My past results are win some-lose some.

---

### Post by jincast90 on 2007-01-11
> **lyceum said:**
> I have never had a problem w/ external hard drives. Internal, just make sure the jumpers are set correctly. 

As for what it sounds like you are trying to do, recover data, not sure if it will work. May work better if you remove the hard drive and mounts it externally to another PC. My past results are win some-lose some.

Well its a laptop.

Otherwise, can someone recommend a way to backup what are on the hard drives, if you are not able to log into your OS?

---

### Post by odin1965 on 2007-01-11
I've had mixed results using the live CD on different systems. Sometimes all the partitions automount and there is an icon on the desktop for them. Then it is easy to back them up.

If they don't automount, open up Gparted (System => Administration => Gnome Partition Editor) and you will be able to see what partitions are available. If none show up, you may have a bad harddrive. If your drive is visible in Gparted, it will show you what paritions there are (hda1, hda2, etc.

Open a terminal and type;
cd Desktop
sudo mkdir windows
sudo mount /dev/hda1 /home/ubuntu/Desktop/windows   <= where hda1 is the name of your windows partition from Gparted

You should now have a folder on your desktop with your windows drive in it.

---


---
title: "Mac - Windows - Linux"
date: 2007-06-01
forum: General Help
---

### Post by FRGus723 on 2007-06-01
I am relatively new to Linux and have a few questions. In a recent attempt to ditch Micro$oft I took a laptop and loaded Ubuntu Feisty. I have 2 USB NTFS drives attached to the Linux box which I can read movie and MP3 files from just fine. I have the old Windows laptop also hard wired to my network which I am solely using as an Azureus bittorrent machine (mainly because I can't write to the NTFS drives without having to first convert to FAT32 or EXT2/3 which I don't wish to do for data integrity) I also have a MacBookPro (my primary machine) and 5 other machines which connect wirelessly to the network and can also play all the movie and MP3 files from the USB drives connected to the Linux box. The question I have is now when I am done downloading a torrent to the windows box and try to copy the files to the NTFS USB drive connected to the Linux box I get a permission error. I am not trying to write to the USB drives from Linux but rather copying an AVI or MP3 file to it from a Windows box.

Can someone, in plain beginner language, explain how I would set permissions on the USB drives to be able to write to them from a Windows box. The linux box will never try to write to them nor do I need them to. I want the USB drives in NTFS so when I take the drive to friends houses who have Windows boxes they can read the files. So changing the file structure on the drives is not what I am looking for, just the ability to write to it from a Windows box. My thought is I probably need to go to etc/fstab and do a chmod to the mount point for the USB drives but I haven't tried this yet. Is this the right first step?

Anyone have some suggestions? Thanks for your help.

---

### Post by raja on 2007-06-01
I think the question is confusing. What exactly are you trying to do? You are trying to copy the files to an USB hard drive formatted as NTFS from Ubuntu?

---

### Post by FRGus723 on 2007-06-01
I am just trying to copy an avi file from a windows laptop to an NTFS USB drive connected to a linux box over the network.

---

### Post by Completenutter2 on 2007-06-01
That sounds like the right step to me, give those things a go, and get back to us :)

---

### Post by raja on 2007-06-01
> **FRGus723 said:**
> I am just trying to copy an avi file from a windows laptop to an NTFS USB drive connected to a linux box over the network.

The NTFS drive will be mounted read-only on Ubuntu. I guess that is why you are unable to write to it (even if it from the windows box). Can you not attach the drive to your windows pc and do this? The other option is to use ntfs-3g - I have been using it for quite some time and it seems very stable.

---

### Post by PilotJLR on 2007-06-01
I think I understand what you're asking... so the NTFS USB drive remains physically connected to your linux system, and the windows machine wants to write to it via the network (using a Samba share). Is this correct?

If so, your linux system IS trying to write to it. Keep in mind SMB / CIFS merely presents a SMB / CIFS share to the clients; it does not present a filesystem. Windows is then writing to the CIFS share, and your Linux system "translates" that into the local filesystem. This clearly requires write permissions.

If my understanding of your situation in paragraph 1 is correct, then you must install and use the ntfs-3g drivers and enable external NTFS read/write.

---

### Post by FRGus723 on 2007-06-02
Hey Pilot

Yes you understand my dilemma.  So I guess even though I feel like it is windows to usb over the network, since the drives are connected USB to the linux laptop I am having linux try to write to the drive.

I have loaded the NTFS-3G drivers from the synaptic package manager but I am unsure what to do when you say "enable read/write"  can you explain for a linux noob how to do that?

Thanks

---

### Post by jjacobs2 on 2007-06-02
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
skip to step 3 I guess

---

### Post by raja on 2007-06-02
> **FRGus723 said:**
> Hey Pilot

I have loaded the NTFS-3G drivers from the synaptic package manager but I am unsure what to do when you say "enable read/write"  can you explain for a linux noob how to do that?

Thanks

ntfs-config is the easy way to do it. Just do ```
sudo aptitude install ntfs-3g ntfs-config
```

Then ```
ntfs-config
```

---


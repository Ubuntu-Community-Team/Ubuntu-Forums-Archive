---
title: "Change destination of Home folder AFTER install"
date: 2007-10-30
forum: General Help
---

### Post by Ian505 on 2007-10-30
I was wondering if it was possible to change the directory of the home directory after installation. I have a XP/ubuntu Gutsy machine and only created a partition large enough for the Ubuntu OS and am running out of space to put downloaded files, etc. I would like to have everything saved into the directory X:\My Documents which is literally where I have my My Documents folder pointing to in Windows XP. So I would like to change my home folder so the destination is X:\My Documents. I would also like my music & video folders pointed to X:\My Documents\My Music and X:\My Documents\My Videos appropriately.

Thanks, any and all posts are appreciated.

-Ian

---

### Post by taurus on 2007-10-30
You cannot use ntfs filesystem as your $HOME because you will run into all kind of problems with permissions.  

Therefore, you need to create another ext3 for /home if you wish and keep that ntfs partition to share your data between windows and Ubuntu.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by perixx on 2007-12-14
What you could do as well is using Puppy-Linux, with a 'frugal-install' on your XP's partition - 'with ntfs-3g' driver activated. 

This installation-method works with only 3 files; one of being the 'ext2'-user-filesystem-container', one the actual Linux-kernel and one the 'system-file-container'.

What might get a little complicated, is to use the nt-bootloader for chainloading Puppy's Grub-loader within it's /Puppy/boot folder, for you'd have to run the appropriate 'dd' command from your Live-CD after the installation - and I don't know if that even would work with a frugal installation (might be interesting to try). 

You could also create a small partition just for holding your Puppy's Grub, which is being chainloaded by the nt-bootloader. I wouldn't dare to install Grub into the MBR, though, for it's very likey to trash your nt-bootloader and rendering your XP inaccessible. You can recover this, but it's some work.

It's surely possible to have the 'pup-save.e2fs' placed in your Windows' folder and have Puppy linked to it. But although there's a tool for Windows to access 'ext2/3' filesystems, I'm not so sure if it can access filesystem-CONTAINERS, so you're able to access your Puppy's saved files unter XP.... you see, it's really not very practicable.

It's much better to just install the Windows-tool to access your ext3-partition directly! (with 'Explore2fs' or 'ext2ntfs'). Or you create a common vfat32 partition which you can access from both XP and Linux (perhaps the easiest and savest method).

perixx

---

### Post by vanadium on 2007-12-14
The most simple and safe solution is to keep your home in place, but have symbolic links to various directories on your ntfs volume. This way, all your user datas, downloads, etc. will transparantly end up on your ntfs partition, which you can easily reach from within your home directory.

---

### Post by perixx on 2007-12-16
@vanadium:

One needs to have the NTFS-partition auto-mounted by default then, wouldn't he? What would be the appropriate (and exact) entry into /etc/fstab for that purpose?

Btw. do you know if there's a switch to disable the Kernel's native NTFS-support of Linux?

perixx

---

### Post by vanadium on 2007-12-16
An Ubuntu unstall usually mounts an ntfs automatically through /etc/fstab. I would not know the proper options, but I am sure it is easily found on the web. The idea is: you just leave /home/$USER on the partition, but then create links to the user data on the ntfs partition. This way, the space used on the system disk remains limited, as most of the actiual user data are stored on the ntfs volume shared with Windows.

To disable ntfs support in the kernel, you probably would need to recompile it which is above my cup of tea.

---

### Post by perixx on 2007-12-16
Yes, that sound like a good solution for Ian505...
He maybe might also shrink his XP-partition and enlarge his Ubuntu-partition after that, with Gparted...

Do you happen to know if I can mount my /home folder to another partition's subfolder - like /hda2/xub32? If the answer is yes, how?

perixx

---

### Post by Ian505 on 2007-12-27
Okay... sorry for the long delay.

First of all... I got a Quad Core CPU and Asus P5N-E SLI MOBO for christmas... so I have been migrating everything to a external drive for the switch of Motherboards, as XP doesn't like that and wants a new key. I am just going to move everything to the Ubuntu partition and only use XP when I have to. Now I would like to view my ubuntu partition in XP. (I flipped)

Any ideas? 

Your guy's answer to my original question made me think that it would be more work than its worth... especially if it will mess with Ubuntu. Though I think that making the link would work perfectly, I would feel much better if I used ext3 in linux as it is native and I keep business info on my computer... and I really don't want to be using nonnative filesystem for important video files. (MM biz- small one don't ask lol)

So I would like Windows to be able to read and write ext3 now. Is there an easy solution?

-Ian

---

### Post by taurus on 2007-12-27
If you want to access your Ubuntu partition, ext3 filesystem, from XP, just use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by Ian505 on 2007-12-27
> **taurus said:**
> If you want to access your Ubuntu partition, ext3 filesystem, from XP, just use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

And there is nothing that I can do to screw this up? It would be pretty bad to mess up all the filesystems and render my data useless.

-Ian

---


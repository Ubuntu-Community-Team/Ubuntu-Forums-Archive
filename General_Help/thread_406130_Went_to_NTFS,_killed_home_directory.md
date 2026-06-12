---
title: "Went to NTFS, killed /home directory"
date: 2007-04-10
forum: General Help
---

### Post by 50words on 2007-04-10
I was having problems with [Windows Desktop Search not being able to index my shared /home partition]("http://ubuntuforums.org/showthread.php?t=402010"), which was formatted in EXT3. (Same thing has happened with online backup solutions like Carbonite, FYI.)

Anyway, so I backed up the contents, configured NTFS-3g in Ubuntu, and reformatted to NTFS in Windows. But when I restarted Ubuntu, of course, I got a filesystem error and a fullscreen terminal telling me to fix my filesystem before I start a Gnome session.

I'm not particularly adept with a Linux terminal just yet, so how do I go about getting my /home partition remounted properly? I've been looking around for links, but not finding what I need.

TIA

---

### Post by julian67 on 2007-04-10
> **50words said:**
> I was having problems with [Windows Desktop Search not being able to index my shared /home partition]("http://ubuntuforums.org/showthread.php?t=402010"), which was formatted in EXT3. (Same thing has happened with online backup solutions like Carbonite, FYI.)

Anyway, so I backed up the contents, configured NTFS-3g in Ubuntu, and reformatted to NTFS in Windows. But when I restarted Ubuntu, of course, I got a filesystem error and a fullscreen terminal telling me to fix my filesystem before I start a Gnome session.

I'm not particularly adept with a Linux terminal just yet, so how do I go about getting my /home partition remounted properly? I've been looking around for links, but not finding what I need.

TIA

You need to edit /etc/fstab as it is set for Ubuntu to mount a FAT partition, but you changed it to ntfs. When Ubuntu boots to the terminal log in and type  ```
sudo vim /etc/fstab
```

Try replacing  fat or vfat in fstab with something like this:

```
ntfs  defaults  0 0
```

You should read something about using vim before you start and make a printout or some notes of the basic commands. 

Btw you still won't be able to index your /home from within windows, you have got it kind of mixed up. You need to add a driver to windows, not to Ubuntu. Go to [http://www.fs-driver.org/]("http://www.fs-driver.org/") and get the EXT2 IFS driver and read the FAQ! Install the driver in windows and you will be able to read your ext2 or ext3 drives. What you are doing is not really a good idea because if you have any trouble unmounting the linux drives from within windows you may corrupt your linux filesystems. Probably you will be more successful running Beagle from within Linux and indexing your Windows partition, or ideally keep a seperate FAT32 partition for data you want to use in both OS. An external usb drive is useful for this.

---

### Post by cmost on 2007-04-10
Do what that other guy said, but use nano to edit the file instead of Vim.  Vim is ridiculously unintuitive and complex to use, especially for newbies.  Nano works the way you'd expect.

---

### Post by 50words on 2007-04-10
Thanks guys! I'll give this a shot.

As for indexing the /home partition, I did have FS-Driver, and WDS still wouldn't index that partition. I looked into the same issue fairly thoroughly with Carbonite online backup, and basically they just didn't support EXT, so their software couldn't "see" my partition. I think WDS must work the same way.

---

### Post by 50words on 2007-04-10
Nope, that didn't do it. I tried "ntfs" and "ntfs-3g" and the numbers that were there, "0 1," as well as "0 0."

I'm thinking it might just be easier to wait until Feisty comes out on the 19th and do a clean install. Except I kind of want to get this right so I can learn the proper procedure.

Plus, I'm not even sure Feisty will let me select an NTFS partition to use as my /home directory. Edgy wouldn't, if I recall correctly.

---

### Post by cmost on 2007-04-11
Personally, you're crazy to use a Microsoft, closed source file system (with tenuous compatibility with Linux as it is) for your home directory.  To me, this is just asking for a disaster.  There are high quality EXT2/3 drivers for Windows that will let you read and write any data stored on your Linux partitions.  Since EXT2/3 is an open file system, its Windows drivers are more reliable.  But, it's your funeral.  Do what you like.

---

### Post by 50words on 2007-04-11
I would much rather use EXT2/3, but Windows Desktop Search is essential to me for keeping track of my clients, communications, etc., and it will not index an EXT partition, even with FS Driver. Google Desktop will, but I don't like it as much as WDS.

So I'm stuck using NTFS, unfortunately.

---

### Post by cmost on 2007-04-12
> **50words said:**
> I would much rather use EXT2/3, but Windows Desktop Search is essential to me for keeping track of my clients, communications, etc., and it will not index an EXT partition, even with FS Driver. Google Desktop will, but I don't like it as much as WDS.

So I'm stuck using NTFS, unfortunately.

Interesting.  Out of curiosity, what's keeping you trapped on Windows?  Beagle / Tracker can handle your indexing and rapid file searching with ease.  Evolution is nearly a drop-in for Outlook (plus additional features) and works perfectly with Exchange.  OpenOffice can replace Microsoft Office for most people (unless you're using Rights Management or some other esoteric feature buried in MS Office.)  Office 2003 works well in WINE.  Is there another specific Windows application that's keeping you tied to Microsoft?  Can you use Windows in VMware / QEMU / VirtualDOS box / Xen / KVM to satisfy the one or two Windows apps you absolutely cannot live without?  If you are not comfortable making the leap to Linux and waving goodbye to Microsoft fear not.  I'm proud to say that I've been MS free for over four years now and haven't looked back.  Good luck.

---

### Post by 50words on 2007-04-13
The main thing keeping me trapped in Windows is the lack of good document scanning capabilities in Ubuntu. I run a paperless office, and Ubuntu, somewhat ironically, is poorly equipped (as far as I have found) to handle one-button scan to file document scanning.

Multiple monitor support also needs to get a lot better.

Also, while Evolution is a good alternative to Outlook, it doesn't include the ability to link forms (contacts, appointments, and tasks) to contacts. I am an attorney, and this is pretty important for keeping track of my files. Beagle/WDS are helpful, but not quite what I need at present.

I can cope if/when I can do document scanning in Ubuntu like I can in Windows, but until then I don't have much incentive.

The one remaining app I have will work good enough in VMware or potentially in Wine. But again, I need better document scanning support.

So basically, for me, it comes down to not having a good document scanning solution. gscan2PDF works okay, but still isn't as convenient as Windows, where I hit the button on my document scanner (Fujitsu S500), it scans, asks me if I need more pages, then OCRs when done, and asks me where I want to save the file. Going through an application interface is slow and inconvenient.

But dangit, I'd love to switch over all the way (which is why I am dual-booting at present).

---

### Post by jzimmerman on 2007-04-29
You might consider running Ubuntu as a guest OS in VMWare on your Windows host.

Then you can setup network between the two with the simple "share via samba" utility in Unbuntu.

Not an ideal solution, but at least you can use both OS's adequately and share files between them.  Windows Desktop Search should have no problem with a network share.

---


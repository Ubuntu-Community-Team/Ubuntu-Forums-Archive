---
title: "Accessing Linux In Windows?"
date: 2008-06-20
forum: General Help
---

### Post by condawg on 2008-06-20
Is there any way for me to run a program in my Linux partition from Windows?

The situation is this.. I'm downloading some stuff in Azureus on my Linux partition, but I'm gaming in my Windows partition and would like to have my downloads going as I did so.
So basically, is there any way to run my Azureus from Linux in Windows?

Or, to make things simpler, is there any way to do the downloads in Windows, but onto my Linux partition?
So, basically run a downloading program in Windows, but have it downloading to my Linux partition?

Thanks =]

---

### Post by Dies on 2008-06-20
Sure, you can access your linux filesystem using something like

[http://www.fs-driver.org/](http://www.fs-driver.org/)

OR

you can easily access your Windows filesystem from Ubuntu using ntfs-3g, matter of fact on a default install your Windows partition should already be mounted somewhere. 

However, I really don't recommend you do this. Giving an OS full access to the main partition of another OS just seems like a bad idea to me. My advice is to set up a shared partition, NTFS is fine, you can access this from linux with no hassles and in my experience it is safer to have linux reading and writing to/from your NTFS filesystems than it is to let Windows .... all over your linux filesystem.

If you decide to use an NTFS partition, you just make folders there for Azureus, one for the actual downloads and one to hold the torrent files. Then just point Azureus to them. A good idea is to stop all torrents and force recheck them whenever you switch OS. Also you may need to go into the torrent folder and delete the .imported from missing torrent files so that Azureus won't ignore them.


If you decide to use a separate partition you can use something like

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

to change the layout of your hard disk.

---

### Post by Pjotr123 on 2008-06-20
You don't want insecure Windows to touch your shiny clean Linux. For exchange of files I recommend using a simple USB memory stick. Don't forget to unmount it before disconnecting, *also in Windows!* (Linux needs the stop code).

This is easier and simpler than creating an exchange partition on the hard drive.

---

### Post by nunki on 2008-06-20
If you are dual booting then post the output of 
```

cat /etc/fstab

```

> 
Or, to make things simpler, is there any way to do the downloads in Windows, but onto my Linux partition?
So, basically run a downloading program in Windows, but have it downloading to my Linux partition?


Your windows partition is probably already mounted somewhere. You could log into windows to game and download, then boot up linux and access the windows partition and pull the downloaded files over.

---

### Post by Dies on 2008-06-20
> **Pjotr123 said:**
> You don't want insecure Windows to touch your shiny clean Linux. For exchange of files I recommend using a simple USB memory stick. Don't forget to unmount it before disconnecting, *also in Windows!* (Linux needs the stop code).

This is easier and simpler than creating an exchange partition on the hard drive.

Yes it is. 

But I wouldn't think gparted is all that hard to master. Also, running all my torrent traffic to/from a USB stick seems laughable not just for performance reasons but also space, unless of course you are talking about a large capacity USB harddrive.

---

### Post by bodhi.zazen on 2008-06-20
boot your linux partition with VMWare or KVM

---

### Post by condawg on 2008-06-21
> **bodhi.zazen said:**
> boot your linux partition with VMWare or KVM

That's a great solution ;)
Thank you.
I didn't think you could do that.

---


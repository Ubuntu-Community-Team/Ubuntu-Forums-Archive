---
title: "Help regarding customizating ubuntu live cd"
date: 2008-03-25
forum: General Help
---

### Post by nipun_jain on 2008-03-25
I am trying to customize ubuntu 7.10 live cd using this guide:

[http://www.cyberpunkcafe.com/page.php?31](http://www.cyberpunkcafe.com/page.php?31)

I mounted /casper/filesystem.squashfs from the ubuntu cd to /media/mnt and copied its content to /home/username/filesystem_dump

**Now i have a problem modifying the initrd.img**

[QUOTE=the guide]Modify the initrd.img!
mkdir /home/username/initrd_workdir
cp /home/(username)/filesystem_dump/initrd.img /home/(username)/initrd_workdir[/QUOTE]

but when i give this command

```
cp /home/(username)/filesystem_dump/initrd.img /home/(username)/initrd_workdir
```

it gives the error:

```
cp: cannot stat `filesystem_dump/initrd.img': No such file or directory

```

I managed to find a file initrd.img-2.6.22-14-generic.bak in /boot of filesystem_backup

So I coped it to initrd_workdir as initrd.img and gave the command

```
 gunzip < initrd.img |cpio -i --make-directories
```

Now to edit the hostname and username i need to edit the file initrd_workdir/scripts/casper but I dont seem to find this file anywhere. Where can i find it?


**So in short, I need to know where the initrd.img file is in the extracted squashfs from the gutsy cd and when i have gunzipped the initrd.img, where do i find the *casper* file that I need to edit the default settings?**

Thanks for the help.

---


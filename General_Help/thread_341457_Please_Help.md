---
title: "Please Help"
date: 2007-01-18
forum: General Help
---

### Post by Graham1 on 2007-01-18
Please Help!!! I think I've done something bad, something really bad :(.

I've just issued the command "mke2fs -L Data /dev/hda6" trying to label my data drive. Having restarted my laptop, I am now prompted with a flashing cursor (no XOSL bootloader). Doesn't look good, does it? :(.

My laptop setup is as follows:-

1. Fedora Core 6
2. Ubuntu 6.10
3. openSUSE 10.2
4. Data (shared drive for above)

Have I lost everything? My XOSL bootloader was installed on the Data drive.

PLEASE HELP!!!

](*,)

Edit: Btw, my Data drive was hda6.

---

### Post by Graham1 on 2007-01-18
Having just run GParted on my laptop it seems that my Data drive is now ext2 (rather than FAT32) with 182MB of data still intact. Does this mean I can convert back to FAT32 and it will work as normal?

:)

---

### Post by meng on 2007-01-18
> **Graham1 said:**
> Having just run GParted on my laptop it seems that my Data drive is now ext2 (rather than FAT32) with 182MB of data still intact. Does this mean I can convert back to FAT32 and it will work as normal?
:)
Sounds like you've been playing with fire, i.e. issuing commands that you don't really understand. I think you may be able to get back your data, at least some of it, but the vital thing right now is for you to do ABSOLUTELY NOTHING so that you don't screw things up worse than they already are.

What I know about the command mke2fs is that it makes an ext2 filesystem (hence the name). I don't know that issuing a mke2fs -L command is a harmless way to change the label volume, but I do know that experimenting with a "solution" is most likely to lose your data completely.

Frankly, if I were in your shoes I would be checking my backups to see how recent they are and then checking my bank account to see if I could afford a data recovery specialist. You may be able to get help on these forums, but if I had the knowledge to help you I would still be wary of advising you about a filesystem I couldn't actually see.

---

### Post by lamego on 2007-01-18
> 
Having just run GParted on my laptop it seems that my Data drive is now ext2 (rather than FAT32) with 182MB of data still intact. Does this mean I can convert back to FAT32 and it will work as normal?
How do you notice it is intact ? If you have reformatted to ext2 it is unlikely that you can access it unless you use some data recovery tools...

---

### Post by Graham1 on 2007-01-18
My problem is, I don't have any backups ](*,). I'm hoping my data is still intact as it is reporting 182MB on that drive. 

My backup plan (if possible), is to split hda6 in half, formatting the second partition to FAT32. Next, make my Ubuntu partition active and boot it that. Would doing this then allow me to see the ext2 partition and copy the content to my newlt created FAT32 partition?

:)

---

### Post by Graham1 on 2007-01-18
> **lamego said:**
> How do you notice it is intact ? If you have reformatted to ext2 it is unlikely that you can access it unless you use some data recovery tools...

I'm not sure I have formatted as all I wanted to do was label a drive (which I read from another post). The scary thing is, I can't remember what was on that partition. Btw, my data drive is 10GB.

:)

---

### Post by Graham1 on 2007-01-18
It doesn't look like GParted can convert from ext2 to FAT32 (not sure if it's even possible). Are there any Linux/Windows tools that can do this? That way I can tell whether my data is intact or not.

:)

---

### Post by tagra123 on 2007-01-18
An encouraging post

[http://blog.maxdunn.org/articles/2006/07/07/how-to-really-mess-up-a-hard-drive-then-fix-it](http://blog.maxdunn.org/articles/2006/07/07/how-to-really-mess-up-a-hard-drive-then-fix-it)

---

### Post by Graham1 on 2007-01-18
I think these are my next steps:-

1a. Convert ext2 to FAT32 (if possible)

Note: XOSL requires FAT32 to boot (hence flashing cursor). If XOSL is no longer in MBR, I can use a 98 bootdisk to re-install XOSL there. 

or

1b. Split hda6 in half, creating another FAT32 partition. Use 98 bootdisk and re-install XOSL and then point to existing distro's.

Once XOSL is up and running, I'm sure (hoping) that my other "OS" partitions are ok (grub running on each distro)

:)

---

### Post by Graham1 on 2007-01-18
> **tagra123 said:**
> An encouraging post

[http://blog.maxdunn.org/articles/2006/07/07/how-to-really-mess-up-a-hard-drive-then-fix-it](http://blog.maxdunn.org/articles/2006/07/07/how-to-really-mess-up-a-hard-drive-then-fix-it)

Thanks for the link. Next time I'll be a little more carefull :). It wouldn't be so bad if it was just the one distro but three and a data drive. Scary, especially for a Linux noob like me :oops:.

[-o<

---

### Post by Graham1 on 2007-01-19
Unfortunately, I wasn't able to save my data :-({|=. However, I did manage to get the other OS's booting \\:D/. My problem now is that FC6 and openSUSE can see my newly created FAT32 drive but Ubuntu see's it as blank :confused:. Any ideas?

:)

---

### Post by Johnsie on 2007-01-19
Can you use a live cd to mount and access the drive?

---

### Post by Graham1 on 2007-01-19
> **Johnsie said:**
> Can you use a live cd to mount and access the drive?

I don't have any live cd's to test with :(. I find it strange that the drive (hda6) hasn't changed, yet Unbuntu see's it as empty and the other's don't.

:)

Edit: Actually, isn't the Ubuntu cd live before installation. Hold on a sec...

---

### Post by Johnsie on 2007-01-19
Ubuntu is a bit funny about automatic mounting sometimes. There's a lot of requests on launchpad so hopefully they'll sort soemthing out.

---

### Post by Graham1 on 2007-01-19
> **Johnsie said:**
> Ubuntu is a bit funny about automatic mounting sometimes. There's a lot of requests on launchpad so hopefully they'll sort soemthing out.

So there's nothing I can do at the moment then?

:)

---


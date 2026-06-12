---
title: "File System"
date: 2008-04-29
forum: General Help
---

### Post by ubtBaba on 2008-04-29
Hello,

I am still new to the Linux world, Ubuntu 7.10 being my first and current distro.

My question is is regarding the two partitions in my laptop, one is the ext3 file system for ubuntu and the second is a ntfs partition I made for downloads.

I read that linux is not very reliable for writing to ntfs.
Is this true? 

Also, if I make this ntfs partition into a ext3 file system can I share it with samba to mac & windows or should I leave it as a ntfs?

Thanks

---

### Post by njparton on 2008-04-29
Change the NTFS partition to FAT if it's on the same computer.  That would be best for all round compatibility.

---

### Post by mahousaru on 2008-04-29
> **ubtBaba said:**
> Hello,

I am still new to the Linux world, Ubuntu 7.10 being my first and current distro.

My question is is regarding the two partitions in my laptop, one is the ext3 file system for ubuntu and the second is a ntfs partition I made for downloads.

I read that linux is not very reliable for writing to ntfs.
Is this true? 

Also, if I make this ntfs partition into a ext3 file system can I share it with samba to mac & windows or should I leave it as a ntfs?

Thanks

I've been using NTFS-3G with 7.10 since it came out reliably and on one of my machines it is quicker for me to boot into nix to copy since there is no overhead with the virus/spyware/motherinlaw scanners.  (Be warned because there are no NTFS repair tools so if it get corrupted you need some way to mount it in a Windows box to fix it).

If you are only accessing the partition directly with Linux (the others using Samba etc), then personally I would use a FS native to Linux such as ext3 since the network sharing protocol would make the FS transparent to the client.  <- Basically if you are not multibooting and only booting via Linux...

---


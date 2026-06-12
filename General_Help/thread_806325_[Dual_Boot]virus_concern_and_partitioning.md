---
title: "[Dual Boot]virus concern and partitioning"
date: 2008-05-24
forum: General Help
---

### Post by kakyoism on 2008-05-24
I'm ready to dual boot my winXP and ubuntu,
and regarding the partitioning, 
I wonder whether Windows virus can infect linux harddrive,
if it's not in NTFS or FAT. 

Basically the reason why I'm gonna switch to ubuntu
is to keep my linux workspace clean from any Windows virus.

If the shared data partition is in NTFS, would a virus on it cause
linux to suffer? Is there any Windows mechanism that allow me to 
write data on a linux harddrive format?

---

### Post by MythosLegend on 2008-05-24
> **kakyoism said:**
> 
I wonder whether Windows virus can infect linux harddrive,
if it's not in NTFS or FAT. 

You shouldn't have to worry. 

> **kakyoism said:**
> 
If the shared data partition is in NTFS, would a virus on it cause
linux to suffer? 

It's unlikely. (Unless linux system files are on that partition and the virus deletes it or something)

> **kakyoism said:**
> 
Is there any Windows mechanism that allow me to 
write data on a linux harddrive format?

I believe you are looking for ext2ifs

---

### Post by jellylogix on 2008-05-24
it depends on the virus and the filesystem type but i would not undermind the power of viruses these days. I'm not sure if it would be possible to reach a ext3 type filesystem, since windows can't even see it. So i think ur home free to do what you want on windows without having to worry, but I'm not guaruteeing anything.

---

### Post by kakyoism on 2008-05-24
thx guys!

Today my winXP was infected by w32 modsys!html,
the most horrible virus I've ever had so far.

It caused no system-level trouble, but wrote 
malicious html code into all my html-like files
including my svn version files, which messed up
my entire SVN repository !!!!!

That's why I'm asking, because if my linux data are
on the shared drive, they may still suffer from this, correct?
Does it mean that I should never share anything between both OS's?

---

### Post by MythosLegend on 2008-05-24
> **kakyoism said:**
> 
That's why I'm asking, because if my linux data are
on the shared drive, they may still suffer from this, correct?

Yeah. Depending on the type of virus. 

> **kakyoism said:**
> 
Does it mean that I should never share anything between both OS's?
It's your call. 

If you install ext2ifs, you still have to give the linux partition a drive letter. Once you give a drive letter to the linux partition, viruses can write to that drive. 

You can change the drive letter back to none. 
The ext2ifs icon is in the control panel.

---

### Post by |{urse on 2008-05-24
There are "currently" 0 windows viruses that can infect a linux system.
there was one a while ago
[http://www.linux.com/feed/23236](http://www.linux.com/feed/23236) <----- June 03, 2002 (8:00:00 AM) -  5 years, 11 months ago  
but it's no longer a threat, besides all it could do was display a message at a specific date.

---

### Post by |{urse on 2008-05-24
I would be more worried about downloading torrents and mp3s and other stuff on linux and moving it over to your windows partition which is far more susceptible. Install the linux antivirus scanner clamav if you need to absutively suretain.

---

### Post by strabes on 2008-05-25
Just use ext3 as your data partition's filesystem and then use the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) to read and write to it in windows. If your windows partition gets a virus your linux partitions will be safe - don't worry about it.

---


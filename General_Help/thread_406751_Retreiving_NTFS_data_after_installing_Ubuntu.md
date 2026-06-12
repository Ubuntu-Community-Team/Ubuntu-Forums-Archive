---
title: "Retreiving NTFS data after installing Ubuntu"
date: 2007-04-11
forum: General Help
---

### Post by ecuasteelo on 2007-04-11
Hello Ubuntu Community,

I was on my way to installing Ubuntu 6.10 Edgy. My system previously was Windows 2000 formatted NTFS on a 40GB HD. I deleted the Windows partition and created 13.97GB "/" partition, 22.58GB "/home" partition and a 730MB "Swap" partition and formatted them with ext3. I got to the point where I was choosing my Time Zone and unfortunately then realized that I needed a database file from my Windows OS. I canceled the Linux installation and have been trying some recovery tools and no luck. 

Is there anyway to recover this database file that was on my Windows partition and if so can you please recommend some good tools. Or should I just face the fact that it is not retrievable. Thank you in advance.

---

### Post by thelinuxguy on 2007-04-12
> **ecuasteelo said:**
> Is there anyway to recover this database file that was on my Windows partition and if so can you please recommend some good tools.

Try attaching the disk to another computer with Windows and PC Inspector File Recovery.
[http://www.snapfiles.com/get/pcinspector.html](http://www.snapfiles.com/get/pcinspector.html)

Do NOT write anything to the disk you are trying to recover from.

---

### Post by raul_ on 2007-04-12
> **ecuasteelo said:**
> I deleted the Windows partition and created 13.97GB "/" partition, 22.58GB "/home" partition and a 730MB "Swap" partition and **formatted **them with ext3.

That pretty much says it...

---

### Post by thelinuxguy on 2007-04-12
> **raul_ said:**
> That pretty much says it...

Although the chances are very slim but the file may still be recoverable after the repartitioning and formatting. What I meant was: Do not write anything (more than what you already have) to that disk.

---


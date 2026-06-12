---
title: "Write To NTFS"
date: 2007-08-30
forum: General Help
---

### Post by measekite on 2007-08-30
Some documentation states one should never write to an NTFS partition from Ubuntu.  Other documentation claim that now it is OK.

I would like to know what the current up to date thinkin is.  Would users who are currently reading and writing to an NTFS partition from Unbuntu please state their experiences.  Would you also state how you are setup to perform these things?

---

### Post by merlinus on 2007-08-30
I have not experienced any problems.  You would not, however, try to run a program that is on an NTFS partition with ubuntu.

Here is how to get write privileges:

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

### Post by Mogurijin on 2007-08-30
I haven't had any issues and I also run games off of them through WINE and I still don't have any issues. Also NTFS-config is great ;)

---

### Post by PmDematagoda on 2007-08-30
Even I don't have a problem with writing to the NTFS partition but I got a question, when you delete a file in NTFS where does that file go to?

---

### Post by Irihapeti on 2007-08-31
I've been using NTFS-3g for a few weeks now, without any major problems. I've got a FAT32 partition for shared files, and I've been wondering about reformatting to NTFS. That is, until I decide to leave Vista altogether.

When you delete files off a NTFS partition when you're using Ubuntu, they go into a hidden .Trash-<yourusername> folder, just as they do on any other partition. You can empty that as normal.

If you boot into Windows and find you have stuff in your Ubuntu .trash folder, you can just shift it to the Windows recycle bin and delete it from there.

Irihapeti

---

### Post by shriah on 2007-08-31
Is there anyway to write in NTFS partition without ntfs-config or ntfs3g? 
I use ntfs3g to mount my ntfs partion and I have some problem with it when the widows is not properly shutdown . Is there any solution to over come this problem ???

---

### Post by Mogurijin on 2007-08-31
> **shriah said:**
> Is there anyway to write in NTFS partition without ntfs-config or ntfs3g? 
I use ntfs3g to mount my ntfs partion and I have some problem with it when the widows is not properly shutdown . Is there any solution to over come this problem ???
The issue with Windows having a death grip on your drives when it doesn't shut down is annoying. The only solution I've found is to let Windows boot all the way and then shut down. Then I just avoid Windows unless I have to be in it for some reason. Mainly to print :P

---

### Post by dsdexterds on 2007-08-31
I done the NTFS-config approach and it worked fine except for two of my drives, I got an error about them being RAID, which is correct, yet I have a thrid drive which is also RAID I was wondering if anyone could maybe point me in the right direction

Thanks in advance

---

### Post by stchman on 2007-08-31
> **measekite said:**
> Some documentation states one should never write to an NTFS partition from Ubuntu.  Other documentation claim that now it is OK.

I would like to know what the current up to date thinkin is.  Would users who are currently reading and writing to an NTFS partition from Unbuntu please state their experiences.  Would you also state how you are setup to perform these things?

I use the ntfs-3g package to write to NTFS partitions with no problems.

---

### Post by measekite on 2007-08-31
> **shriah said:**
> Is there anyway to write in NTFS partition without ntfs-config or ntfs3g? 
I use ntfs3g to mount my ntfs partion and I have some problem with it when the widows is not properly shutdown . Is there any solution to over come this problem ???


What is the difference beteen nfgs-config and ntfs3g?

---

### Post by Irihapeti on 2007-08-31
measekite:

ntfs-3g is the actual driver, and ntfs-config is a gui front-end to help you set it up. You can configure ntfs-3g through the terminal if you prefer doing it that way.

Irihapeti

---


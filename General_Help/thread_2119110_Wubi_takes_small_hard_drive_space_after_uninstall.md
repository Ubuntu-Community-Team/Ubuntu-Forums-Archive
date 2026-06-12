---
title: "Wubi takes small hard drive space after uninstall"
date: 2013-02-23
forum: General Help
---

### Post by NegusK on 2013-02-23
Hello, i recently downloaded ubuntu using wubi and ubuntu was working fine, but then when installed flash and restarted, ubuntu didnt come up so i decided to reinstall it.

So when i uninstalled it i noticed it took about 2 GiB from my C drive, how can i recover that space ?


Thanks in advance.:)

---

### Post by WizardlyPenguin on 2013-02-23
If you still have Windows dual booted, go into disk management and find the drive and format it. That should work. :)

---

### Post by NegusK on 2013-02-23
> **WizardlyPenguin said:**
> If you still have Windows dual booted, go into disk management and find the drive and format it. That should work. :)

I dont =/

I tried EasyBCD but it didnt show me the drive

---

### Post by Impavidus on 2013-02-23
Wubi installs don't have a partition (=drive in windows parlance) of their own. They use a file, which they mount as a virtual partition. As far as windows is concerned there is no linux partition and there has never been one.

By saying it took 2GiB from your C drive, do you mean the C partition has shrunken by 2GiB or that the free space on the C partition has decreased by 2GiB? And where did you install your wubi installation? C or somewhere else?

---

### Post by NegusK on 2013-02-23
> **Impavidus said:**
> Wubi installs don't have a partition (=drive in windows parlance) of their own. They use a file, which they mount as a virtual partition. As far as windows is concerned there is no linux partition and there has never been one.

By saying it took 2GiB from your C drive, do you mean the C partition has shrunken by 2GiB or that the free space on the C partition has decreased by 2GiB? And where did you install your wubi installation? C or somewhere else?

The free space was decreased, and yes i installed it in C.

---

### Post by Impavidus on 2013-02-23
Then there are some files left. I've never used wubi myself, so I'm not completely sure you can just remove them. It should be possible if Ubuntu has been properly uninstalled, but I don't know how to check that.

---

### Post by NegusK on 2013-02-23
> **Impavidus said:**
> Then there are some files left. I've never used wubi myself, so I'm not completely sure you can just remove them. It should be possible if Ubuntu has been properly uninstalled, but I don't know how to check that.

I uninstalled it using the wizard, and i actualy dont know where the actual files are..

---

### Post by Frogs Hair on 2013-02-23
The Ubuntu folder would be in local disk C under computer but as I remember it should be removed when Ubuntu is removed.

A wubi installation does not change the size of the Windows overall volume it simply installs inside of it.

Make sure the folder has been removed and run disk defrag.

---

### Post by NegusK on 2013-02-23
> **Frogs Hair said:**
> The Ubuntu folder would be in local disk C under computer but as I remember it should be removed when Ubuntu is removed.

A wubi installation does not change the size of the Windows overall volume it simply installs inside of it.

Make sure the folder has been removed and run disk defrag.

I'm using a solid state drive, sorry i should've mentioned that aswell as not typing "hard drive" :-\"

---

### Post by Frogs Hair on 2013-02-23
None of my friends using Wubi have an SSD , so I am not familiar.

---

### Post by bcbc on 2013-02-23
If the \ubuntu folder has been removed (sounds like it), then you should look for a hidden \found.000 folder. If a file was corrupted (like the ISO) then it may have been recovered to these folders and not removed when you uninstalled. And from your original description it sounds like there was some corruption.

E.g. run CMD.EXE (select Run as Administrator) and then:

```
dir /a:h \found*
```

[IMG]http://4.bp.blogspot.com/-hIzACmuwWkw/UJl3ZJdF9PI/AAAAAAAAAEE/k7n4lQLdn2E/s640/mroot2.PNG[/IMG]

Look inside those for any files that add up to the 2Gib

---

### Post by NegusK on 2013-02-24
> **bcbc said:**
> If the \ubuntu folder has been removed (sounds like it), then you should look for a hidden \found.000 folder. If a file was corrupted (like the ISO) then it may have been recovered to these folders and not removed when you uninstalled. And from your original description it sounds like there was some corruption.

E.g. run CMD.EXE (select Run as Administrator) and then:

```
dir /a:h \found*
```[IMG]http://4.bp.blogspot.com/-hIzACmuwWkw/UJl3ZJdF9PI/AAAAAAAAAEE/k7n4lQLdn2E/s640/mroot2.PNG[/IMG]

Look inside those for any files that add up to the 2Gib

File not found =/
I actualy heard about this file and ran chkdsk to search for it, and couldnt find it.

---

### Post by bcbc on 2013-02-24
The only other files I can think of that would be leftover are in the %TEMP% directory - but that won't be anything close to 2GiB.

---


---
title: "remove files from /boot"
date: 2007-11-13
forum: General Help
---

### Post by talex1 on 2007-11-13
Hello 
I removing files from /boot directory. I have only  'Ubuntu-Server 7.10 "Gutsy Gibbon" - Release i386' CD. 
System is still operates. How can I restore files from /boot? 
Thanks for help

---

### Post by PmDematagoda on 2007-11-13
Could you please be a little more clearer? I'm sorry, but from what I am seeing, this is what I think is your problem, correct me if I'm wrong.

"You removed the files in /boot and want to restore them, and your system still works, you also have the Gutsy 7.10 Server Edition Live CD."

Was the above description right? If not, please correct me.

---

### Post by talex1 on 2007-11-13
exacly :). I dont have network connect to  this computer (testing server) and I dont have files wich was in /boot directory. I think that this file should by on CD but how can I get them?

---

### Post by PmDematagoda on 2007-11-13
You still may have the files in your trash bin, open the trash bin and if your files are there, simply restore them to their original place, and I advise you to not to boot Ubuntu until this problem is resolved as it most probably would stop your Ubuntu OS from booting up at all.

---

### Post by talex1 on 2007-11-13
unfortunatelly I remove this file from console (I dont have x-server), so I dont have the trash...

---

### Post by PmDematagoda on 2007-11-13
There is a Trash folder, navigate to the Trash folder in your Home directory. Since the Trash folder is hidden you need to use ".Trash" when moving to the folder, so the command would look like this:-

```
cd ~/.Trash
```

Then try and see if the files are there.

---

### Post by talex1 on 2007-11-13
I'm in console text mode! I dont have the trash.

---

### Post by PmDematagoda on 2007-11-13
You could try to get the /boot files from a Live CD, but it is rather risky and the kernel will have to match with the one represented by the /boot files of the Live CD with the one of your normal Ubuntu install.

---

### Post by meindian523 on 2007-11-13
if you give a ls -alF in your Home directory,you would find a .Trash,that's what PMD is talking about,got it?

ie

```
username@<hostname>:~:ls -alF .Trash
```

will give you .Trash with 700 permissions....

---

### Post by talex1 on 2007-11-13
It 's Ubuntu-Server 7.10 (SERVER!!!) I dont have gnom and  dont have the trash. Try ALT+CTR+F1, login  and remove any files...but nothing important ;)

I change the question - where on install CD is files from /boot directory?

---

### Post by PmDematagoda on 2007-11-13
I believe that there is a drive for the Live CD's root itself which is named File System when you are in a Live CD session, you can get the files from there.

---

### Post by bingoUV on 2007-11-13
You say the system is working fine. Does this include booting? Did you try rebooting after deleting those files? In case it works, the files may not really be important enough for you to want to restore them.

Using the live CD's boot files will most likely not work as they have hacks to be able to boot from CD, and behave like a normal system. Though it depends on which file you deleted.

Somebody can give you their installed ubuntu. Post the he ubuntu flavour and version you have installed. Also, the contents of your /boot by giving the output of the following
```

sudo find /boot

```

---

### Post by talex1 on 2007-11-13
System is working, but I know, when I reboot it does not up. I remove all files from /boot directory. in /boot is only /grub.

I know that there should be 
vlinuz.....
System.map....
initrd....
but i dont know from where I can get this file(I have only install CD).

Now is theoretical question because I get this file from other installation, but I dont believe that in this situation  one and only solution is reinstall (if you have only install CD).
vlinuz I can copy and rename from install CD, I think.
Who know how get others necessary to boot files from Ubuntu-Server 7.10 install cd???
Is it possible to take them out???

---

### Post by bingoUV on 2007-11-14
> **talex1 said:**
> System is working, but I know, when I reboot it does not up. I remove all files from /boot directory. in /boot is only /grub.

I know that there should be 
vlinuz.....
System.map....
initrd....
but i dont know from where I can get this file(I have only install CD).

Now is theoretical question because I get this file from other installation, but I dont believe that in this situation  one and only solution is reinstall (if you have only install CD).
vlinuz I can copy and rename from install CD, I think.
Who know how get others necessary to boot files from Ubuntu-Server 7.10 install cd???
Is it possible to take them out???

You can best reply to this question yourself as you have now restored the files. Do a diff on the files on install CD, and those on your hard disk e.g. 
```

diff file1 file2

```
will tell you if file1 and file2 are identical.

I believe vmlinuz should be identical, but grub , device.map will not be the same.

---


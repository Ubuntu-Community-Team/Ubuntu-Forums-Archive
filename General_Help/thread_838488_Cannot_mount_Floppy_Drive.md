---
title: "Cannot mount Floppy Drive"
date: 2008-06-23
forum: General Help
---

### Post by paddy1 on 2008-06-23
# /etc/fstab: static file system information.
I have tried mounting floppy through root with no results.
This is my etcfstab contents

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b75ccc85-3d97-4b44-a1dc-45fd3cb3d1d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=412e6646-cb69-448d-8749-98174d61b9b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any suggestions please?

---

### Post by avtolle on 2008-06-23
Not that this solves your problem, but the floppy on my system only mounts with a floppy disk in it.

---

### Post by paddy1 on 2008-06-23
Still will not mount with floppy in

---

### Post by ajgreeny on 2008-06-23
You don't say what command you are using but so it's difficult to know if you are doing it right.  Try adding the "Disk mounter" to your panel and using that.  If that won't work, I don't know what else to suggest.  Your fstab entry is exactly the same as mine and mine works with that, or manually, using ```
mount /media/floppy0
```

---

### Post by paddy1 on 2008-06-23
I used the command mount /media/floppy0, but when tryiong to save, it says that the Abi file I am trying to save is write protected. There is nothng in the file properties to suggest or change this

---

### Post by paddy1 on 2008-06-23
When I try to send file to floppy drive, it says "permission denied"

---

### Post by VMC on 2008-06-23
> **paddy1 said:**
> I used the command mount /media/floppy0, but when tryiong to save, it says that the Abi file I am trying to save is write protected. There is nothng in the file properties to suggest or change this

Is the floppy disk write protected?

---

### Post by paddy1 on 2008-06-23
No, the floppy is set for write. The file I saved to the desktop as a DOC file and when I try to save it to a flopy, it says the file is write protected and "permission denied". Could it possibly be an issue in permissions?

---

### Post by VMC on 2008-06-23
> **paddy1 said:**
> No, the floppy is set for write. The file I saved to the desktop as a DOC file and when I try to save it to a flopy, it says the file is write protected and "permission denied". Could it possibly be an issue in permissions?

What kind of file is it? System file. I would rather see you copy and paste into your home directory first. Type this

```
ls -l filename
```

Then you can use

```
chmod 777 filename
```

Make sure you do this from copied file

---

### Post by paddy1 on 2008-06-23
I am getting really upset with linux now. It is a simple bloody Abi word processing file that will not copy to User or the floppy, because it says it is "write protected".

Why is this so damn difficult? I drag the file to the floppy icon on the desktop, and I expect the file to be copied to the floppy. Why is this so hard to do? It says permission denied, plain and simple!

---

### Post by cariboo on 2008-06-23
In a terminal type the following:

```
sudo chmod -R 777 /media/floppy0
```

I gave up on floppies a long time ago as it seemed even straight out of the box there were a  lot of data errors and 95% of the preformated floppies needed to be formatted before you could use them, and then if you tried to readthe floppy in another it couldn't read the floppy.

Jim

---

### Post by paddy1 on 2008-06-23
Is this question to difficult for the gurus to answer?

---

### Post by paddy1 on 2008-06-23
:guitar:Finally solved the problem, but I think there may be a bug in xubuntu. You can only save to a floppy AFTER you save to User.
After initial installatio, you have to right click on the file and change the permissions to allow read/write, reboot the computer, and then right click on the file and say "send to' floppy. It seems a round about way to do it, as you can't save to desktop and drag to floppy, nor can you 'save as' and go through media/floppy0.

---

### Post by VMC on 2008-06-23
> **paddy1 said:**
> I am getting really upset with linux now. It is a simple bloody Abi word processing file that will not copy to User or the floppy, because it says it is "write protected".

Why is this so damn difficult? I drag the file to the floppy icon on the desktop, and I expect the file to be copied to the floppy. Why is this so hard to do? It says permission denied, plain and simple!

Who owns the file?

---


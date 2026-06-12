---
title: "Problems changing folder ownership"
date: 2017-07-13
forum: General Help
---

### Post by brequete on 2017-07-13
Hello guys, I'm experiencing some problem on changing the ownership of a folder. Right now I'm running dual boot with Windows 7 and Ubuntu 16.04. I have a 200GB partition where I share documents, pictures, music and video folders between one OS and the other, this partition gets automatically mounted on startup on /media/datos but the owner of all the folders inside the partitions is root, so I cant write new files o modify existing unless I open those files as root, so that's why I'm trying to change the owner of theese folders running this command on terminal emulator:

root@Laptop:/home/eliocabrera# chown eliocabrera -R /media/datos/Elio_Cabrera/Documents
root@Laptop:/home/eliocabrera# 

Once the this comand is "excecuted" I check the properties of the folder and the owner of the folder and also all the files inside of it remains as root.. I would aprecciate if someone can help me with this telling me what am I doing wrong and the correct way to do it. Thanks in advance for the help comunity.

PD: As you can see English is not my main language, so sorry if I misspelled something.

---

### Post by &amp;KyT$0P# on 2017-07-13
I don't think you can [FONT=Courier New]chown[/FONT] individual files/folders on a Windows format partition.

It might work to unmount the partition, then mount it using your file manager.

---

### Post by CatKiller on 2017-07-13
Windows filesystems don't understand Linux permissions and ownership.

The permissions that are applied to the partition are set at the time that the partition is mounted.

You can change the options that are used for mounting that partition by editing its entry in /etc/fstab.

---

### Post by brequete on 2017-07-15
> **CatKiller said:**
> Windows filesystems don't understand Linux permissions and ownership.

The permissions that are applied to the partition are set at the time that the partition is mounted.

You can change the options that are used for mounting that partition by editing its entry in /etc/fstab.

I finally made it! Thanks @CatKiller for your clarification, after a few google reasearch based on your comment I found the solution, it was as simple as adding  uid and gid in the mounting line on the fstab file. For me the problem is solved, I'll copy how the fstab line shoud be: 

UUID=84C8C3C2C8C3B12A       /media/datos     ntfs-3g uid=eliocabrera,gid=eliocabrera default 0 2

---


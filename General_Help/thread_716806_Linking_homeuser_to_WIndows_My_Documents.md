---
title: "Linking /home/user to WIndows My Documents"
date: 2008-03-06
forum: General Help
---

### Post by XMAG on 2008-03-06
Hi,

I've recently installed ubuntu on my brother's computer, but as he doesn't uses it that much I created a small 5GB Partition and decided to use symbolic links to everything on the NTFS partition.

I wanted to know if there's a way to link /home/user to My Documents on the windows drive, so when I open his home directory I'm actually seeing all of the files on My Documents. I'm currently doing this by manually creating links to all of the folders on My Documents but that's not exactly what I wanted since there are some files exactly in My Documents that are not showing (obviously I'm not creating symbolic links to every single file, only for the foders).

The only ways I could thing of doing this (though I don't know how to to them) is to link /home/user to My Documents (is that even possible?) or to find a way for ubuntu to automatically create symlinks to every file and folder on My Documents (the folder itself, obviously I don't need to create symlinks for evey file in evey directory inside it)

Any ideas on how to do this?

---

### Post by gerscht on 2008-03-06
try to move your home directory and create a link afterwards (you will have to do this from a different console probably)
```

sudo mv /home/USERNAME /home/USERNAME_old
sudo ln -s /home/USERNAME /media/NTFSpartition/Documents\ and\ Settings/USERNAME

```
Mind you that NTFS doesn't understand Linux permissions, so everything will be readable by every user.
All in all it's probably not such a good idea... :confused:

---

### Post by pointone on 2008-03-06
Simply create a symlink from My Documents to /home/user/documents, perhaps?

---

### Post by XMAG on 2008-03-07
> **pointone said:**
> Simply create a symlink from My Documents to /home/user/documents, perhaps?

Yeah I thoght of that, but then it wouldn't be really IN the home directory... I was wondering if there's a way to do it exactly as if they were the same... I'll try what gerscht proposed!

---

### Post by Oldsoldier2003 on 2008-03-07
> **XMAG said:**
> Yeah I thoght of that, but then it wouldn't be really IN the home directory... I was wondering if there's a way to do it exactly as if they were the same... I'll try what gerscht proposed!

i read something earlier that makes me think that putting your home directory in a ntfs partition will create login problems. It  may not in your case, but earlier today someone was wanting to put the entire home partition as ntfs and was told he would break his installation...

---

### Post by dcstar on 2008-03-07
> **Oldsoldier2003 said:**
> i read something earlier that makes me think that putting your home directory in a ntfs partition will create login problems. It may not in your case, but earlier today someone was wanting to put the entire home partition as ntfs and was told he would break his installation...

Exactly, the filesystem permissions required by Linux may not be available on NTFS, so you run a big risk of stuffing up your system.

Putting any Linux system file/directory on a non-Linux filesystem is fraught with danger, put user data on them but not the stuff Linux relies on to be on something it has to total control over.

---

### Post by prshah on 2008-03-07
Putting your home directory on an NTFS partition will cause all sorts of problems because of permissions issues. Note that many programs create a hidden ".xxxx" folder to store their settings. If permissions are not OK on these settings, some programs (Eg Azureus, Wine) will not work, even if all access is given to everybody because of group issues.

What you can do is this: Copy all the stuff from your windows My Documents folder to your linux /home/username folder. Then go back to Windows, install ext2/3 IFS drivers to allow you to read your linux partition, and then have your Windows My Documents point to the linux /home/username folder.

Note that you MUST have /home on a seperate partition, eg. your main linux partition has mount point "/" and you create another ext3 partition with mount point "/home".

You can use a linux live CD to perform the partition operations, with limited risk to the data. Since you don't need 5Gb for the linux partition, you can divide it into 3.5Gb for "/" and 1.5Gb for "/home".

When dealing with partitions, be careful or you WILL make your files/folders/data disappear.

Cheers,
PRShah

---

### Post by Feivel on 2008-03-07
> **XMAG said:**
> Hi,

I've recently installed ubuntu on my brother's computer, but as he doesn't uses it that much I created a small 5GB Partition and decided to use symbolic links to everything on the NTFS partition.

I wanted to know if there's a way to link /home/user to My Documents on the windows drive, so when I open his home directory I'm actually seeing all of the files on My Documents. I'm currently doing this by manually creating links to all of the folders on My Documents but that's not exactly what I wanted since there are some files exactly in My Documents that are not showing (obviously I'm not creating symbolic links to every single file, only for the foders).

The only ways I could thing of doing this (though I don't know how to to them) is to link /home/user to My Documents (is that even possible?) or to find a way for ubuntu to automatically create symlinks to every file and folder on My Documents (the folder itself, obviously I don't need to create symlinks for evey file in evey directory inside it)

Any ideas on how to do this?

If you can read NTFS (otherwise install the NTFS config tool) in Nautilus you should be able to right click and choose make link. Wouldn't that work :)

ETA - On second thought, that will just make a link you can put in the directory. That's not what you want to do. Next time, I'll get some sleep instead of posting :)

---


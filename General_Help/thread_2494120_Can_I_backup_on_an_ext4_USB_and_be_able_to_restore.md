---
title: "Can I backup on an ext4 USB and be able to restore if I lose main user for that USB?"
date: 2024-01-05
forum: General Help
---

### Post by norvel4 on 2024-01-05
If I use an ext4 USB and have backup files on it and lose like my user that I used to put stuff on that USB and own it so I can do that, can I still get all like my files? What about root owned files if I have any? What permissions failure might I incur using an ext4 USB to back up home directory? What permissions failure if I back up root directory? I know root stuff is read only to like my user on like my computer but what about on a USB? If it helps I am on a Lenovo Thinkpad T460 with Ubuntu 22.04.3 LTS and Ubuntu Pro and I have root permission stuff in like my home directory because I mess with sudo maybe or maybe not, maybe.

---

### Post by oldfred on 2024-01-05
You should not have / ownership & permissions in /home.
If you copy files to any Windows format like NTFS or FAT32 you lose all ownership & permissions. You actually can reset /home's as you always are owner & want /home's default permissions. But / ownership & permissions varies a lot.

I have these users and each may have ownership & various permissions.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ id [/COLOR]
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),132(lxd),133(sambashare)
[/FONT]
```

Depending on version of Ubuntu your /home has default permissions & you as owner.
Ubuntu Home directories were created with 755 permissions but will be dropped to 750 with 21.04 and later,  now to prevent new home directories from being readable by other users on the system. 

you can see your default settings here:
[FONT=monospace][COLOR=#000000]cat /etc/adduser.conf[/COLOR]
[/FONT]

---

### Post by HermanAB on 2024-01-06
Note that a decent backup system should run as root, to ensure that it will backup everything.

---

### Post by norvel4 on 2024-01-06
Just to be clear, I have a desktop Ubuntu. Also, I would be using rsync to back up. I just try to know if I lose like my main user on like my computer and have a backup with root owner/group files if I can at least read them. Feel free to ask if you want any more info. I would be using ext4 USBs. Do you know how I might check that access thing with one computer? All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by oldfred on 2024-01-06
I prefer to do a full install to any USB drive over 16GB. I have had installs in 16GB, with 8GB for data, but could not add much.

I then rsync /home to my external drives.

You can see ownership & permissions with ll (thats el,el). I also change in Kubuntu my browser to show ownership & permission.
From my m2-usb3 adapter external drive.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/media/fred/m2_data**[/COLOR][COLOR=#000000]$ ll [/COLOR]
total 228 
drwxrwxr-x  18 fred fred  4096 Oct  1 12:10  [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-x---+  4 root root  4096 Jan  6 13:22  [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
-rw-rw-r--   1 fred fred   617 Jan 18  2021  alias.txt 
-rw-rw-r--   1 fred fred  1643 Apr  9  2020  backup_excludes.lst 
-rw-rw-r--   1 fred fred  4858 Jun 28  2020  backup_z170.sh 
drwxrwxr-x   6 fred fred  4096 Jun 20  2023  [COLOR=#5454ff]**Calibre_Library**[/COLOR][COLOR=#000000]/[/COLOR]


[/FONT]
```

---

### Post by norvel4 on 2024-01-06
So I can see permissions but how would I access root owned files and folders if I can without like original owner or group of that original computer it is from if I can? Can I just get like a yes or no whether I can access root owned files without original owner and group of origin computer?

---

### Post by yancek on 2024-01-06
Access how?  You can access a lot of root owned files as a user if you mean just to view them or their contents.      If files are 'root owned' what difference does the original user make?   You should be able to access and modify files on an installed system from a Linux 'live' usb or dvd.

---

### Post by norvel4 on 2024-01-06
Like on a regular ext4 USB, not bootable, trying to know if I can access things on that ext4 USB owned by another user to use and write to with some root owned and grouped. What difference it may make is that on some parts of like my system it asks for an administrator password to access some root owned or grouped things. I was trying to find if like that applies on USBs. It seems like you are saying on a USB I can access even root owned and grouped things from basically any user. Anyway, looks like I can but do you know if I could do it on a live not installed yet system or a Windows reader? Thanks for that last reply. Anyway, trying to be able to restore from backup if I do not have old users. It seems you are saying I can. You are saying at least on an installed system I can read files from another user including those with root stuff, correct? Anyway, thanks and like done but not quite. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by jimmyrus on 2024-01-08
> **norvel4 said:**
> Like on a regular ext4 USB, not bootable, trying to know if I can access things on that ext4 USB owned by another user to use and write to with some root owned and grouped. What difference it may make is that on some parts of like my system it asks for an administrator password to access some root owned or grouped things. I was trying to find if like that applies on USBs. It seems like you are saying on a USB I can access even root owned and grouped things from basically any user. Anyway, looks like I can but do you know if I could do it on a live not installed yet system or a Windows reader? Thanks for that last reply. Anyway, trying to be able to restore from backup if I do not have old users. It seems you are saying I can. You are saying at least on an installed system I can read files from another user including those with root stuff, correct? Anyway, thanks and like done but not quite. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.
no it doesn't matter since the rebuilt system will have access to whatever you put on a usb if you mount it as such. Doesn't matter the fs on the usb at all. If you mount it as root, you have root access. 

And what's with the "thanks and done not quite maybe not maybe" garbage? none of your posts make much sense and you dont seem to have a good grasp on things. If you back up a windows system you don't need special users to read the mounted device do you? No. This is no different.

---

### Post by norvel4 on 2024-01-08
Thanks and sorry if I am annoying or do not make sense maybe or maybe not, maybe.

---

### Post by jimmyrus on 2024-01-08
> **norvel4 said:**
> Thanks and sorry if I am annoying or do not make sense maybe or maybe not, maybe.
nah, you ain't sorry and you don't make sense. Just saw you on stack exchange with the same garbage and you said you just dont care. Do you act like that in real life and expect people to help you? How's that work out?

---


---
title: "13,04 - Change Home directory to an ntfs paritition"
date: 2013-10-20
forum: General Help
---

### Post by linuxnewbie3 on 2013-10-20
Hi,

I use Ubuntu 13.04 and Windows 7 in Dualboot (I am a Ubuntu User since 3 Weeks and for the process of changing I want to keep Windows 7, when 14.04 LTS is released I want to change completely).

On the screen below you can see my existing parititions (sda1: Windows 7 Recovery, sda2: Windows 7 System Reserved, sda3: Windows7 Installation, sda4: extended, sda5: swap, sda6: Ubuntu Installation, sda7: Data).

Now my home folder is located on sda6. But I want to locate it on sda7 because I want Windows 7 and Ubuntu beeing able to use my personal data. Therefore I need to relocate my home directy.

On the internet I only found two solutions:

a) creating a new ext4 partition (which doesnt work, because I need to use the already existing sda7 ntfs partition)

b) Change the directorys with Ubuntu Tweak (with this programm I only could change the directory for pictures or videos, but not the whole home folder)

How can I change the home directory the way I want?

Thank you in advance

sincerely

linuxnewbie

[IMG]http://s14.directupload.net/images/131020/abjao8ob.png[/IMG]

---

### Post by Bucky Ball on 2013-10-20
An easy solution would be to copy the directories and their contents to / to sda7, once you know your data is safely there, delete the directories in your /home directory on / and create symlinks to the directories (copies of the originals) which now reside on sda7. To create a symlink:

[https://duckduckgo.com/?q=create+symlink+ubuntu](https://duckduckgo.com/?q=create+symlink+ubuntu)

Or, yes, you can move the /home directory to its own partition or another drive. 

Also, you have plenty of room to shrink sda7 and create an EXT4 partition in the free space created, but that is a 'non-solution' because Windows can't read/write to EXT* partitions anyway so forget that option. Cross it off as an option.

---

### Post by Impavidus on 2013-10-20
I think (not entirely sure, but almost) that there are some configuration files in your home directory that will create problems if they don't have Unix permissions – in other words, it won't work on an NTFS partition. It is safe to make symlinks in your home directory to directories like Documents etc. on your NTFS data partition and have them replace those directories in your home directory.

---

### Post by linuxnewbie3 on 2013-10-20
Thank you for you answers. :)

For most of the folders I createt Symlinks like you said. For Music, Documents, Videos and Pictures I changed the directory with Ubuntu Tweak because I want to be directed i nthe right folder if I click on the Picture-library button in my browser.

Now that works perfectly gread. What doesnt work is that when I search in my dash for music, pictures and so on my data is not found. How can I configurate the Dash to search on sda7?

---

### Post by Bucky Ball on 2013-10-20
Interesting question. Don't use Dash so don't know, though, sorry.

As Impavidus mentions, just don't copy the hidden directories to the NTFS from your /home directory in /. They are right, that won't work.

They are hidden anyway so start with '/.nameofdirectory' so you won't see them. Glad the symlinks worked though. That's a start. No doubt the Dash change is easy and straightforward ... once you know how to do it! ;)

---


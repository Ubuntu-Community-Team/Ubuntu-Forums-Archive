---
title: "Panic!!"
date: 2008-06-18
forum: General Help
---

### Post by enigma1 on 2008-06-18
Hi all.  

I have no idea if I am posting this in the right place, but I am desperate.  Here is my problem.    A friend has managed to royally screw up his Windows computer to the extent it will no longer boot.  Now, using a live CD of Hardy Heron, I can see the hard disk and files still on it.  The disk appears in 'Computer' as '160.0 GB Media'.    My question is this....how do I use 'terminal'  (or anything else, for that matter) to search this disk for particular files?   

I have tried:
find *.dbx
find *.pst
ubuntu@ubuntu:-$ cd /Desktop     (got me nowhere)
ubuntu@ubuntu:-$ cd /ubuntu/Desktop   (got me nowhere)
ubuntu@ubuntu:-$ ls   (this got me Desktop Documents Music Pictures etc)

Basically, I want a find command that will take me to the 160.0 Gb Disk and search all through it for certain filetypes.   

Can anyone guide me?

James

---

### Post by jonathan.gardner04 on 2008-06-18
You could try

locate *.filetype

---

### Post by sdennie on 2008-06-18
First: "Don't Panic".

If you aren't familiar with the command line but, want to find files, it's probably easiest to go Places menu and select 160GB Media and click on the find button (it should be on the far right of the toolbar).

---

### Post by avtolle on 2008-06-18
My suggestion. From the terminal under the Live CD```
sudo fdisk -l
``` to find the partitions on the hdd. Then, a mount point will need to be created[cd mkdir /media[/code] using media as an example. Now, the hdd partitions will need to be mounted; and that's where I'm blanking (the correct command to be entered at the terminal). Once mounted, the contents of the file can be looked at, and, I believe, copied to external media using the```
cp /path/to/file/filename /path/to/external/drive/filename
``` command. I'll try to find the way to do the mount command, but it may take a bit, and hopefully, someone else will respond.

---

### Post by logos34 on 2008-06-18
> **enigma1 said:**
> The disk appears in 'Computer' as '160.0 GB Media'.    My question is this....how do I use 'terminal'  (or anything else, for that matter) to search this disk for particular files?   

I have tried:
find *.dbx
find *.pst
ubuntu@ubuntu:-$ cd /Desktop     (got me nowhere)
ubuntu@ubuntu:-$ cd /ubuntu/Desktop   (got me nowhere)
ubuntu@ubuntu:-$ ls   (this got me Desktop Documents Music Pictures etc)


no, you need to mount it first.  Double-click on volume in the side pane...it should mount at default '/media/disk'.

Then,

ubuntu@ubuntu:-$ cd /media/disk

(now you're in C: )

What exactly are you looking for? What did he do to screw up windows?

---

### Post by avtolle on 2008-06-18
[http://ubuntuforums.org/showthread.php?t=819337&highlight=Live+CD+copy+files+HDD](http://ubuntuforums.org/showthread.php?t=819337&highlight=Live+CD+copy+files+HDD) see post 5 for a way to use Nautlius for this, likely much easier.

---

### Post by enigma1 on 2008-06-18
Guys........thanks to you all for the speedy replies.

I'll try going through what happened when I followed the suggestions.

first,   'locate'  ................  finished almost as soon as I finished typing, with no results   (I suspect this is because 'locate' needs to build and store a database, and that can't be done just using a live CD - no writeable medium to store the DB on?)


second, the 'Places' bit shows the disk  as 160.0GB Media, and it apparently IS mounted, and 'file browser' allows me to see lots of files and folders, etc.  When I use the search option on the file browser toolbar, there is lots of thrashing of the HD, but in the end, no results.  Just to see if I was doing it right, I used the search option to look for picture files (there are lots of picture files on the HD, guy is a photography nut  :)   )   by searching for *.jpg, *.tif.  I got no results at all.  So if the search bar in file browser returns no results for files that I KNOW are there, then it tells me there are no results for *.dbx or *.pst, I am inclined to be a bit sceptical about the results  :)

third,  sudo fdisk -l  gives me this:

/dev/sda1   (followed by start and end blocks, and the file system (NTFS)  )

but I still can't figure out how to search   :)



fourth,  I just found out that what I have been referring to as the 'file browser' actually IS Nautilus.   Something new, learned  :)

---

### Post by enigma1 on 2008-06-18
me again, guys  :)

I missed one.....someone asked how he managed to screw up his windows. That one is easy......he breathed in close proximity to it   :)

---

### Post by avtolle on 2008-06-18
I've a feeling that the reason you are getting no results has to do with permissions on the files. In the post linked in my later post, there are links to discussions of how one changes permissions, etc. 

BTW, when you have the files up in 'Places", right click on a file or folder, select properties, then click on the Permissions tab and see what you get. Let us know what it is, so we may have a suggestion or two to help.

---

### Post by sdennie on 2008-06-18
Try:

```

find /media -iname "*.jpg"

```

---

### Post by enigma1 on 2008-06-18
guys!!.......brilliant!!

the find -iname command worked a treat and I have now recovered all the .pst, .dbx, and .jpg files.   Thank you ALL so much for your patience and help.  A little side effect of this exercise has been me learning a little more into the bargain  :)

thanks again!!

James

---


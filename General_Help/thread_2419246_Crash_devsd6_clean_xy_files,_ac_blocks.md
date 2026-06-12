---
title: "Crash /dev/sd6 clean x/y files, a/c blocks"
date: 2019-05-18
forum: General Help
---

### Post by ragnaro7 on 2019-05-18
Hi Im new in ubuntu and im having problems, mi pc crash and shows this.
At the start was only when I update with de interface option, but when I update in terminal it works fine.
But now happens when im using it normally. I re-install ubuntu and still having the same problem.
Sometimes before /dev/sda6... it says "recovering journal"

Im using: Ubuntu 18.04.2 LTS
RAM: 8GB
Intel® Core&#8482; i5-2400 CPU @ 3.10GHz × 4 
Graphics: Intel® Sandybridge Desktop
GNOME: 3.28.2
64 bits

[https://i.imgur.com/bZGDbKB.jpg](https://i.imgur.com/bZGDbKB.jpg)

---

### Post by Bashing-om on 2019-05-18
ragnaro7; Hello - Welcome to the forum.

As you advise of "  it says "recovering journal"" on a fresh install I have to question the integrity of the .ISO file:
Did you verify the download ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How did you make up the install medium ( USB ? ) ?
Did you check too this medium ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

And we can not as of yet rule out hardware issues - is the drive failing ? If the above checks good, then next is to check the file system with 'fsck'.

[INDENT][INDENT]there has to be a reason
[/INDENT][/INDENT]

---

### Post by ragnaro7 on 2019-05-18
Hi, I didnt verify the .iso, i think im gonna download again and check it

I use an USB

I use the fsck in terminal and this shows:

fsck de util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda6 está montado. (is mounted)

"attention the file system is mounted, if it continues to cause damage to the filesystem"
Do you wanna continue (y/n)


> **Bashing-om said:**
> ragnaro7; Hello - Welcome to the forum.

As you advise of "  it says "recovering journal"" on a fresh install I have to question the integrity of the .ISO file:
Did you verify the download ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How did you make up the install medium ( USB ? ) ?
Did you check too this medium ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

And we can not as of yet rule out hardware issues - is the drive failing ? If the above checks good, then next is to check the file system with 'fsck'.
[INDENT][INDENT]there has to be a reason
[/INDENT]
[/INDENT]


---

### Post by DuckHook on 2019-05-18
Welcome to the forums, ragnaro7

Please do not post large images on the help forums. They are problematic for people who view on small screens or who have limited bandwidth. Instead, you can attach such images as files using the paperclip icon in the toolbar.

---

### Post by Bashing-om on 2019-05-18
ragnaro7; Welp -

> 
"attention the file system is mounted, if it continues to cause damage to the filesystem"
Do you wanna continue (y/n)


One cannot run a file system check on a running system - hence that warning !

Run that file system check from your booted live(USB).

[INDENT]there is a procedure :)
[/INDENT]

---


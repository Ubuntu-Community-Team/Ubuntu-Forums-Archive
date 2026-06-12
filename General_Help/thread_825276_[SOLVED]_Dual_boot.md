---
title: "[SOLVED] Dual boot"
date: 2008-06-10
forum: General Help
---

### Post by Dale Sexton on 2008-06-10
I'm new to Linux, but not computers. I have Ubuntu installed on a hard drive with Firefox and Thunderbird working (I'm so happy). My D drive is my old windows 98 drive. I need to access it on occasion to migrate information. Is there a way to dual boot from either the C or D drive? I can access the D drive with Ubuntu but some things need win98 booted.

Dale Sexton

---

### Post by chex_m8 on 2008-06-11
If win98 was on your computer whe you installed ubuntu it should have set up the dual boot automatically.

---

### Post by housam on 2008-06-11
Type in the terminal ( applications >> accessories >> terminal )the following code and post the results :
```
sudo fdisk -l
```
where -l is the lower case of L

---

### Post by Xiong Chiamiov on 2008-06-11
The misconception that drives are tied to a certain letter is one of the things that Microsoft has done that bugs me quite a bit.  Try changing the boot order in your BIOS, and watch them switch places!

Linux does just fine with mounting both ntfs and fat partitions (the latter of which I'm guessing you have).

---

### Post by Dale Sexton on 2008-06-11
> **housam said:**
> Type in the terminal ( applications >> accessories >> terminal )the following code and post the results :
```
sudo fdisk -l
```
where -l is the lower case of L

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3bd45c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2353    18900441   83  Linux
/dev/sda2            2354        2434      650632+   5  Extended
/dev/sda5            2354        2434      650601   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
240 heads, 63 sectors/track, 7943 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x19b119b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2700    20411968+   c  W95 FAT32 (LBA)
/dev/sdb2            2701        7941    39621960    f  W95 Ext'd (LBA)
/dev/sdb5            2701        5321    19814728+   b  W95 FAT32
/dev/sdb6            5322        7941    19807168+   b  W95 FAT32

---

### Post by Dale Sexton on 2008-06-11
> **chex_m8 said:**
> If win98 was on your computer whe you installed ubuntu it should have set up the dual boot automatically.

No, I installed Ubuntu on the drive then put the old drive back in the machine.

Dale

---

### Post by Dale Sexton on 2008-06-11
> **Xiong Chiamiov said:**
> The misconception that drives are tied to a certain letter is one of the things that Microsoft has done that bugs me quite a bit.  Try changing the boot order in your BIOS, and watch them switch places!

Linux does just fine with mounting both ntfs and fat partitions (the latter of which I'm guessing you have).

Correct

Dale

---

### Post by Dale Sexton on 2008-06-15
Anybody?

Dale

---

### Post by meierfra. on 2008-06-15
Open the file menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change

"timeout 3" to "timeout 10"

Change

"hiddenmenu" to "#hiddenmenu"

Add this to the very end of the file

title  Windows 98
rootnoverify (hd0,0)
chainloader +1

save the file and reboot. You should get a menu at boot up, and choosing "Windows 98" should boot you into Windows 98.


If that  did not work, try this instead

title  Windows 98
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Dale Sexton on 2008-06-15
Thanks. That got me close. I get the windows splash screen, then the screen goes black. Not sure what to do next.

Dale

---

### Post by meierfra. on 2008-06-16
> I get the windows splash screen,then the screen goes black.

This is a Windows problem and no longer a Grub problem.  I don't really have any experience with fixing Windows 98.  But  if you have a Windows CD,  you might try "fixboot" and  "chkdsk /r" from the windows repair console.

---

### Post by Dale Sexton on 2008-06-16
> **meierfra. said:**
> This is a Windows problem and no longer a Grub problem.  I don't really have any experience with fixing Windows 98.  But  if you have a Windows CD,  you might try "fixboot" and  "chkdsk /r" from the windows repair console.

The hard drive boots on it's own. This will be one I have to tinker with. I'll try a google. If I make it work, I'll link to it for others to find.

Dale

---

### Post by meierfra. on 2008-06-16
> The hard drive boots on it's own

O.K.  So maybe than it is a grub problem after all?  Could be  something special about Windows 98, which I don't know about.

---

### Post by meierfra. on 2008-06-16
Which of the two choices gets you to the splash screen?

---

### Post by Dale Sexton on 2008-06-16
> **meierfra. said:**
> Which of the two choices gets you to the splash screen?

That would be the last one.

Dale

---

### Post by meierfra. on 2008-06-16
I did some googling and its seems that "map" does not work very well with "Windows 98" (although I didn't find anybody who had  exactly the same problems as you)


So there are a couple of things  you could try:

1)  Add Ubuntu to the Win98 boot loader. (I know how to do this for XP, but I'm  not sure  how it works for Win98

or


2)  Install Grub  to the Windows 98 drive.

Let me know if you would like to try one of these and I'll write up instruction.

---

### Post by meierfra. on 2008-06-16
Instruction to install grub to the MBR of the Windows drive.

Step 1)  Edit menu.lst:


```
gksudo gedit /boot/grub/menu.lst
```

change 

# groot=(hd0,0)

to

# groot=(hd1,0)


Use 

title Windows 98
rootnoverify (hd0,0)
chainloader +1

for the Windows item.

Save the file

Then in the terminal

```
sudo update-grub
```

Step 2 Install Grub to the MBR of the internal drive:

```
sudo grub
```

and at the grub prompt:

```

device (hd1) /dev/sda
device (hd0) /dev/sdb
root (hd1,0)
setup (hd0)
quit 
```


Edit:  I left out an important part:  For this to work, you need to change the boot order in  the bios: boot from the Windows 98 drive)

---

### Post by meierfra. on 2008-06-16
Edit:  This is different solution then the previous post. You only need  to do one of the solutions)


Instruction to add Ubuntu to the Windows 98 boot loader.

Step 1) Edit menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```


change "timeout 10" to "timeout 2"

change "#hiddenmenu" to "hiddenmenu"

change

# groot=(hd0,0)

to

# groot=(hd1,0)


Use

title Windows 98
rootnoverify (hd0,0)
chainloader +1

for the Windows item.

Save the file.

In the terminal
```

sudo update-grub
```


Step 2 Install Grub to the Ubuntu partition:

```
sudo grub
```

and at the grub prompt:



```
device (hd1) /dev/sda
device (hd0) /dev/sda   (This is not a misprint, It really needs to be /dev/sda)
root (hd1,0)
setup (hd0,0)
quit

```


Step 3 Create "ubuntu.bin"

```
sudo mkdir Win
sudo mount /dev/sdb1 Win
sudo dd if=/dev/sda1 of=Win/ubuntu.bin count=1
```

(be very careful with the "dd" command. Make sure you don't leave out the "count=1")

Step 4 edit "boot.ini"

```
sudo nano Win/boot.ini
```

add this to the end: (don't leave any blank lines)

c:\ubuntu.bin="Ubuntu"

Save the file.

 (If you prefer, you can edit "boot.ini" from Win 98 rather than Ubuntu.
Also, since  you said Win98 is the D: drive, you might try  d:\ubuntu.bin="Ubuntu" instead.)


Edit:  I left out an important part:  For this to work, you need to change the boot order in  the bios: boot from the Windows 98 drive)

---

### Post by Dale Sexton on 2008-06-17
How do I undo this? My computer is stuck (I'm on another one). I have a list of several Ubuntu entries to choose from, but I get:
Error 15: File not found
Press any key to continue...

I get no further. Not being able to get to the desktop I don't know how to undo it.

There are some commands to edit before booting and command line, but I have no clue what needs to be done here. I think what happened is I saw your first message and did it, but didn't get the next message. Just a guess.

Dale

---

### Post by meierfra. on 2008-06-17
Sorry, I forget to mention one important thing:

You need to change the boot order in the bios:  Boot from the Win98 drive.


> think what happened is I saw your first message and did it, but didn't get the next message.
No,  this is not the problem. My two posts are two different solutions. You should NOT do both.

---

### Post by Dale Sexton on 2008-06-17
So how can I get the computer to boot up again?

Oh! had to reread the message. I'll give it a try later today. Have to go back to work. I'll leave a message on how it works.

Dale

---

### Post by Dale Sexton on 2008-06-17
ok. Windows boots... Hang on

Ubuntu boots... Yeah! (fanfare)

I love you, man! (tears o joy)

You have gone above and beyond to help. As I need window I can use it and try to migrate what I can to Ubuntu. I can tell I already like it and have converted two of my computers. Converting more as I have time.! I have more knowledge of windows, but will be saving this thread for my Ubuntu knowledge base. Many many thanks!!

Dale

---

### Post by meierfra. on 2008-06-17
> Many many thanks!!

You are welcome. Glad to be of help. [How to mark as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---


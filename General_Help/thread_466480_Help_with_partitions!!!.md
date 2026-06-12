---
title: "Help with partitions!!!"
date: 2007-06-06
forum: General Help
---

### Post by Penguin246 on 2007-06-06
Ok... I reinstalled Windows/Ubuntu after a weird failure. For some dumb reason I made my Windows partion too small in the Ubuntu installer. I Want my HD to be divided in half, one half for Ubuntu and the other for XP. I really dont want to lose all my stuff AGAIN:( so can some tell me how to do this step by step.

---

### Post by mijj on 2007-06-06
it might be a good idea to have a third partition for data independent of any OS.

---

### Post by smoker on 2007-06-06
if you are talking about resizing your windows partition larger and having a smaller linux partition, i would recommend using the 'gparted live-cd' i have never had any problems using it, it can be had from here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

best of luck

---

### Post by Penguin246 on 2007-06-06
Scratch resizing windows I'll make a OS independent partition it sounds better. Okay!!! I know it has to be Fat32 or something but in GParted I can't do anything with any partitions they all have lock next to them:(. Do I have to open GParted with sudo? I want to shrink Ubuntu's partition if I add an OS independent partion. How would i do that and add the third partition. I want to leave Windoze alone if possible;).

EDIT: This is in response to mijj's post.

---

### Post by DeusEx on 2007-06-06
Or you try testdisk. 
It's in the universe repositories.
Interface is a bit harsh though!

---

### Post by merlinus on 2007-06-06
Download, burn and boot with the gparted live cd, as smoker suggested.  Using gparted either from your ubuntu install or the ubuntu live cd often does not work.

Also, you can format your data partition as ext3, and by installing the necesssary drivers -- ntfs-3g and ifs -- you will be able to read and write to it from both ubuntu and windows.

-merlin

---

### Post by mostholy on 2007-06-06
okay, merlinus, you have sparked my interest.  Can you elaborate on the necessary drivers to enable read and write from both worlds?  By elaborate I'm hoping for a step-by-step detail as I'm still trying to remember what I used to know about linux.  

thanks in advance....

---

### Post by merlinus on 2007-06-06
In ubuntu:

Applications/Add Remove

Show: all open source applications (from dropdown list at upper right).

ntfs-3g

This will enable you to read and write to/from ntfs partitions.

For fs:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Download and install from windows.  It has a gui setup, and will allow windows to read and write to/from ext2/ext3 partitions.

BTW, you will not need a driver to read/write from ubuntu to ext3.  But with ntfs-3g, you will be able to access your windows data.

Good luck!

-merlin.

---

### Post by Penguin246 on 2007-06-07
Everything works fine with the Gparted LiveCD UNTIL it tries to do my graphics. The screen goes black then goes back to the command line telling me it didn't work. After using Force-something (DAMN can't remember:()
it says something abount no screen????? 

I have a Intel 910/915 graphics chip and a 19' LCD gateway monitor and both work flawlessly.

BTW on force-whatever I chose th "chips" driver.

---

### Post by merlinus on 2007-06-07
force-vesa?

-merlin

---

### Post by mostholy on 2007-06-07
Merlin,  thanks for the response, seems to be quite straightforward to enable the ntfs write ability.  I think I'm more inclined to go all ext3 and finish cutting myself free of windows.

---

### Post by Penguin246 on 2007-06-09
Okay GParted LiveCD works with VESA graphics:).
I am wondering, can I install Windows programs on my EXT3 OS independent partition?
Or run exe's off of it???

---

### Post by Penguin246 on 2007-06-09
I neddto defrag right???

---

### Post by merlinus on 2007-06-09
Defrag thrice!  

And no, you cannot run windows programs nor .exe files in an ext3 partition.  Use NTFS for this.

You can run some windows programs with an emulator such as wine in ubuntu.

-merlin

---


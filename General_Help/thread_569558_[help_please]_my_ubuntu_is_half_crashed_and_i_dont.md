---
title: "[help please] my ubuntu is half crashed and i dont know wt to do ???"
date: 2007-10-07
forum: General Help
---

### Post by bAsem on 2007-10-07
first of all hello to every fellow ubuntu user ,, 


i have a serious problem and dont know how it happened . so i will tell u all what i did before that problem occured .

i have ubuntu fiesty 7.04 yesterday i decided i would install xp along with it on a different partition so i used gparted and resized one of my partitions but then i remembered something about xp after ubuntu and grub loader stuff and i should install ubutu after xp .. so after the partition i decided not to install xp 

and booted into my ubuntu ... to my shock now all i see is my desktop wallpaper 
and my mouse pointer (no menu bar no mounted drives ) and ubuntu cant read my other drives (i can only open firefox using my keyboard shortcut ..

i also tried alt+f2 but nothing happened 


sorry for the long speech but i just cant do it all over again :(

thank u so much for u r patience and hope i hear from u soon :)


cheers

---

### Post by p_quarles on 2007-10-07
What about alt-F1? That should open a terminal, and if you can do that, it sounds like this can be fixed.

---

### Post by bAsem on 2007-10-07
no alt+f1 either :(

thanks for ur fast reply

---

### Post by p_quarles on 2007-10-07
Hmm. What happens when you use the mouse to right-click on the desktop?

---

### Post by bAsem on 2007-10-07
it open the normal menu create folder create launcher .. etc etc :)

i really appreciate ur help man

---

### Post by p_quarles on 2007-10-07
Cool. You should be able to set up your panels and desktop icons however you want using that. Post back here if you need any further help.

---

### Post by DagMan on 2007-10-07
This is because, I think, of the way fstab now handles disks no longer by name.
There is a way to get the new id's for the new partitions but I don't know how and until someone else comes along the following should work.
well actually, can you post the output of 
**sudo fdisk -l**
you can type the command by hitting ctrl-alt-f2 then logging in and then ctrl-alt-f7 to get back here to the gui.  You can toggle back and forth using those key combos so take your time.
also if you know which partitons were mounted at which folder, we'll need that, for example, partition 1 is / partition 2 is swap then there was an extended partion created, then logical partion mounted at /home ...etc.  
This will be especially imporant if the fdisk output say something like 'partions are not in order' at the bottom of it
That and the output of sudo fdisk -l
also while you're at the command line, can you post the output of 
**cat /etc/fstab**

---

### Post by bAsem on 2007-10-07
the only option that works is create folder nothing else works

and all my drives are unmounted :( 

how can i create my panels that way

---

### Post by p_quarles on 2007-10-07
You can't create an application launcher? 

If you can, you'll need to create one with the following info:
name: terminal
command: gnome-terminal

---

### Post by DagMan on 2007-10-07
create the launcher to open xterm or gnome-terminal, then check if you still have all your partitions mounted
**df -h **
If not then use that terminal instead of having to toggle like I said above, just use the terminal instead and go from there.

---

### Post by bAsem on 2007-10-07
i couldnt toggle back using ctrl+alt+f7 so i took a pic 

the weird thing is that beryl is still working and when i hooked up my phone it orecognized it as mass storage mode

so wt is giong on :(

and i cant create a launcher :( i tried

thanks alot guyz

---

### Post by bAsem on 2007-10-07
the sda1 is the root for ubuntu and sda7 is the swap

sda5 sda6 and sda8 are the ntfs patititon (sda8 was the latest partition i created to install xp on) and sda8 is the only one that ubuntu reads ... but it requires a password to open it 

ps: i used automatix to download a patch to read/write ntfs maybe that is the cause of my problems ??

---

### Post by p_quarles on 2007-10-07
What were the results of this?
```
df -h
```

---


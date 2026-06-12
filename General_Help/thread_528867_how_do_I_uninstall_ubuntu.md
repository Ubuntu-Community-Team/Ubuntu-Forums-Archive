---
title: "how do I uninstall ubuntu ?"
date: 2007-08-18
forum: General Help
---

### Post by jusailakes on 2007-08-18
I was given a compaq desktop.I boot it up and Ubuntu appears and asks me for a username and password.Which I dont know.I cant get anywhere else but to the one screen.How do I uninstall it so I can use xp?

---

### Post by SPr on 2007-08-18
> **jusailakes said:**
> I was given a compaq desktop.I boot it up and Ubuntu appears and asks me for a username and password.Which I dont know.I cant get anywhere else but to the one screen.How do I uninstall it so I can use xp?

Put the Windows XP cd in and reboot. You should be able to reformat and reinstall Windows using the disc.

---

### Post by jusailakes on 2007-08-18
I tried that but it wont.It starts running.I mean you can hear it and see the light blinking but it doesnt go anywhere but to the Ubuntu logo.No matter what I do

---

### Post by SPr on 2007-08-18
> **jusailakes said:**
> I tried that but it wont.It starts running.I mean you can hear it and see the light blinking but it doesnt go anywhere but to the Ubuntu logo.No matter what I do

In that case the computer isn't set to boot from the cd drive. You'll have to change some BIOS settings.

If you know what motherboard is in the computer then you should be able to find a manual for it using Google. That's the best I can suggest, sorry.

---

### Post by _simon_ on 2007-08-18
When your pc POSTS it should tell you what key to press to enter BIOS.

Press it and then you need to find the boot order and make sure the CD/DVD Drive is FIRST.

---

### Post by DamjanDimitrioski on 2007-08-18
You want to uninstall Ubuntu which is Linux distribution.
Follow this steps:
                          - Take microsoft windows xp cd.
                          - Take a brick.
                          - Get a hammer.
Instructions: 
      - Take the hammer, smash the cd.
      - Then take the brick, and hit your head, until you will say Linux Rules, and microsoft down.

---

### Post by SPr on 2007-08-18
> **_simon_ said:**
> When your pc POSTS it should tell you what key to press to enter BIOS.

Press it and then you need to find the boot order and make sure the CD/DVD Drive is FIRST.

Why are the easiest solutions sometimes the last thing I think of :confused: I learn a lot by going the long way round though :)

---

### Post by Vince4Amy on 2007-08-18
Out of interest why do you want to remove Ubuntu & install XP?

---

### Post by zorglub76 on 2007-08-19
I'm a newbie in Linux world, but I have a tip for those who want to remove some Linux distro and not to screw up the whole Windows installation - just use some boot loader instead of the deleted GRUB, and your Windows installation will stay intact (I use Smart FDISK for these purposes).

---

### Post by joe.turion64x2 on 2007-08-19
Wouldn't you rather take control of the Ubuntu installation? All you need is the password, and it is damn easy to retrieve.

You only have to get a Linux LiveCD (the Ubuntu one will do). If you get the Ubuntu liveCD just boot from it, then open a terminal (Applications -> Accesories -> Terminal) and type
> sudo gedit /etc/shadow
to open the file /etc/shadow.
In that file you will find multiple lines, usually the last one will refer to the user of that system (look for fancy names for example, not system devices). Once you have found the line corresponding to the previous user notice that the second column (columns are separated by : characters) is a mix of unreadable characters, well, that is the encrypted password, delete those characters, save changes in the file, close it, and reboot your machine. Take out the Ubuntu CD and when you are greeted at Ubuntu's login screen type the user name you discovered in the mentioned file, and when prompted a password just hit Enter (there is no password). That way you would have recovered Ubuntu.

Joe.

---

### Post by jusailakes on 2007-08-19
Actually if I could get past the lack of username/password  issue then there wouldnt be a problem.But even if I had some sort of bootable disk to use,my problem would then be getting it to do simply that.When I try running a disk it trys(light starts blinking and can hear it but see nothing change).

---

### Post by joe.turion64x2 on 2007-08-19
> **jusailakes said:**
> Actually if I could get past the lack of username/password  issue then there wouldnt be a problem.But even if I had some sort of bootable disk to use,my problem would then be getting it to do simply that.When I try running a disk it trys(light starts blinking and can hear it but see nothing change).
Have you checked your BIOS settings? There should be a boot priority option. Or perhaps when you turn on your machine there is a instruction that passes by quickly to select the boot device. If you can get that very issue solved then using my method you could take possession of the Ubuntu system.

I suppose you have already tried to boot with other CD's, just to make sure you are not dealing with a damaged one.

Joe.

---


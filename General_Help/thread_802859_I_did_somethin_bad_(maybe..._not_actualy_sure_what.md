---
title: "I did somethin bad (maybe... not actualy sure what I did)"
date: 2008-05-21
forum: General Help
---

### Post by CraymelCage on 2008-05-21
Well my problem is that the desktop I use with ubuntu installed is, for lack of a better word, screwed. At least the hard drive is. It all started wih vlc (I think my computer is trying to send me a message) I was installing it from the repositories. It froze in the middle of the install and so I shut my computer off. when I turn it back on I continue installing it with the dkg -somethin or other command. After I install it I run a video and everythings fine. Then I go to the command terminal. Then I go to synaptic it asks for my password I type it. It reads that I put my password in wrong. I try again, nope nothing. I wasn't putting in the wrong password (trust me on that). So I open the command terminal. the command terminal is now two times wider then it should be and yellow. It took forever to load. I decide to restart. Nothing changes. I decide to reinstall Hardy heron. It reinstalls. I restart and it's loading. At the ubuntu loading bar screen before the login screen it "looks" like it froze then boots regardless. Instead of being greeted by a fancy log in screen I just get a black screen that reads:
```
Ubuntu login
user name:
```
I login regardless. Then I see what you see when you first open the comand terminal. I can type in commands like in the terminal too. I try to install other operating systems on my computer (all linux) they fail to install. Now all of them that used text install they show me this after scanning for my hard drive:
```
[CENTER][!] Detect disks[/CENTER]

No disk drive was detected. If you know the name of the driver needed by your disk drive, you can select it from he list.

     Driver needed for your disk drive:
                                   list
```
I'm at a loss. I need help soon because I'm dreaming about me, my computer and a golf club.

thanks in advanced.

---

### Post by drs305 on 2008-05-21
> **CraymelCage said:**
> I need help soon because I'm dreaming about me, my computer and a golf club.

DON'T DO IT! We've all been there. ](*,)

Someone will help you out. Give it some time.  The line above did give me a laugh, though...



By the way, the command you probably ran was 'dpkg --configure -a"  Does that ring a bell? (No answer required)

---

### Post by CraymelCage on 2008-05-21
Well I'm glad I could give you a chuckle. I'm on my dads laptop and every five seconds I hear "Don't screw up my computer." Soon my thoughts will move to me, a golf club and my dads face. Who ever can help me may save a life.

---

### Post by drs305 on 2008-05-21
While you are waiting for a reply, and at least this will get your post back to the top:

Do you have a LiveCD or alternate install disk?
Can you run LiveCD?
Do you have a separate partition for home?

These are just some really basic questions that someone who knows what they are doing might ask you.

---

### Post by Cap'n Skyler on 2008-05-21
so i assume this is a fresh install and you really have nothing to lose by re installing it right?
i have messed mine up so bad before none of the half dozen linux's would boot(dont ask).i finally went with a different linux and had the new one use the entire HD.then go back to my fave linux and do the same and get that one all patched and up and running and then i left it alone.LOL
  so if you cant boot i am not sure how to wipe the HD and try to re install.can you get a live 'buntu cd going?:popcorn:

---

### Post by CraymelCage on 2008-05-22
> **drs305 said:**
> While you are waiting for a reply, and at least this will get your post back to the top:

Do you have a LiveCD or alternate install disk?
Can you run LiveCD?
Do you have a separate partition for home?

These are just some really basic questions that someone who knows what they are doing might ask you.

I have the hardy heron live cd that comes with a text install. I also have the gutsy live cd ubuntu and kubuntu, a debian 4.00 install cd and a fedora 8 install cd. I have tried to install all. I can run the live cds fine. This morning I tried to run the hardy heron live cd and after a minute my screen goes blank.

Before this happend I set my partition with home and root as one and a seperate media partition to store thing for a reinstall and things like that. At the moment though with this messed up install I think it's just one big partition.

I haven't completely wiped my hard drive because my dban disk is at my moms. I want to try and see if that helps me though.

---

### Post by CraymelCage on 2008-05-22
Bump for the life of my annoying father.

---

### Post by jlacroix on 2008-05-22
This is a long shot, but try this. This method is assuming you are not given a user interface and just have a full screen black terminal.

(After logging in) Type:

sudo vim /etc/X11/xorg.conf

Press Insert on your keyboard

Scroll down and look for something like this:

PCI 0.02 (I just made it up, it's something like that)

In front of that line, type "#" to comment it out.

Press Escape.

Type exactly this without quotes: ":wq" (Enter).

You should be back at the terminal. Type:

sudo reboot

Does it work then? Or was that PCI line not in the file?

---

### Post by pixel :-) on 2008-05-22
do a memory test first,it's a boot option in grub,if your ram is broken you don't want to corrupt further your data.

---

### Post by Lord Xeb on 2008-05-22
Interesting... If it makes you feel any better, I was trying to put linux on an external drive, and in the process (since I did not know what I was doing) I put the linux ISO in the C:\ drive. O_____________________________O Lets just say that he wasn't very happen and took his company's IT guy 6 hours to fix it. >_>

---

### Post by CraymelCage on 2008-05-22
Thanks for all your replies. I actually fixed my problem before coming back and reading your posts. I was using at the live cd and I clicked on places and surprisingly enough it showed my root/home partition and my media partition. I opened up gparted and it actually showed me my partitions (I guess it was done hiding from me). I noticed that I made a mistake with the linux swap partition so I tried to delete all my partitions starting with the media partition. It freezes and I shut down my computer. When I restarted and booted the live cd my hard drive decided to play hide and seek again (jerk). I rebooted, my hard drive was visible, I immediately reinstalled rewriting every thing. My computer is functioning normally again.

---

### Post by Lord Xeb on 2008-05-22
O_o I have never experienced that problem. You should have reported via a bug report.

---


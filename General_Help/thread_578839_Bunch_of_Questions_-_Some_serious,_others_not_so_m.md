---
title: "Bunch of Questions - Some serious, others not so much"
date: 2007-10-17
forum: General Help
---

### Post by nickdr on 2007-10-17
I installed and am running Ubuntu 7.10 Gutsy Gibbon RC 64 bit. I did took the complete plunge, after playing with various Ubuntu releases for the past 2 years I took the full plunge and got rid of Windows without much thought. 
So far so good, except for a few things:

1) This is probably the most serious problem, the "e" key on my keyboard just stops working sometimes. I think it is after starting a certain program, not sure though. Does anyone know what would cause this and how to stop it? Even a way to get it working without having to restart the computer. I tried unplugging the keyboard, but still doesnt work after plugging back in.
If this helps, I have a Saitek PC Gamer's Keyboard, it is USB.
Also I just found this out, I can't do "Shift" and "n" to create an uppercase n. Weird...

2) Azureus was working awesome, then after installing WInE (I think) it shut off, and now everytime I try to start it gets past the splash screen and shows main screen for a second and then closes. What gives?
Also is there a UTorrent for Ubuntu?

3) How do I get the num lock key to turn on automatically?

4) I installed gdesklets but every time I start it it loads the windows for it, then the window turns black and closes. How do I make it work? Is there any other widget programs?

5) I jumped from Windows when I saw banshee had iPod support. It turns out not all iPods are created equally. Any idea how/when I can sync my iPod Touch with Ubuntu and banshee?

6) In Windows I used the Task Scheduler extensively. What is the equivalent in Ubuntu? I used the task scheduler as an alarm clock. For instance every weekday morning at 5:20AM the Task Scheduler would start my windows media player playlist called "Rock 3" so that I could wake up to my favorite commercial free and crap free music. Can I do this in Ubuntu?

7) I have a Leadtek TV 2000/XP TV tuner card, it is PCI. Can I use this to watch TV in Ubuntu? How? What programs do I need?

8) How do I get the scroll wheel to work? In Windows I used to enjoy pushing and holding the center mouse button down, the scroll wheel, to scroll through pages quickly. How do I do this in Ubuntu. Mostly Firefox.

9) Where can I get some themes, icon themes, and mouse cursors? How do I install them?

10) What is the best Gnome CD/DVD burning program? Also what do I use to rip DVD? In Windows I was very familiar to DVD Shrink and DVD Decrypter.

11) I own Quake 4 and Doom 3, I know that both of these games are Linux compatible, how do I install them?

12) I will be re installing Windows on a smaller hard drive to play some games and for now stuff like iPod syncing. I know when I reinstall Windows it will not see Ubuntu, and just boot straight to Windows. How do I get a boot menu back so that I can choose between Windows and Ubuntu. I own Acronis OS Selector for Windows, but I am not sure if it will see Ubuntu or how to get it to see it. If this is important here is my hard drive info:
Both Drives are IDE
- Drive 1 (Master) 80   GB - Will contain Windows and Windows programs
- Drive 2 (Master) 250 GB - Contains Ubuntu
Currently the 80 GB hard drive has copies of my music, videos, etc.. I used it as a back up drive so all this info was not lost when formatting my hard drive for Ubuntu, I also didnt have to make a million backup DVDs.

I know that I have asked alot of questions, but even if you could just point me in the right direction on one of them I would be thankful. So far I love Ubuntu, and I think once the above issues are ironed out I will not miss Windows at all. Yes I need some games every now and then, mostly half life 2 episode 2 and team fortress 2 coming out later this month, but I have the feeling that this time I have made the move to Linux for good.

Once again thank you for any help that you can give.

PS - Please dumb down any help you can give me as much as you can. I am a noob.

---

### Post by nickdr on 2007-10-17
Couple more things:

1) this one is also important:
how do i get my printer to work?
it is a LExmark X83, uses USB.

also can I use networked printers? While on the topic of networking how do share folders on my computer so that other people on my network can access them. Everyone else has Windows.

2) How do I adjust the videos played inside of Firefox. They are always played at whatever size the firefox window is at. I want to be able to play them at their intended size.

Once again thanks!

---

### Post by montres on 2007-10-17
Regarding question No 9:
Goto [http://art.gnome.org/]("http://art.gnome.org/")
You will find a lot of themes and artwork.
Sorry, I don't feel competent enough to anser any of your other questions!

---

### Post by digitalhillbilly on 2007-10-17
Sry I can't help you with the "e" key problem but that did happen to me at one time. A self preservation mechanism keeps me from remembering too much about it - it drove me mad. I don't remember what the cause was or how I fixed it. Was likely something ridiculous

For dual booting with XP on a secondary drive, this is what I did:

1. disconnected my linux drive and made the drive I wanted to put XP on master. Connected it and Installed XP

2. disconnected the now XP drive and reconnected the linux drive and booted.

3. edited my menu.lst file by first opening it with:

```
sudo nano /boot/grub/menu.lst
```
[CENTER]or[/CENTER]
```
sudo gedit /boot/grub/menu.lst
```

whichever you prefer.

4. next, added entry for the xp drive and changed the length of time the grub selection screen was up:

look for "timeout" near the top of the file and change the number to the lenght of time you want in seconds. Mine is 20 seconds.
```
timeout          20
```

add and entry for XP:
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=78293a30-2f53-481e-a769-9f8f058651ec ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Windows XP Professional
map		(hd0)	(hd1)
map		(hd1)	(hd0)
rootnoverify	(hd0,0)
makeactive
chainloader	(hd1,0)+1

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=78293a30-2f53-481e-a769-9f8f058651ec ro single
initrd		/initrd.img-2.6.20-16-generic
```

A couple things to note about this. First, I don't think you need to alter any of the Ubuntu entries. Leave them as default. Second, I don't know if copying my XP entry verbatim will work for you since my linux drive is SATA and the XP drive is IDE PATA (IDE). I think it'll work for you though.

5. shut down, reset the XP drive to slave or or keep it master and put it on your secondary bus or whatever your set up is. Power up and when grub loads, choose XP with the arrow keys. 

Post here whether it works or not

dh


edit: just noted a difference. You want to have XP as the first drive in the chain, I have it as the second. I don't know if you need all the chain loader and map stuff if it's the first.

---

### Post by conehead77 on 2007-10-17
4) Azureus

Delete the *.log files in your ~/.azureus/logs/ folder.

Then start Azureus again.

---

### Post by nickdr on 2007-10-18
bump

---

### Post by forestpixie on 2007-10-18
> 3) How do I get the num lock key to turn on automatically?

numlockx worked for me
```

sudo apt-get install numlockx
```

then ```
numlockx on 
```
> 
5) I jumped from Windows when I saw banshee had iPod support. It turns out not all iPods are created equally. Any idea how/when I can sync my iPod Touch with Ubuntu and banshee

I don't actually possess an iPod but I'm sure that amarok has support

> 10) What is the best Gnome CD/DVD burning program?
I use k3b -which is a kde application - there are plenty of threads on this :)

---

### Post by sa_venkatesan on 2007-10-18
Hello, 


For Question 10) I use Places->CD/DVD Creator to burn CDs/DVDs and it does the job perfectly.  Simply insert a blank CD/DVD, go to CD/DVD Creator and copy/paste the files to be burnt in the CD/DVD Creator Folder.   Click Write to Disc. That's it.


To rip CD/DVDs, you can use the following command. 

$ sudo  umount /dev/cdrom
$ sudo readcd dev=/dev/cdrom f=/some/path/mydvd.iso

Hth,

with warm regards,
Venkat

---


---
title: "I heve qeustions about Linux Ubuntu"
date: 2008-06-04
forum: General Help
---

### Post by central419 on 2008-06-04
Hello community!

I'm new to Linux, and I have some questions about it.
Being new to this forum also, some if not all of my questions may already have been awnsered here. I did a search for the thing my main qeustion is about, and it awnsered it a bit. I'm however looking for a bit more personal help, help with the problem I'm personally having. If anyone would be willing to help me a bit personally, I'd be very appreciative!

My computer:
Asus M2V motherboard
AMD Athlon 64 3500+
4 gig DDR2
Nvidia GeForce 7900 GS
Realtek RTL8139 Family PCI Fast Ethernet NIC
2 x Acer AL2016W screens

I have tried together with a friend, to install Linux Ubuntu 7 on it, a while back. We installed it on a seperate HD, in dual boot. The problem, we just couldn't solve, was: we could not get the dual screen to work properly. Nvidia Drivers were the problem, But we just couldn't find out how to get the right ones and how to configure them. 
Ideally I'd like to have my desktop span across both monitors, but maximizing windows to only 1.

Probably because of the nvidia drivers not working/misconfiguration, I was also unable to enable desktop effects.
I read on this forum that the Nvivia 7900GS is actually a recommended video-card for ubuntu.

A second problem/question is:
I'm currently using Adobe Photoshop CS3 on my Windows XP. I need the program for my work, and although Adobe hasn't made a version specificly for Linux, I know of WINE, and Virtual machines that might be able to perform the task for me. My question really is, does anyone have experience with Photoshop CS3 on linux though WINE, or is it a better option to go with a Virtual Machine, which I might want to do anyway; I have a Windows Licence, so I better use it right? Is there VM software that will allow seamless transition? I'd consider non-free VM software if it works well.

A third question:
Currently I have ALL my data on NTFS harddrives.
I know Linux can read it, but can i continue using it? or do I have to change it?

A fourth question:
Is evolution compatible with Exchange server? Or should I perhaps be looking for something similar but different?

For mostly everything else Linux suits my needs. I'm a webdesigner / webdeveloper.

---

### Post by BlackSwordD2 on 2008-06-04
i can only answer your second question (if you can call it that) you could use unbuntus freeware version of photoshop called Gimp which should act the same and save files in the smae format. if that is not an option i know an easy way to use wine is just to reinstall the app. but with wine it can get a little hazy with some programes so i'd suggest using a VM like virtual box or dual boot windows and ubuntu

and thats all of my 2 cents i can offer

---

### Post by ibuclaw on 2008-06-04
Hi, although I cannot say anything about how you're next experience will be until you try it out.

But Ubuntu has matured since last year.

1) Monitor support has improved. I'm not on Dual Monitor atm, but I can see the function is there.

2) WINE has not yet reached Adobe CS3 compatibility status yet (It won't work).

Although the Google developers have made a terrific job at making CS2 compatible to a Platinum level (Highest ranking, Installs and Runs Flawlessly).

And as for Virtual Desktops, I doubt the suitability of them would meet your needs. As most are only capable of emulating a 800x600 screen.

So you if your willing to have a compromise and stick to working on Adobe CS2 with Linux. Then that may be your safe bet.

I cannot comment on the other two. As I don't use them personally.

But I hope that I've given some useful topics for you to consider.

Regards
Iain

---

### Post by Gannon8 on 2008-06-04
3) Yes, Ubuntu can read/write to an NTFS drive. Just do this in a terminal:
1. Create a mount point for the NTFS drive if one doesn't exist already. I'm going to use /windows/
```
sudo md /windows/
```
2. Mount the drive. My NTFS partition is on /dev/hda2 Yours may be different. Do you have it on a second hard drive or on a different partition on the first hard drive?
```
sudo mount -f ntfs /dev/hda2 /windows/
```
3. Open the /windows/ folder. Go to Places > My Computer > Filesystem > Windows
Now it should look like if you went to My Computer > C: on windows.

Did this help you?

---

### Post by central419 on 2008-06-04
Thank you for your awnser about CS3 compatibility. If CS2 is a sure deal, I'll think about that. It has pretty much all the features I want to use.

I have actually tried the Live DVD Ubuntu 8.04.
I like it a lot, except the problems / qeustions I had in first post. Especially my first qeustion.

Can anyone comment on the nvidia 7900GS in particular?
How do I get it fully working?

If I'm sure I'll be able to do it, I'll install Ubuntu for real.

---

### Post by central419 on 2008-06-04
I have 3 physical Hard drives.

1 is partitioned in 2.
 partition C holds Windows
 partition D holds redudent Data
2 is 1 partition
 holds work data
3 is 1 partition
 holds media data (music, video)

When I testdrive Ubuntu with the live DVD, all drives are mounted automaticly, and I can read them. I didn't try editing anything on it, because I though I just couldn't. I though NTFS was windows only, but Linux was able to read.
Is it truely safe / wise to keep the drives in NTFS?
If I were to change it, would I have trouble with them in windows?

---

### Post by central419 on 2008-06-04
..

---

### Post by ibuclaw on 2008-06-04
Oh, NTFS. Sorry I didn't know what you were talking about earlier. :)

Yes, NTFS partitions work rather seamlessly with Linux, you can **read and write** to them now (They've fixed that bug).

If you don't want a particular drive to auto-mount (ie, the primary Windows partition). Then all you simply do is open up the fstab file and comment out the line with the partition on and reboot. Simple!

NVIDIA drivers aren't loaded by default on the LiveCD. So you can't use them as such. But once you install Ubuntu and first login to your account, the Hardware Driver Manager should pickup the fact that you have the Card in your system and will immediately install the NVIDIA drivers for you after your confirmation. (I have the 8500GT, and it works effortlessly with compiz and my multimedia work.)

And yes, Photoshop CS2 works seamingless. It's third in the top ten Platinum software that work with WINE. [Read here.]("http://appdb.winehq.org/")

Regards
Iain

---

### Post by central419 on 2008-06-16
Thanks everyone for their reply.

I'm using Linux now!
I'm very happy with it. Very.

I got the Harddrives and graphics card to work very nicely.

A few more questions, if I may.

How do I get applications to launch right after login?
Can I install a second language spell checker?
I'm using Gnome, does this mean I cannot use any KDE developed software?
How do I install more fonts? And are fonts I used in Windows installable?
I installed teamspeak (client), but I can't find it in the programs menu. How do I get it to show up?

---

### Post by avtolle on 2008-06-16
You may use KDE apps with Gnome; to install more fonts, install ubuntu-restricted-extras from the repositories using Synaptic or Add/Remove programs. There is a way to install other Windows fonts, you can search the Forums for threads on how this is done.

---

### Post by Zorael on 2008-06-16
> **central419 said:**
> How do I get applications to launch right after login?
Can I install a second language spell checker?
I'm using Gnome, does this mean I cannot use any KDE developed software?
How do I install more fonts? And are fonts I used in Windows installable?
I installed teamspeak (client), but I can't find it in the programs menu. How do I get it to show up?

[list=1][*]You want to find Sessions somewhere up in your Gnome panel.
[*]Pass!
[*]Yes, you can use KDE software; installing any will pull the necessary dependencies from the repository. The KDE (Qt) apps' looks will be a bit inconsistent with your normal Gnome (GTK) apps, and may in some places look outright funky, but that's life for a dirty, dirty Gnomeling. :> The only drawbacks to running apps based on different window frameworks (Qt, GTK, etc) is that each have to have their own libraries in memory when apps that require them are running.
[*]As for the fonts, all truetype fonts work. There is likely some dirty Gnome GUI way of installing them; else you can just manually copy them into your **/usr/share/fonts/truetype/** directory. Preferably, put them into their own subdirectories there to make it neat. Then run '**sudo fc-cache -fv**' in a terminal.
[*]I don't see why it didn't show up if you installed the version available from the repos, but you can manually add an entry to it in your (dirty) Gnome panel. The program with which to do this is called **alacarte**, which you can launch from a normal run-box (Alt+F2) or a terminal, but intuition tells me that you can just right-click the panel and click Edit.[/list]

---


---
title: "Ubuntu 8.04 LTS (Hardy Heron) Alpha 1"
date: 2007-12-02
forum: General Help
---

### Post by SebK on 2007-12-02
Hi,
I was wondering if Ubuntu 8.04 LTS Alpha 1 will be in Wubi?
[http://cdimage.ubuntu.com/releases/hardy/alpha-1/](http://cdimage.ubuntu.com/releases/hardy/alpha-1/)
Thanks

---

### Post by ago on 2007-12-03
> **SebK said:**
> Hi,
I was wondering if Ubuntu 8.04 LTS Alpha 1 will be in Wubi?
[http://cdimage.ubuntu.com/releases/hardy/alpha-1/](http://cdimage.ubuntu.com/releases/hardy/alpha-1/)
Thanks

Not alpha-1 but yes, wubi will be in 8.04

---

### Post by doubleblack on 2007-12-06
I have a question regarding this, I have Wubi 7.10 installed with Ubuntu and with the recent release of 8.04 Alpha 1 I know you can run "update-manager -d" using the update-manager package from gutsy.

My question is, with Wubi 7.10 installed can I run "update-manager -d" and upgrade to Hardy Heron Alpha 1 successfully and not break any functionality?

Regards.

---

### Post by Planets on 2007-12-06
Doubleblack,

I installed 7.10 via Wubi and upgraded to 8.04 with no issues whatsoever.

---

### Post by ago on 2007-12-06
> **Planets said:**
> Doubleblack,

I installed 7.10 via Wubi and upgraded to 8.04 with no issues whatsoever.

Congrats you probably are the first person on earth to run wubi 8.04 you have even beaten me to it... :P

---

### Post by Planets on 2007-12-06
Hey, awesome! =P

---

### Post by flamelab on 2007-12-07
> **Planets said:**
> Doubleblack,

I installed 7.10 via Wubi and upgraded to 8.04 with no issues whatsoever.

Oh god you are good:) . Bravo .

How did you manage to do that ?
I guess that you may have experienced some problems since wubi 7.10 is alpha and Heron is alpha as well :confused:

---

### Post by Planets on 2007-12-07
Just type update-manager -d in the terminal. I back up my Ubuntu folder before every update just in case.

---

### Post by flamelab on 2007-12-08
> **Planets said:**
> Just type update-manager -d in the terminal. I back up my Ubuntu folder before every update just in case.

Thanks ! I am gonna try that ( it seems that it is so simple as always ).

What problems ( if there are any ) have you encountered ??[img]http://www.adslgr.com/forum/images/smilies/hmmm.gif[/img]

---

### Post by flamelab on 2007-12-09
For the record , I updated to Heron too !!!:lolflag:

No problems so far .

I had some problems with ro mounted disk issues , but I solved them .

I will inform you !

---

### Post by maestrobwh1 on 2007-12-10
Need a little help

I did an upgrade from feisty to hardy... as it was in a partition neighboring my gusty (my default OS) and it actually went "fairly" well.

Okay, so after the upgrade, compiz is broken... no biggie.  

Bigger issue, something is linking my desktop to the root of the drive so that even though the start menu works, the panel looks good, and my wallpaper is the same, all the folders from / are showing.  If I open home, the Desktop folder is intact with all of my shortcuts and files that were there.

The path to the desktop somehow defaulted to the root of the drive.  Help?

---

### Post by flamelab on 2007-12-11
&#932;he Compiz Fusion problem is based on dependencies and broken packages in the unstable Hardy .And drivers are behind that as well .
I only face the problem of ATI drivers , for example , that are not going to be installed . I really messed up xorg and xorg.conf after that .

It is still alpha , we'd better be patient and return to our gutsies .

---

### Post by Planets on 2007-12-11
Try updating today. My compiz was broken and the update fixed it. Make sure you have it checked in the Appearances tab. Also make sure you have the options you want in the compiz manager.

---

### Post by Joeb454 on 2007-12-11
I might upgrade to hardy :) Will back up /home first but other than that I've not really got much to lose except the time it takes to install

---

### Post by flamelab on 2007-12-11
> **Joeb454 said:**
> I might upgrade to hardy :) Will back up /home first but other than that I've not really got much to lose except the time it takes to install

I have got a 24 mbit dsl . It was finished in minutes (except the deb compiling ) . I then installed the latest kernel 2.6.23.9 and everything are ... :guitar:

---

### Post by maestrobwh1 on 2007-12-11
I was having a lot of issues actually, I was surprised to even have X start, although it was acting flakey and everything seemed to drag slowly, firefox scrolling was nuts.  I actually got compiz to start, my desktop was showing all the folders of the root partition, and there were really weird artifacts over the buttons and scroll bars.  
I re-imaged my drive, as I wasn't in the mood to do this all over again.  I worked really hard on working with gutsy from the beginning and I think I will take a break on this one... and wait until it is ready to roll out.

I do have one question... is it okay to skip a distro and upgrade (should I change my mind), or should I do an upgrade to gutsy first?  Doing the latter, I could use the "normal" upgrade route, update-manager -c.  

I used apt-get upgrade and apt-get dist-upgrade to pull off the feisty to hardy leap.  I think it is why it looked like crap.

---

### Post by flamelab on 2007-12-12
&#921; think it is just software and kernel upgrade ....

But ... how did you make the graphics card work ??Nvidia or ATI ?
That was my only problem , I abandoned Heron ...

---

### Post by maestrobwh1 on 2007-12-12
I had some tweaks for my old ATi card in my xorg.conf that I backed up before... so when I did an upgrade, I recopied my old xorg file back to /etc/X11 so perhaps that is why it worked... sort of.

I have an old ATi radeon 7200 with 64 MB... runs fine with compiz in Gutsy (and feisty with some extra eyecandy epos for that project).    

I think I  am going to run Heron in desktop mode from a CD when it comes out officially and see if Compiz works from that.  If it doesn't, I'll just stick with Gutsy for a while and leave the old Feisty partition as a backup.

I get annoyed with things that aren't backwards compatible.  Yeah, I guess the card is old but it still works and I don't see future distro's offering things for me now.   I guess if suspend and hibernate worked like a charm, I would consider trying harder.  Never worked on my desktop all the way back to Dapper and I am not confident it will work with hardy.

I am done tweaking for now:-)

---

### Post by Planets on 2007-12-14
> **maestrobwh1 said:**
> 
I do have one question... is it okay to skip a distro and upgrade (should I change my mind), or should I do an upgrade to gutsy first?  Doing the latter, I could use the "normal" upgrade route, update-manager -c.  

I used apt-get upgrade and apt-get dist-upgrade to pull off the feisty to hardy leap.  I think it is why it looked like crap.

I don't think it's possible to Gutsy.

---


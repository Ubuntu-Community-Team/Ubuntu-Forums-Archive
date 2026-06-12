---
title: "No video play back on a fresh Hardy"
date: 2008-06-07
forum: General Help
---

### Post by tarekeldeeb on 2008-06-07
Hello all,

I have an Acer 5050/5051 laptop with ATI 1200 (ATI Radeon Xpress Series). I used to have Gutsy .. it was perfect for me. When I upgraded to Hardy .. it was perfect as well.

For some reasons, I had to make a fresh installation, I got Hardy. But for my surprise, there is no Video playback at all. When a video file is opened (in totem/mplayer/vnc/xine) I only see the first frame, then a black screen. The sound is fine. When I pause the video, I sometimes see another frame.

The ATI driver I had cam from ENVY.
This is independent on the video format I am playing.
I have the Desktop effects set to Normal.
Earth3d/Google Earth suffer from black flickers as well.

Does anyone got through this problem before?
Is there any solution?

Thanks in advance,
Tarek

---

### Post by Pjotr123 on 2008-06-07
Try applying this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by pedro_orange on 2008-06-07
```
sudo apt-get install ubuntu-restricted-extras
```

Problem solved :)

---

### Post by geirha on 2008-06-07
It doesn't sound like you are missing plugins and the likes, it sounds like your xorg is lacking some configuration. They changed to rely more on dynamically detecting configuration in hardy: [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

That could be the reason why gutsy and gutsy->hardy worked, but not plain hardy. Did you try installing the ati driver from hardy's repositories before trying envy? Hardy's fglrx pacakge might add the proper configuration you need (just a guess).

Do you happen to have a copy of /etc/X11/xorg.conf from your previous system (for comparison with the new xorg.conf)?

---

### Post by tarekeldeeb on 2008-06-07
> **Pjotr123 said:**
> Try applying this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

All packages in this solution are already installed .. no advance!

> 
Code:

sudo apt-get install ubuntu-restricted-extras

Problem solved 
Did not solve the problem .. too :confused:

I will try to change the xorg configuration as stated by Geirha ..
wish me luck :)

Thanks to all who replied ..

I will update you soon with results -if any- :lolflag:

---

### Post by nixtux on 2008-06-07
I installed Hardy yesterday and had ungodly issues with it.  I ended up re-isntalling 7.10 and everything works flawless now.  

Video playback worked but it'd hang my box and I didn't have any IRQ/Interrupt conflicts.  Additionally I couldn't find any info in logs.

I also had issues with compiz zoom not unzooming (possibily a setting I over looked.)

Good luck.

> **tarekeldeeb said:**
> All packages in this solution are already installed .. no advance!


Did not solve the problem .. too :confused:

I will try to change the xorg configuration as stated by Geirha ..
wish me luck :)

Thanks to all who replied ..

I will update you soon with results -if any- :lolflag:

---

### Post by tarekeldeeb on 2008-06-07
OOOooohh !!

Switching desktop effects to 'none' fixed the video playback .. now perfect.

Is there a way to have both functioning; video playback and normal effects?

---

### Post by geirha on 2008-06-07
> **tarekeldeeb said:**
> OOOooohh !!

Switching desktop effects to 'none' fixed the video playback .. now perfect.

Is there a way to have both functioning; video playback and normal effects?

It did work after upgrading from gutsy, right? It should be possible. 

Try following the first method here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by tarekeldeeb on 2008-06-07
> **geirha said:**
> It did work after upgrading from gutsy, right? It should be possible. 

Try following the first method here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
Yes, it did work before ..
:confused:

I think what is stated at the link you provided, is done by ENVY .. The driver is working .. direct rendering is on.

The problem is with the video playback

---


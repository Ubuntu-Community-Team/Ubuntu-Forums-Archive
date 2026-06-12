---
title: "XFCE Windows black out in several apps(eg gThumb)"
date: 2014-12-04
forum: General Help
---

### Post by alan-gauld on 2014-12-04
Since upgrading to Lubuntu 14.04 LTS several of my applications have blacked  out windows.
I'm running XFCE and the windows I'm talking about are typically options windows such 
as the editing tools in gthumb. 

The Menu editor is another case in point. I've posted an example on Flickr at

[https://www.flickr.com/photos/alangauldphotos/15944650682/](https://www.flickr.com/photos/alangauldphotos/15944650682/)

These all worked fine in Ubuntu v12.

Any ideas how to fix it?

Alan G

---

### Post by carlwsnyder on 2014-12-04
Are you going to insist on using Xfce under Lubuntu, or are you willing to re-install with Xubuntu?  I suspect that your problem stems from themes which work well under OpenBox/LXDE for Lubuntu, but give problems for Xfce/Xfwm in Xubuntu desktop.  Either change themes and check to see if they work properly, re-install with the proper settings for Xfce, or switch back to LXDE.

If you report that you have changed back to the Lubuntu desktop and have the same problems, then that is a different problem, but mixing desktops will sometimes lead to these types of errors.

---

### Post by coldcritter64 on 2014-12-04
> Since upgrading to Lubuntu 14.04 LTS...You say upgrading; from what, an older Lubuntu version? If so which one ? 
And do you mean an in place upgrade with an update manager application (as compared to a fresh install of a newer version.) ?

  As far as I understand things Lubuntu uses LXDE as the desktop environment. But you say ... 
 > I'm running XFCE ...  Have you installed the XFCE DE (comes standard with Xubuntu) as well or is that a typo ?
> These all worked fine in Ubuntu v12.The stock Unity version or one of the above 2 variants ?

I am just trying to get a better handle on how this set up came about with so many desktop environments possibly being referred to. :?

Despite the slight confusion at this moment, some hardware details, particularly graphics hardware, provided may be of some help.
Running the following command in terminal will at least let us know what graphics card you are using.
```
lspci | grep VGA
```

 Regards, coldcritter64

---

### Post by alan-gauld on 2014-12-04
OK, A bit more background.
I was running the stock Ubuntu 10 LTS (not 12 as previously reported - sorry about that) but 
with XFCE desktop.
I upgraded via a magazine cover disk to 14.04 LTS and that turned out to be based on Lubuntu.
(they omitted to mention that in the magazine!)

I have no great need to stay on Lubuntu, it's just the hassle/time of doing a version switch 
that keeps me here.  

The lspci output is:
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]

I tried changing themes/styles in XFCE with no obvious change. I'll try switching desktops 
and report back...

Alan g.

---

### Post by alan-gauld on 2014-12-04
I've started Unity (trying to use Openbox froze the PC on bootup!). 
gThumb seems to work although the labels are now a dark text against 
a darker background. But at least they are readable. But a long way 
from how they used to look (and how they look on my Netbook 
running Mint17)

So is the fault with XFCE? Or at least a setting somewhere there?
If so what, I really want it working on XFCE - I really don't like Unity!

---

### Post by Rob Sayer on 2014-12-04
The problem is as stated in post #2.  You've created a mess for yourself by installing multiple DEs.  Running DEs with openbox isn't a noob project.  Especially Unity.  Frankly no one who knew how to config openbox would try it with unity.  I have had more than one DE installed but I will not do that anymore unless one is Qt based like KDE and the other is GTK based.

Just do a clean reinstall of xubuntu if that's what you like.  And don't bite off more than you can chew just yet.

---

### Post by alan-gauld on 2014-12-04
> **Rob Sayer said:**
> Running DEs with openbox isn't a noob project.  

:-)

I'm not exactly a noob, I've been using Unix since University in 1986 and started  
using Linux in 1993 (the original Slackware distro). I've been running Ubuntu as 
my main desktop since 2009. I've been a software engineer for 30+ years and 
most of the code has been on  of one variety of *nix other.

But the problem seems to be the Lubuntu distribution on the magazine CD that 
had 4 DEs installed. I'll go and find an original distro from the web site and face 
the fact that I'll be out of production for the next 3 days or so... :-(

Thanks everyone for the prompt responses.

Alan g.

---


---
title: "Problem with rendering of Desktop and Apps after updating to Lubuntu 21.10"
date: 2021-10-18
forum: General Help
---

### Post by jesuel on 2021-10-18
I have just updated my Lubuntu to the 21.10 (Impish Indri) version  and after that the desktop environment is sort of pixelated and laggy in  a way which makes it impossible to work with. Some aplications are also  displaying this problem, most notably the file manager and also  Mendeley Reference Manager, to a lesser extent. [This is how my file manager PCManFM-Qt looks like]("https://i.stack.imgur.com/ur4JP.jpg") (everything full of pixels and with a delayed response) and [this is what happens when I right-click the desktop]("https://i.stack.imgur.com/9OVyI.jpg") (the  menus are not rendered properly). The problem is also affecting some  lubuntu utilities like FeatherPad and KCalc, but Firefox and Thunderbird  work completely fine. I sent photos instead of screenshots because when  I press print screen, the screen renders correctly and the pixelated  anomalies don't show.
 
Before upgrading everything was normal, so it must be related to  something which changed versions in this update. My desktop environment  is lxqt and the window manager is openbox. I am not sure if this is  relevant, but I am using the Arc-Dark gtk2 theme and I have qt5ct  installed. Changing the theme doesn't solve the problem. I am using the  correct resolution for my monitor (1920x1080).

 
A friend of mine, who understands more about Linux than I do, said  that probably the problem is with openbox, whose version is  3.6.1-9+deb11u1. I tried to reinstall it using sudo apt --reinstall install openbox, but it didn't solve the problem. If not with openbox, the problem should be with lxqt, which I also tried to reinstall.

 [URL="https://lubuntu.me/impish-released/"]
Lubuntu has noted that one needs to copy some configuration file[/URL] for openbox after the upgrade. I also did this, but nothing changed.

 
Does someone know what to do?

---

### Post by guiverc on 2021-10-18
This question was also asked at [https://askubuntu.com/questions/1370059/problem-with-rendering-of-desktop-and-apps-after-updating-to-lubuntu-21-10](https://askubuntu.com/questions/1370059/problem-with-rendering-of-desktop-and-apps-after-updating-to-lubuntu-21-10)

If you believe it's `openbox` (I don't) you can use a replacement WM as per my comments on that thread. As stated there, I believe it's an issue with the kernel & your hardware's GPU (*you stated you don't believe your system has a GPU, but it's the onboard/inbuit (motherboard) GPU chipset that others & myself refer to*)

I don't have any useful experience with `qt5ct` - but I also don't believe it's involved.

---

### Post by guiverc on 2021-10-19
.. continuing from what I started at askubu..

LXQt doesn't go to your hardware - its the linux kernel that does that.  You felt at first it was `openbox`, so did you replace it with `xfwm4`, `fluxbox` or something else, logout, login to confirm it wasn't `openbox`. You can then switch it back to `openbox` with your system restored on next logout/login. You can try logging in with other sessions (eg. openbox). 

Also what LXQt drew you'll see in screenshots (which you said have no errors - ie. it's not LXQt but how it's appearing on your screen which is far more likely kernel/kernel-modules.

Did you upgrade the Ubuntu GNOME & Kubuntu (KDE Plasma) with the same level of updates?  That would be worthwhile info knowning  (I have boxes with nvidia  that have issues with KDE/GNOME & `nouveau` that are flawless with Lubuntu/LXQt & it's simpler rendering & I've never seen it the way you describe - or I've miss understood something in how you tested; ie. I'm assuming you've installed *impish* Ubuntu 21.10 & Kubuntu 21.10 & upgraded to the same level but not had issues).

---

### Post by jesuel on 2021-10-20
Thanks for the effort in trying to understand my problem.

First of all, I'd like to say that I have installed plain Ubuntu 21.10 now and it is working without the problem. I gave up on Lubuntu, because I needed the computer to work and could not afford losing another day with these errors. 

I did not replace openbox. I only installed gnome by running 'sudo apt install gnome' on terminal and after that the problem was gone in the gnome desktop environment. Does this change openbox to something else?

I think I did not emphasize it enough in the first post, but it wasn't only a visual problem. The system was laggy when accessing the file manager as well as other lxqt utilities, like FeatherPad. Screenshots actually made the errors disappear while taking the screenshot (using screengrab) and then, afterwards, they were there again. 

I don't understand what you mean by "same level of updates". I simply ran "do-release-upgrade" and then sudo apt full-upgrade. I installed gnome as I said above. 

I have no NVidia product in this computer. My processor (Intel i710700K), has a                                                                                                                                           Intel UHD Graphics 630 unit inside.

---

### Post by guiverc on 2021-10-21
> **jesuel said:**
> First of all, I'd like to say that I have installed plain Ubuntu 21.10  now and it is working without the problem. ...
I did not replace openbox. I only installed gnome by running 'sudo apt  install gnome' on terminal and after that the problem was gone in the  gnome desktop environment. Does this change openbox to something else?

I don't understand what you mean by "same level of updates". I simply  ran "do-release-upgrade" and then sudo apt full-upgrade. I installed  gnome as I said above. 



GNOME doesn't use `openbox` by default, it's own WM functions for X11 are  handled by `mutter` though you can select a GNOME session using  `openbox` if it's setup.

(*if it's setup automatically my box  would likely have it; as I've both `ubuntu-desktop` (GNOME),  `lubuntu-desktop` (LXQt) & `xubuntu-desktop` (Xfce) installed - but  I'm not going to logout & look sorry; I'm also now on jammy but I  doubt that makes a difference)*

I've only had experience of a *flavor*  desktop (eg. Lubuntu) with a second desktop fully installed (eg. `sudo  apt install ubuntu-desktop` to install the full GNOME desktop &  apps) so I don't know how much of each stack you're using with your  different meta-packages (*and I'm too lazy to look up as its solved*).

The LXQt desktop doesn't speak directly to hardware, so issues are much lower in the stack..  I'm convinced it's not LXQt but something in your *stack* but it doesn't matter now as you've resolved it, so well done.

---


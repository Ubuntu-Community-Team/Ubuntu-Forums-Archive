---
title: "Need Help With New Xubuntu Install"
date: 2008-01-29
forum: General Help
---

### Post by xXChaoticNoiseXx on 2008-01-29
Ok.... i am somewhat new to linux and i need help. I have just instaledl Xubuntu 7.10

I have 3  main problems with my new install

1. Start up time is in the area of 3 to 4 minutes. If you have any tips or tricks on how to shorten this time period. i would greatly appreciate it.

2. On start up i dont get the xubuntu loading bar. The screen goes black and white writing comes up on the screen. The first statment states that its loading files need to boot. Then it goes on to talk about checking the system clock and intializing services and what not. The monitor then cuts off and prints to the screen "Can not display this video mode".

3. Finally i get to the login screen and proceed. when logging in the screen goes black once again and the cursor turns to a black x with a white outline. When the desktop wall paper does finally load up, if you move the mouse it leaves a black square where the mouse was. And anything i click on gets pushed down by that square. In short theres a invisible square that follows my cursor and it pushes window borders and items on the menu and panels around. When in a web browser that square makes a few squares that let you see through the window and to the desktop background.

I have the restricted drivers installed and all updates installed
The system is fairly old and has 512mb ram
Nvidia glx-legacy video card
Dell 1350E flat screen monitor
50 gig hdd
xserver-xorg installed
xserver-xgl installed
JRE installed
Flash player 9 installed
Flash install in firefox
1024 x 768 @ 60 hz
no beryl or compiz-fusion
no emerald
i have ubuntu and kubuntu completly removed

Its a pure Xubuntu install

These problems are really annoying me. The third more so then the rest. If anyone has any Solutions they are greatly appreciated

Thanks in advance

---

### Post by xXChaoticNoiseXx on 2008-01-29
*UPDATE*

I have elimanated the the square problem and the cannot display this video mode problem is fixed. I still get the white text saying what its loading.... but everything else is fine

but my terminal displays clear.... you can see through the window

---

### Post by sTpny on 2008-07-04
Hi, I've never used Xubuntu, but I know a couple of things that might help.  First off,   I beleive you can get rid of the white on black loading text when you start up by editing your you need to edit your options in /boot/grub/menu.lst. check out the man page to make sure, but I beleive you just add "quiet" without the quotes to shup up those messages.  Your startup time can be shortened significantly by editing which processes initialize on start up. in Ubuntu, it's in System->Preferences->Sessions
Your graphics are because of a problem with your /etc/X11/xorg.conf. You say you are using the restricted driver, but you didn't mention if you've run the configurators for it.  If not, it's nvidia-xconfig for a quick default xorg.conf, and nvidia-settings for a nice GUI to help it make more sence. You'll have to sudo those commands, but they are pretty easy to work with. You might also like to read their man pages.  ie: "man nv"<-the free driver, "man nvidia" <- the restricted driver, "man nvidia-settings", etc.  All without the quotes.

good luck. 

sTony

---


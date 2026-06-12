---
title: "[Gutsy] Dual Screens, Xgl, and compiz"
date: 2007-12-20
forum: General Help
---

### Post by Sir_Sid on 2007-12-20
I just installed ubuntu over my old kubuntu installation. A complete and fresh install. I ran into some problems with my dual screen setup. I was forced to manually edit the mode option in the xorg.conf to get the correct resolution. (I am using Xinerama)

So here is my problem.
I cant enable any desktop effects. I tried through the gui and I get the error saying they cannot be enabled. So I ran compiz in console and I got an error saying I did not have Xgl. I installed xserver-xgl and compiz worked, but the computer would not recognize the bounderies between my two monitors properly. As in when I maximized a window, it would maximize across both screens instead of only one. 

When I use my original xorg.conf with one monitor, compiz will work.
When I install xgl compiz will work across both monitors, but boundaries are not recognized
When I just use two monitors, compiz will not work but boundaries are recognized. 

Is there a way to use xgl and have it recognize my two monitors properly Or use compiz in any other way?

I have uploaded my current Xorg.conf file as an attachment.

SOLVED

I used nvidia-settings to use twinview instead of xinerama and compiz works now.

---

### Post by approaching on 2007-12-21
would you mind explaining your process a little more? what exactly did you do.

for my question to even matter, what card are you using?

---

### Post by Sir_Sid on 2007-12-21
Well I am using an nvida mobile card. I am not sure of its exact number but I think its the 7300. 

My setup is the laptop monitor and an external LCD. 


When I first installed Ubutnu, the menu in Administration >> Screens and graphics would not detect my two screens properly. When I edited screen 1, it would modify two. But if I modified screen 2, the resolutions would both change to something I didnt pick at all. This lead me to just edit my xorg.conf file manually.

 Near the bottom of the file, there is an options called Mode. From what I understand these are the available resolutions the screens will use. I just edited this field so the only available resolutions were the correct ones. (In all I edited two fields, the mode for each screen).

This got my two screens working properly, but I could not enable desktop effects. When I typed 
```
compiz
```
in console, I got an error saying xgl was missing. So I installed xserver-xgl. This lead to some pretty annoying window behaviour across both screens. I removed xserver-xgl. After a bit of searching I came across a tool called nvidia-settings 
```
sudo apt-get install nivida-settings
```
Using this tool I enabled twin-view instead of xinerama. This made desktop effects work as soon as I restarted X. 



SO, I didnt know which bit you needed clarifying with, but that was my story.
Now for the important bits from all that

If you have an nvidia card, two monitors, and you want compiz effects do the following:
Enable Proprietary Drivers
Install nvidia-Settings
Use it to enable twin-view and potentially edit your resolutions 
Restart X and there ya go.

---


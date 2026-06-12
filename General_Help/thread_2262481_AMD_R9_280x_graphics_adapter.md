---
title: "AMD R9 280x graphics adapter"
date: 2015-01-25
forum: General Help
---

### Post by virtual81 on 2015-01-25
I have just installed Ubuntu 14.10 for about the 3rd or 4th time.
Each previous attempt to install a more suitable graphics driver has failed leaving a blank screen on reboot.

I have a 64bit Ubuntu 14.10 install on a Z77 chipset, i5 3570K 8 gig ram and an R9 280x graphics card.
On launching Steam i get the following error message
```
Error: OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457.

```

Have tried the "fglrx" choices in Software & updates.
Have also tried the latest 64bit AMD driver.

Searching shows many with similar issues, but no solutions. [example]("https://mwop.net/blog/2014-11-03-utopic-and-amd.html")

I recall a previous venture into Ubuntu a couple of years ago i had a display control panel to configure graphics settings like AntiAliasing etc, but cant see anything like that at the moment. 

Can anyone offer any suggestions?

---

### Post by phidia on 2015-01-25
See if any of the ideas in [this thread]("http://ubuntuforums.org/showthread.php?t=2202873") at the forums here do any good.
AMD driver down link [here]("http://support.amd.com/en-us/download") and you can use that site to go to the forums there from drivers & support.

---

### Post by virtual81 on 2015-01-25
I'm not confident that what is posted in that thread is ideal for 14.10
Additionally in the second post xorg.conf is mentioned, however it appears 14.10 does not use an xorg.conf file, at least not one i could find when following a few guides to restore my ability to access a gui.

I wonder if anyone out there has any solid ideas proven to work on a 14.10 install that would allow for some modern steam games to run?

---

### Post by rjnicholson1591 on 2015-04-17
So I've been using 14.10 on my desktop for a while now, I have a single Sapphire R9 280X Vapour-X (silver-blue card with three fans).

Firstly the drivers from AMD's site do not work, I get a low graphics mode on boot, I could look into tinkering with this a bit more but I really don't like the idea of downloading them from the site, etc.

Secondly, the fglrx and fglrx-updates install and I'm able to access the desktop and play with the Catalyst settings, though I do have to run a command to disable Over/Underscanning for my LCD TVs. However, when I went to play a Steam game (Robocraft) the game would launch and run nicely until suddenly it would just completely freeze up my entire system forcing a complete restart. I can confirm that it was the Catalyst 14.20 with both fglrx and fglrx-updates, both of these seem to be the same.

So with fglrx freezing up my system, I was about to sigh and crawl back to windows and wait a few months before trying again, but then I came across a few posts about using the FOSS (xorg) drivers where you just don't any proprietary and just run with what you get from a fresh install. It seems AMD have recently been helping out on the FOSS front a lot so they have improved a lot. So with fglrx purged and xorg reinstalled and reconfigured, I loaded up Robocraft and found that I was getting a clean 60FPS with no freezing what so ever! I also added the oibaf ppa for more up to date drivers, I can't really say what difference they have made though as I only quickly tested Robocraft without the PPA so my experience is mostly with the PPA.

To conclude, for now with the R9 280X the FOSS drivers are the way to go it seems, though I did come across a few problems:
Underscanning was needed for my left LCDTV which goes through an active DisplayPort to DVI adapter, the xrandr commands handily sort this one out.
Minecraft and other FGLRX Java games would reset my display setups to some kind of fallback showing only one monitor when they were closed, turns out creating a basic xorg config that doesn't really do anything stops this from happening.

Another cool tip is to copy your ~/.config/monitors.xml to /var/lib/lightdm/.config/ once your displays are all positioned nicely so that they are applied to the login screen, guest logins and set as the defaults for new users. There's also ARandR which is a very simple but effective GUI for arranging multiple displays as the default Ubuntu GUI for this can be a right pain. ARandR (or xrandr via command) can also be used to turn of dispalys that are showing as connected when they're not to prevent the mouse cursor from flickering too, clicking on 'phantom dispalys' in the Ubuntu GUI seems to crash the GUI but this doesn't happen in ARandR or xrandr -r displaytype --off (I think that's the syntax) can be used.

---


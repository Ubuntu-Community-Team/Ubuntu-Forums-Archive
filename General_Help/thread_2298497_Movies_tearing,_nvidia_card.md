---
title: "Movies tearing, nvidia card"
date: 2015-10-11
forum: General Help
---

### Post by gospodorz on 2015-10-11
Hello there,

Movies both on YT and those played from HDD using vlc are tearing. My graphic card is Geforce GTX 860M, using Ubuntu 14.04. Google and searching here didn't help. 

I think my vsync is off since it don't work in games on steam.

Nvidia drivers version: 346.96

Anyone know if its fixable or I have to watch movies on Windows?

Thanks in advance!

Edit:
When I switch to Intel GPU (Power saving mode) tearing disappears, so problem lays in nvidia drivers i guess.
Also vsync works, when Intel GPU is active. Is there a way to turn vsync on in nvidia drivers?

---

### Post by efflandt on 2015-10-12
I guess I had always seen a checkbox for **Sync to VBlank** (although, I never use that setting), which on my desktop is in **OpenGL Settings** of **NVIDIA X Server Settings**.

But I just checked on my laptop and apparently that setting is not there. There is something in **NVIDIA X Server Settings** under **X Server XVideo Settings**, but that just says **Currently synced to display: unknown**, and under that **Sync to this display device** just has a radio button on **Auto**, which seems like it cannot be changed, so maybe you cannot change that with hybrid graphics. I never noticed tearing on my GTX 765M @ 1080p (except Unigine Valley benchmark), which had been using nvidia-331-updates until I recently installed nvidia-355 from graphics-drivers/ppa. Your GTX 860M should be somewhat faster, unless it needs a newer driver like nvidia-352 or nvidia-355. [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by mc4man on 2015-10-12
You may try this test ppa I set up to fix most tearing with Optimus cards using nvidia drivers via nvidia-prime.
Instructions, ect. on page
[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

---

### Post by gospodorz on 2015-10-12
Could u guide me a little through that ppa-thing? I'm rather new to ubuntu, and intructions inside those links aren't clear for me.

---

### Post by SeijiSensei on 2015-10-12
I have Sync to VBlank enabled in the NVIDIA X Server Settings application.  I never see any tearing.  I use smplayer with the xv output driver for video.

---

### Post by QDR06VV9 on 2015-10-12
> **gospodorz said:**
> Could u guide me a little through that ppa-thing? I'm rather new to ubuntu, and intructions inside those links aren't clear for me.
To add PPA
```
sudo add-apt-repository ppa:mc3man/tearfree-test
```
Then add the PPA he recomends
```
sudo add-apt-repository **ppa:graphics-drivers/ppa**
```
Update && Upgrade your system
```
sudo apt-get update
sudo apt-get upgrade
```



To Remove it and revert changes 
```
sudo appt-get install ppa-purge
sudo ppa-purge ppa:mc3man/tearfree-test
sudo apt-get update
sudo apt-get dist-upgrade
```
I would give [COLOR=#000000]SeijiSensei's suggestion a try if this is of no help.
Regards[/COLOR]

---

### Post by gospodorz on 2015-10-12
@SeijiSensei
I don't have option to change vsync in nvidia settings. It's just off and not enableable or am I blind?

---

### Post by SeijiSensei on 2015-10-12
> **gospodorz said:**
> @SeijiSensei
I don't have option to change vsync in nvidia settings. It's just off and not enableable or am I blind?

I won't cast aspersions on your vision!

In my case it appears in the OpenGL settings dialog under X Screen 0.  I have a check box for "Sync to VBlank" and one for image flipping.  I'm using a GTX 750.

---

### Post by QDR06VV9 on 2015-10-12
It is in OpenGL Settings then on the right you will see Sync to VBlank.
But I don't run a hybrid card. I put a screen of my nvidia-settings so I do not get to see what you have.

---

### Post by gospodorz on 2015-10-12
> [COLOR=#000000]I won't cast asp[/COLOR][COLOR=#000000]ersions on your vision![/COLOR]

[COLOR=#000000]In my case it appears in the OpenGL settings dialog under X Screen 0. I have a check box for "Sync to VBlank" and one for image flipping. I'm using a GTX 750.[/COLOR]

Yeah, for me option just isn't there.


ill try that runrickus guide now.

---

### Post by gospodorz on 2015-10-12
Installed it, didn't help. Also I noticed tearing on Intel GPU too, just a little less, but it's tearing too. I proobably just didn't notice that first time. So the problem don't have to be caused by lack on nvidia vsync.

---

### Post by QDR06VV9 on 2015-10-12
Just to check see if your [COLOR=#333333][FONT=monospace]/etc/X11/xorg.conf Shows this
```
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Section "Device"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    Identifier "intel"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    Driver "intel"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    BusID "PCI:0@0:2:0"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    Option "AccelMethod" "SNA"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    Option "TearFree" "True"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]EndSection[/FONT][/COLOR][COLOR=#333333][FONT=monospace]
```

[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-10-12
Try installing smplayer from the repositories and seeing how well that works.  By default it will use mplayer as its engine, but I recommend using [Doug McMahon's repository]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") to fetch smplayer and the successor to the mplayer engine, mpv. If you're using 14.04LTS, then follow these steps:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install smplayer mpv

```
You can tell smplayer to use mpv by changing the entry for the executable to /usr/bin/mpv in smplayer's Options > Preferences > General dialog.

You can also try switching the video driver in Options > Preferences > General > Video from "xv" to "vdpau." That will use the built-in hardware decoder in the NVIDIA card which might also help.

---

### Post by shutterfoot on 2015-10-12
Have you checked to see if your desktop composite manager  is set to "sync to vblank?" If you are on Unity you're probably using compiz, and it should be under the OpneGL plugin. Though I've noticed (on XFCE with intel graphics also) that sometimes screen tearing, and some odd behavior, still occurs with it on, and so I turn off the desktop compositor and sync and instead find the in-game options for sync to vblank (for steam) and in kodi (mediacenter i watch my shows and movies on). For me that works flawlessly then.

---

### Post by gospodorz on 2015-10-12
@[COLOR=#000000]shutterfoot
I don't have any sync options under Opengl, I mentioned that somewhere above.

[/COLOR][COLOR=#000000]@SeijiSensei
I will try that tomorrow, but problem is that YT videos and streams on twitch.tv are tearing too, so that rather won't satisfy me

@[/COLOR][COLOR=#000000]runrickus
Yes, xorg.conf shows this.[/COLOR]

---

### Post by shutterfoot on 2015-10-12
Oh sorry, I must've missed that. I thought it wasn't present in nvidia settings, so thought maybe we'd give compizconfig a try. You can also try disabling your compositor altogether and see if that makes any difference.

---

### Post by QDR06VV9 on 2015-10-12
> **gospodorz said:**
> [COLOR=#000000]
@[/COLOR][COLOR=#000000]runrickus
Yes, xorg.conf shows this.[/COLOR]
Thanks for testing that out, Sorry it was not successful.:(
Regards

---

### Post by gospodorz on 2015-10-14
So smplayer didn't help.

I guess I will have to say sorry to Windows when watching movies and just wait nvidia to fix that.

Thanks for help guys!

---

### Post by mc4man on 2015-10-14
> **gospodorz said:**
> So smplayer didn't help.

I guess I will have to say sorry to Windows when watching movies and just wait nvidia to fix that.

Thanks for help guys!
You don't need nvidia drivers to watch videos, the Intel gpu works quite fine with or without hwdec (vaapi

Am curious - what session are you using as my experience here is that a ubuntu (unity/compiz) session on Intel gpu has absolutely no tearing, not on the Desktop nor in any videos. (seen in various Intel/Nvidia mobile combos from last few years

---

### Post by gospodorz on 2015-10-15
How to check what session am I using?

---

### Post by QDR06VV9 on 2015-10-15
It would be the output of
```
 echo $DESKTOP_SESSION
```
Mine
```
echo $DESKTOP_SESSION
mate

```

---

### Post by gospodorz on 2015-10-15
```
dominik@dominik-Aspire-VN7-591G:~$  echo $DESKTOP_SESSION
ubuntu

```

---

### Post by mc4man on 2015-10-15
Can you post a sample clip somewhere that shows tearing for you?
Attached is sample tearing test video, unpack & try in various players both in a window & fullscreen. Tearing would show up as a break in the pole sides. The test vid is not 100% conclusive, see below.

If the above vid is ok then this short clip can expose the lack of vsync during the fight scene about 26 sec in.
[http://www.datafilehost.com/d/2a524d0f](http://www.datafilehost.com/d/2a524d0f)

This ^ is with the intel gpu, using the mobile nvidia will show tearing in both unless patched as I suggested, then tearing only occurs with cursor movement in the video window.
(- though with nvidia mobile & default ubuntu-drivers-common no need for a vid to expose tearing, all I need to do is pick up a window & shake it horizontally, the window sides break clearly..

---

### Post by gospodorz on 2015-10-17
On Windows ur sample works flawlessly.

On Ubuntu switched to nvidia gpu its tearing a lot.

Switched to intel gpu, still shows tearing, just a bit less.

Previously I was testing it using this video: [https://www.youtube.com/watch?v=piH5_aP0fY8](https://www.youtube.com/watch?v=piH5_aP0fY8)
Moment 2:48 - 2:53 shows a LOT of tearing, still on windows it works flawlessly.

Sorry that it took me so long to respond, but I had isp problems.

---

### Post by mc4man on 2015-10-17
> **gospodorz said:**
> On Windows ur sample works flawlessly.

On Ubuntu switched to nvidia gpu its tearing a lot.

Switched to intel gpu, still shows tearing, just a bit less.

Previously I was testing it using this video: [https://www.youtube.com/watch?v=piH5_aP0fY8](https://www.youtube.com/watch?v=piH5_aP0fY8)
Moment 2:48 - 2:53 shows a LOT of tearing, still on windows it works flawlessly.

Sorry that it took me so long to respond, but I had isp problems.
Which player(s) show tearing when on Intel gpu. 
Also install compizconfig-settings-manager, open it up (command of ccsm) & compare settings in screenshot.

---

### Post by gospodorz on 2015-10-19
My settings looks the same, but I noticed strange thing.

When I switch to Intel gpu and login then logout, movies show tearing.
But, when I switch gpus and restart system, there is almost no tearing if no at all.

---

### Post by mc4man on 2015-10-19
> **gospodorz said:**
> My settings looks the same, but I noticed strange thing.

When I switch to Intel gpu and login then logout, movies show tearing.
But, when I switch gpus and restart system, there is almost no tearing if no at all.
The switch of gpu via a log out/in works ok here in 14.04 but doesn't that well in 15.10 (don't have 15.04
So not getting a good switch in 14.04, while is ok here, does have some possibility.
If the switch over issues continue on 16.04 with a log out/in I'll probably file a bug.

Do you see this with all players?

---

### Post by gospodorz on 2015-10-20
In all players and in web browser.

---


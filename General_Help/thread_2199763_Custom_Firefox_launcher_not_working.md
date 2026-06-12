---
title: "Custom Firefox launcher not working?"
date: 2014-01-15
forum: General Help
---

### Post by d4m1r on 2014-01-15
Hey guys, I am having a very strange problem....

I have recently enabled hardware acceleration for Firefox but basically, to enable it I now need to launch Firefox with "VDPAU_DRIVER=va_gl firefox" in the terminal for example. Instead of having to manually launch Firefox via terminal everytime, I just wanted to modify the Firefox shortcut on my Unity launcher. I was told I could do this by editing the "firefox.desktop" file in /usr/share/applications to something like "Exec=env VDPAU_DRIVER=va_gl firefox %u" instead of just "firefox %u". Well, that didn't work (Firefox launches but no hardware acceleration)...Now I am trying to edit the firefox shortcut on my Unity bar by using the stock "Main Menu" application. BUT if I change the parameter for Firefox in my Unity bar to anything other than the default "firefox %u", it just doesn't launch....

It will blink a few times but will never launch :confused: I have tried setting it to "VDPAU_DRIVER=va_gl firefox", ""VDPAU_DRIVER=va_gl firefox %u", and even "Exec=env VDPAU_DRIVER=va_gl firefox %u", but it will not launch....What is going on?? All those commands work just fine in the terminal...

---

### Post by deadflowr on 2014-01-15
I would recommend opening the fire.desktop ,and save it with save as and place the new save in the users home folder
Put it in this
```
/home/user/.local.share/applications/
```
This way you can edit it without the need to run as root.
It'll also take precedence in loading over the file in the /usr/share folder.

but aside from that, have you tried a plain entry
```
Exec=[COLOR=#000000]env VDPAU_DRIVER=va_gl firefox %u[/COLOR]
```
no quotes.

---

### Post by d4m1r on 2014-01-15
Huh?

1) There is no /home/user folder.

2) Yes ofcourse, I never actually put the quotation marks in....Just used it in my original post to seperate the commands I used against my normal text ;)

---

### Post by deadflowr on 2014-01-15
/home/user = your name.

---

### Post by mc4man on 2014-01-15
hwacell thru env VDPAU_DRIVER=va_gl works fine here when editing /usr/share/applications/firefox.desktop (though I prefer to manually start in instances where it makes sense.

The icon in the unity launcher by default opens /usr/share/applications/firefox.desktop so if you use some means to create another firefox.desktop then I'd first remove your current launcher & then - 
 add your alternate one via. drag & drop 
or 
if your new launcher has been made executable then d. left click on & after it opens pin it to launcher.

By what means are you determining if hwacell is enabled?

---

### Post by d4m1r on 2014-01-17
Nothing seems to work....

1) Tried setting /usr/share/applications/firefox.desktop to Exec=env VDPAU_DRIVER=va_gl firefox %u, and that didn't work...Complains about the Exec=env part so I removed it and still nothing.

2) Tried removing the unity shortcut to try to get it to pickup the changes I made to /usr/share/applications/firefox.desktop but that doesn't work either...

3) I tried to start Firefox with my script.sh (containing just Exec=env VDPAU_DRIVER=va_gl firefox), confirmed hardware acceleration working, pinned it to desktop. Restarted Firefox and it was software acceleration again (as if I had used the stock launcher).


FYI, to check if hardware acceleration is actually enabled or not, go to any Youtube video, right click on the video, stats for nerds, and it should say something other than "software acceleration".

---

### Post by d4m1r on 2014-01-19
Anyone have any ideas? :(

---

### Post by d4m1r on 2014-02-09
Well, looks like that was indeed a bug and it is thankfully fixed in the latest Flash update (11.2.202.336).

However, I still can't get Firefox to launch by default with hardware acceleration from the Unity Bar. **NONE** of the below methods work.....

> 1) Tried setting /usr/share/applications/firefox.desktop to Exec=env  VDPAU_DRIVER=va_gl firefox %u, and that didn't work...Complains about  the Exec=env part so I removed it and then it complains about the VDPAU part...

2) Tried removing the unity shortcut to try to get it to pickup the  changes I made to /usr/share/applications/firefox.desktop but that  doesn't work either...

3) I tried to remove my Firefox unity shortcut,  start Firefox with my script.sh (containing just Exec=env  VDPAU_DRIVER=va_gl firefox), confirmed hardware acceleration working,  pinned it to desktop. Restarted Firefox and it was software acceleration  again (as if I had used the stock launcher).


---

### Post by aeyeaws on 2014-06-14
[B]lifted from another site, for intel vid

Install and set up libvdpau-va-gl in Ubuntu[/B]


[B][COLOR=red]Important:[/COLOR] make sure [libvdpau-va-gl1]("http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html") is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package.

**1.** Firstly, install the VAAPI drivers 
sudo apt-get install i965-va-driver
[B]
2.[/B] Install libvdpau-va-gl by using the main WebUpd8 PPA
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install libvdpau-va-gl1
[B]
3.[/B] Adobe Flash doesn't use hardware acceleration by default on Linux so we'll have to force it:
sudo mkdir -p /etc/adobe
echo "EnableLinuxHWVideoDecode=1" | sudo tee /etc/adobe/mms.cfg
echo "OverrideGPUValidation=1" | sudo tee -a /etc/adobe/mms.cfg
[B]
4. Like I was telling you above, it's not a good idea to enable libvdpau-va-gl system-wide yet. Instead, you can simply launch an application with VDPAU_DRIVER=va_gl  firefox[/B][/B]

---

### Post by monkeybrain20122 on 2014-06-14
> **aeyeaws said:**
> 


[B][COLOR=red]Important:[/COLOR] make sure [libvdpau-va-gl1]("http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html") is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package.

[/B]

Where did you get Nvidia settings without a Nvidia card? If you have an Nvidia card you don't need libvdpau-va-gl as it supports vdpau directly and libvdpau-va-gl won't work because it does vdpau through vaapi and only Intel does vaapi (Even AMD does VDPAU directly now instead of VAAPI, at least for the open driver)

I enbale libvdpau-va-gl system wide on Ubuntu 13.10, 14.04 and Fedora 20, I have not experienced a problem but I have an intel card.

---

### Post by monkeybrain20122 on 2014-06-14
> **d4m1r said:**
> Hey guys, I am having a very strange problem....

I have recently enabled hardware acceleration for Firefox but basically, to enable it I now need to launch Firefox with "VDPAU_DRIVER=va_gl firefox" in the terminal for example. Instead of having to manually launch Firefox via terminal everytime, I just wanted to modify the Firefox shortcut on my Unity launcher. I was told I could do this by editing the "firefox.desktop" file in /usr/share/applications to something like "Exec=env VDPAU_DRIVER=va_gl firefox %u" instead of just "firefox %u". Well, that didn't work (Firefox launches but no hardware acceleration)...Now I am trying to edit the firefox shortcut on my Unity bar by using the stock "Main Menu" application. BUT if I change the parameter for Firefox in my Unity bar to anything other than the default "firefox %u", it just doesn't launch....

It will blink a few times but will never launch :confused: I have tried setting it to "VDPAU_DRIVER=va_gl firefox", ""VDPAU_DRIVER=va_gl firefox %u", and even "Exec=env VDPAU_DRIVER=va_gl firefox %u", but it will not launch....What is going on?? All those commands work just fine in the terminal...

Well I would simply enable libvdpau-va-gl system wide. If you mess with the .desktop file it will be undone when Firefox updates next time.

1) If you install libvdpau-va-gl from repo or ppa, 

```
gksudo gedit /etc/X11/Xsessions.d/20vdpau-va-gl
```
and uncomment the last two lines (remove the # in front) , save and then reboot

2) If you compile libvdpau-va-gl then
open the file /etc/environment
and add the line
```
export VDPAU_DRIVER=va_gl
```
Save and reboot

The version in 14.04's repo is old, and I remember that it didn't work when I tested it when 14.04 was released. You can update with the webupd8 ppa
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get upgrade

```

There was(is?) a bug if you try to play .mov video using mplayer (either local file or apple trailers with gecko-mediaplayer plugin) or vlc with vdpau enabled then you will see only a blackbox with audio n (with vlc you can always use vaapi directly instead) This was fixed in master a while back so I compiled it myself. I don't know whether the webupd8 ppa has upgraded or not.

---

### Post by monkeybrain20122 on 2014-06-14
BTW, it would not worth the trouble to enable libvdpau-va-gl only for flash, actually that means only Youtube (vdpau for flash works only on Youtube and there are many ways to play Youtube without flash) If you enable it system wide you can also use it with mplayer based video players, which are more efficient than vlc working directly with vaapi (you can also use mpv with vaapi, but mpv is not in the repo and the interface is a bit sparse)

---

### Post by d4m1r on 2014-06-25
> **monkeybrain20122 said:**
> BTW, it would not worth the trouble to enable libvdpau-va-gl only for flash, actually that means only Youtube (vdpau for flash works only on Youtube and there are many ways to play Youtube without flash) If you enable it system wide you can also use it with mplayer based video players, which are more efficient than vlc working directly with vaapi (you can also use mpv with vaapi, but mpv is not in the repo and the interface is a bit sparse)

Thanks for the reply, but it is widely NOT recommended to enabled the Intel based hardware acceleration system wide for 2 reasons as I understand it. First off, it conflicts with Nvidia drivers if you have a dedicated GPU along with an Intel integrated one (like I do). Also, they are very much still in beta state apparently so not stable enough to be be used system wide.

Regardless, the only benefit I see for this right now is for Youtube anyway so I'm perfectly happy with only implementing it for Firefox. As an update, I eventually did get this working by doing what I previously described The problem was a bug in the software that was later corrected in an update, so I was doing the right thing all along!

---

### Post by monkeybrain20122 on 2014-06-25
> **d4m1r said:**
> Thanks for the reply, but it is widely NOT recommended to enabled the Intel based hardware acceleration system wide for 2 reasons as I understand it. First off, it conflicts with Nvidia drivers if you have a dedicated GPU along with an Intel integrated one (like I do). Also, they are very much still in beta state apparently so not stable enough to be be used system wide.

Regardless, the only benefit I see for this right now is for Youtube anyway so I'm perfectly happy with only implementing it for Firefox. As an update, I eventually did get this working by doing what I previously described The problem was a bug in the software that was later corrected in an update, so I was doing the right thing all along!

Well I have no idea about Optimus machines. I have only an Intel card and I enable vdpau-va-gl system wide with no problem (on more than one machines).  As a general point IMO "beta" software can work very well and 'stable' releases can be buggy simply because in beta bugs are also fixed very quickly. You get the worst of all worlds when you put a beta software in feature freeze like many applications in Ubuntu's repo (libvdpau-va-gl1 is in 14.04's repo but it is some old version which may not even work, I would either install from webupd8's ppa or compile the latest myself)

But since you have a Nvidia card why do you need this? As I understand  you can run applications with the Nvidia card on demand using bumblebee  so just use  the Nvidia card when you need vdpau.

I wouldn't be bothered with flash as it works only on Youtube and I don't use flash on Youtube anyway (Viewtube/ smtube) Also enabling vdpau for flash will result in flash crashing or hanging on some sites. I use it mainly for mplayer (Smplayer and gecko-mediaplayer plugin for Firefox)


P.S. If you change the desktop file it will not work after a Firefox update as it will be replaced.

---


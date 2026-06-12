---
title: "So what is the best display server to use?"
date: 2023-06-12
forum: General Help
---

### Post by SpaceManJack on 2023-06-12
So I'm currently using Ubuntu 22.04 and I've got my PC hooked up to my 55 inch 2019 TCL 4k TV, I had to go into settings and double the font to 200% cause everything was just way too small at first.

So I've just now learned about display servers after doing some googling. So what's the best display server to use then? Wayland?

So i was previously using my 24 inch 1080p monitor.

So yeah I have hooked up my PC to my 55 inch 4k TV and at first everything was way too small so I had to increase the font to 200% in settings, which fixed that.

But It seems to me my mouse is a little laggy, like just a tad laggy. Like my mouse movement seems to be fine for the most part but occasionally it will stutter, I don't remember having any problems with my mouse on the 24 inch monitor. Are there any servers for the mouse as well?

I've got a wireless logitech mouse I bought back in 2021. So yeah it seems on this giant 55 inch screen my mouse movement isn't totally smooth and perfect (it's fine for the most part but it stutters here and there), what gives?

---

### Post by Holger_Gehrke on 2023-06-12
Display in this case means everything needed for having a GUI, so  graphics, mouse, keyboard are all handled by the display server. Wayland is the newer display server protocol. X11 is the older one. The idea behind Wayland is to not have all the historical baggage which X11 has to carry with it since its design goes back to the early 80s. There are two problems with this: after 15 years of development it still is in the opinion of a very vocal part of the users of Linux not quite production quality (that mouse lag is a [known Wayland/Gnome problem]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1982560") and you seem to have a mild case of it ...) and some of the features Wayland doesn't implement are very useful, so people who rely on those won't even try Wayland. Since I now and then need the network transparency of X11 (meaning application and display can be two different machines connected over a network, you start a program on a different machine and get it's window on your desktop) and I'm using XFCE as my DE and that doesn't support Wayland yet I'm staying on X11 for the foreseeable future. 

Holger

---

### Post by SpaceManJack on 2023-06-13
> **Holger_Gehrke said:**
> Display in this case means everything needed for having a GUI, so  graphics, mouse, keyboard are all handled by the display server. Wayland is the newer display server protocol. X11 is the older one. The idea behind Wayland is to not have all the historical baggage which X11 has to carry with it since its design goes back to the early 80s. There are two problems with this: after 15 years of development it still is in the opinion of a very vocal part of the users of Linux not quite production quality (that mouse lag is a [known Wayland/Gnome problem]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1982560") and you seem to have a mild case of it ...) and some of the features Wayland doesn't implement are very useful, so people who rely on those won't even try Wayland. Since I now and then need the network transparency of X11 (meaning application and display can be two different machines connected over a network, you start a program on a different machine and get it's window on your desktop) and I'm using XFCE as my DE and that doesn't support Wayland yet I'm staying on X11 for the foreseeable future. 

Holger

Yes on the 24 inch 1080p monitor I couldn't detect any discernible mouse lag but as soon as I hooked my computer up to my 55 inch 4k TV I can tell the mouse movement just isn't as sharp feeling, like it feels a little slow.
There's no fix for this? Am I really gonna have to go back to Windows in order to fix this because I'd like to continue to use my 55 inch if I could. For what it's worth my PC is a build from 2015 with a (at the time) mid-range GeForce GTX 750 Ti
and an AMD quad-core CPU, 16 gigs of ram, it was built to play Starcraft 2 at max settings, what's funny is it couldn't play Starcraft 2 at max settings even though everyone assured me the 750 Ti would be able to do so lol. And I'm using a cheap $20 logitech mouse I picked up 
back in 2021, could it possibly be the mouse? Should I buy a new mouse?

Yeah I remember back in 2015 asking Reddit what I'd need in order to play Starcraft 2 at max settings and multiple people recommended the 750 Ti, but it could barely do medium settings lol. 

If I can't fix this slow mouse movement I might have to consider going back to Windows because I didn't have this problem on Windows, I don't understand why the developers of Linux think this is acceptable, this is unacceptable!!! It's 2023 and lots of people are now
hooking up their PCs to their giant TVs, the last thing a person wants is to have slow mouse movement. This is ridiculous!

Any developers here who work on Linux? Do Linux developers actually visit this forum? Seriously if I can't get this resolved then I may have to go back to Windows. I'm not trying to hate on Linux but dude I can't live with this, this is unacceptable.

---

### Post by Holger_Gehrke on 2023-06-13
No, developers usually don't read this forum. It's mostly experienced users helping other users.

NVidia were kind of late to the party as far as support for Wayland is concerned. They are generally problematic for use with Linux since they treat the information necessary to write drivers as confidential business secrets. So to get good performance out of them you have to install NVidia's drivers. In Ubuntu there's a tool to download and install additional drivers including the ones for NVidia graphic cards. Have you done so ?

Another approach would be to try running with X11. When logging in after selecting your username there should be a cog icon which allows you to select what kind session you want. There should be a choice for 'Ubuntu on Xorg' or words to that effect.

Holger

---

### Post by TheFu on 2023-06-13
> **scott130 said:**
>  
If I can't fix this slow mouse movement I might have to consider going back to Windows because I didn't have this problem on Windows, I don't understand why the developers of Linux think this is acceptable, this is unacceptable!!! It's 2023 and lots of people are now
hooking up their PCs to their giant TVs, the last thing a person wants is to have slow mouse movement. This is ridiculous!

Any developers here who work on Linux? Do Linux developers actually visit this forum? Seriously if I can't get this resolved then I may have to go back to Windows. I'm not trying to hate on Linux but dude I can't live with this, this is unacceptable.

Nobody here works for Canonical.  We are volunteers helping others.

You appear to have a misunderstanding for what Ubuntu and Linux are.  There's no single company behind Linux. Canonical is like a reseller. They get thousands of independent projects and put them into a package, then give it away.  I think we are getting our money's worth.

As for GPU drivers, those come from the vendors making the cards.  You can't really blame Linux for crappy drivers for your card.  YOU picked the hardware.  If you are unhappy with the supported drivers under Linux, YOU should complain to the hardware maker and consider taking your money to a company with better Linux support next time.

There are millions of Linux developers around the world, but the skills needed to do driver development are very specialized.

If Linux doesn't meet your needs and MS-Windows does, then you should run Windows.  I know that I'm not seeing slow mouse on my systems, but my setup is nothing like yours.  I don't use Wayland.  This is because there are some workflows I need that depend on X11.  I don't use wireless mice or keyboards.  I don't use wifi.  I don't use nvidia GPUs anymore (except in 1 system).

**I hope you find happiness.  Every OS can be frustrating, sometimes.  ** Hopefully, the frustration from MS-Windows that caused you to try Linux won't be problems this time. Good luck.

I doubt it is the mouse, but you never know.  If it is USB, try a PS2 mouse instead.

---

### Post by MAFoElffen on 2023-06-13
```

sudo apt install ratbagd piper

```
Piper is an opensource GUI gaming mouse settings and profile tool... 'ratbagd' is a dependency for it.

RE: [https://itsfoss.com/piper-configure-gaming-mouse-linux/](https://itsfoss.com/piper-configure-gaming-mouse-linux/)

---

### Post by SpaceManJack on 2023-06-14
> **MAFoElffen said:**
> ```

sudo apt install ratbagd piper

```
Piper is an opensource GUI gaming mouse settings and profile tool... 'ratbagd' is a dependency for it.

RE: [https://itsfoss.com/piper-configure-gaming-mouse-linux/](https://itsfoss.com/piper-configure-gaming-mouse-linux/)

I'm hesitant to try this for fear it might screw my whole system up, is this what you use for your computer?

---

### Post by MAFoElffen on 2023-06-14
Yes... With gaming mice, nVidia GPU's and such. I've a bit of experience with Windows, Linux and UNIX.

I still do X11. I've been using XServer since 1988. I've been supporting Xorg since 2015. (When Alan Coopersmith taught me much about X11 and doing nVidia SLI on OpenSolaris.) I've been supporting the Linux Graphics Layer since 2010. Maybe you've seen my [Graphics Resolution Sticky]("http://ubuntuforums.org/showthread.php?t=1743535") on the Forum?

I can use Wayland, but have had problems with it from time to time. It is also not well supported by nVidia and Steam Games. So I keep going back to using X11. I think Wayland is getting closer, but is not there yet. No matter what the marketing hype says. It's still growing and working things out.

Yes, I went to four x 44" 4K displays about 6 years ago. At the defaults, I would lose my cursor and it took me forever to get across the screens with the cursor. I made the cursor much larger and lowered the DPI, so that the mouse would go across them much faster.

---

### Post by SpaceManJack on 2023-06-14
> **Holger_Gehrke said:**
> No, developers usually don't read this forum. It's mostly experienced users helping other users.

NVidia were kind of late to the party as far as support for Wayland is concerned. They are generally problematic for use with Linux since they treat the information necessary to write drivers as confidential business secrets. So to get good performance out of them you have to install NVidia's drivers. In Ubuntu there's a tool to download and install additional drivers including the ones for NVidia graphic cards. Have you done so ?

Another approach would be to try running with X11. When logging in after selecting your username there should be a cog icon which allows you to select what kind session you want. There should be a choice for 'Ubuntu on Xorg' or words to that effect.

Holger

So uh yeah I'm not using Wayland I'm using whatever is the default display server for Ubuntu, it's just i was having issues with my mouse so that's why I was wondering what the best display server is to use?

"So to get good performance out of them you have to install NVidia's  drivers. In Ubuntu there's a tool to download and install additional  drivers including the ones for NVidia graphic cards. Have you done so ?" 

Hey I'm actually using the default Ubuntu driver right now but I do know about the NVidia drivers. So here's the story about 4 months ago now I upgraded from 20.04LTS to 22.04LTS and on 22.04LTS I had the NVidia drivers installed but an update caused my whole computer to crash, I had to do a fresh clean install of 22.04LTS. I was told the NVidia drivers were to blame, so yeah this happened about 4 months ago now, here look [https://ubuntuforums.org/showthread.php?t=2483119](https://ubuntuforums.org/showthread.php?t=2483119) So first off, when 24.04LTS comes out I'm going to wait at least a year after it's been out before I upgrade to it, I've learned my lesson there. Because I switched to 22.04 when it had only been out for about 6 months.

But yeah I was using the NVidia drivers with 20.04LTS with no problems whatsoever, but hey 22.04LTS has been out now for over a year so I think I will try out the NVidia drivers again, so yes I will try that out and get back to you. Thanks.

But I've learned my lesson, when 24.04LTS comes out I won't be switching to it until it's been out for at least 1 year, let them work all the bugs out you know what I'm saying?

---

### Post by SpaceManJack on 2023-06-14
> **TheFu said:**
> Nobody here works for Canonical.  We are volunteers helping others.

You appear to have a misunderstanding for what Ubuntu and Linux are.  There's no single company behind Linux. Canonical is like a reseller. They get thousands of independent projects and put them into a package, then give it away.  I think we are getting our money's worth.

As for GPU drivers, those come from the vendors making the cards.  You can't really blame Linux for crappy drivers for your card.  YOU picked the hardware.  If you are unhappy with the supported drivers under Linux, YOU should complain to the hardware maker and consider taking your money to a company with better Linux support next time.

There are millions of Linux developers around the world, but the skills needed to do driver development are very specialized.

If Linux doesn't meet your needs and MS-Windows does, then you should run Windows.  I know that I'm not seeing slow mouse on my systems, but my setup is nothing like yours.  I don't use Wayland.  This is because there are some workflows I need that depend on X11.  I don't use wireless mice or keyboards.  I don't use wifi.  I don't use nvidia GPUs anymore (except in 1 system).

**I hope you find happiness.  Every OS can be frustrating, sometimes.  ** Hopefully, the frustration from MS-Windows that caused you to try Linux won't be problems this time. Good luck.

I doubt it is the mouse, but you never know.  If it is USB, try a PS2 mouse instead.

I'm not using Wayland I'm using the default display server which is X11 right? I was simply asking what the best display server is to use? 

So NVidia GPUs don't play well with Linux, ok I'll remember that next time I build a PC for sure, so which GPUs are best for Linux, AMD?

---

### Post by SpaceManJack on 2023-06-14
> **MAFoElffen said:**
> Yes... With gaming mice, nVidia GPU's and such. I've a bit of experience with Windows, Linux and UNIX.

I still do X11. I've been using XServer since 1988. I've been supporting Xorg since 2005. (When Alan Coopersmith taught me much about X11 and doing nVidia SLI on OpenSolaris.) I've been supporting the Linux Graphics Layer since 2010. Maybe you've seen my [Graphics Resolution Sticky]("http://ubuntuforums.org/showthread.php?t=1743535") on the Forum?

I can use Wayland, but have had problems with it from time to time. It is also not well supported by nVidia and Steam Games. So I keep going back to using X11. I think Wayland is getting closer, but is not there yet. No matter what the marketing hype says. It's still growing and working things out.

Yes, I went to four x 44" 4K displays about 6 years ago. At the defaults, I would lose my cursor and it took me forever to get across the screens with the cursor. I made the cursor much larger and lowered the DPI, so that the mouse would go across them much faster.

"I made the cursor much larger and lowered the DPI, so that the mouse would go across them much faster" 
You can do that with Piper? Should I do that too?

Hey please go through here and read my other comments I've made to the others, I'm not currently using NVidia drivers for my GPU I'm using the Ubuntu default driver, one of the other users said I should switch over to NVidia drivers, so let me ask you are you using an NVida GPU and the NVidia drivers?

I'm going to switch to the NVidia drivers and see if that fixes my problem.

---

### Post by SpaceManJack on 2023-06-14
You know a user here said to try the NVidia drivers and that's actually a good point sir, I'll try that. The only reason I wasn't using the NVidia drivers was cause it caused a bug with an update which caused my whole computer to crash, which I fully explained in an earlier comment in this here thread.

I'll try the NVidia drivers and I'll get back to y'all.

---

### Post by MAFoElffen on 2023-06-14
Having used high-end GPU's since 2003 on Windows, then UNIX, then Linux...

Learn to rescue and reinstall you nVidia drivers, enough that it becomes second nature. Meaning, set your Grub2 menu so that you force it to display at least 1-2 seconds.

The reasons for this is that sometimes Linux kernel updates will boink your video driver, even with nvidia-dkms. It's much less often than it used to be, but still happens occasionally. Life happens when you don't plan for it. (-- John Lennon)

The easiest thing to do is to add 'nomodeset' to the kernel boot line, so that you can boot and reinstall your drivers... Or go to  rescue boot mode, enable networking, drop to a root prompt and do
```

apt remove nvidia-*

```
Then boot with 'nomodeset'... Then reinstall the driver.

Should you reset your DPi for your mouse settings? Yes. If it doesn't work to your satisfactions, you could always later do
```

sudo apt remove --purge ratbagd piper

```
remove it, and be back to where you are now.

I think you mis-understood, both AMD, Intel and nVidia work well with Linux. They do not play well **yet** with the Wayland graphics engine... Things are getting better, and they are trying to tweak it for gaming... Just not there yet. Intel and AMD have opened their drivers up to opensource and are included in the Linux Kernel. nVidia has been closed source / proprietary until very recently (within the past few weeks), where they just released their drivers as opensource for Linux Kernel 6.4. So I do not foresee that hitting Ubuntu until the HWE stack of 24.04 LTS.

---

### Post by tea for one on 2023-06-14
> **scott130 said:**
> So uh yeah I'm not using Wayland I'm using whatever is the default display server for Ubuntu
The default display server for Ubuntu 22.04 is Wayland.
You can check via the terminal:-
```
echo $XDG_SESSION_TYPE
```

---

### Post by TheFu on 2023-06-14
So, when replying, it helps to answer the questions AND prove your answer.  For example, you seem to think that X11 is the default for Ubuntu Desktop.  It wasn't when 20.04 was first shipped.  They backed it out for nvidia because the nvidia drivers/hardware didn't work well with Wayland, but for AMD/Intel, I think Wayland has been the default for some time.  It is possible that your system got confused and is trying to use Wayland.  So, please PROVE IT.  Guessing isn't good. We need facts that are proven.

Asking which display server is best is like asking which *color* is best.  It depends.
I'd rather use Wayland, but it doesn't handle all my workflows, so I don't.  I suspect it will be 8-10 yrs more before Wayland handles what I need.  I have time, as long as X11 is supported.  Lots of flavors don't use Wayland still, so Canonical is willing to not have some functionality that X11 has provided for 20+ yrs to gain some of the great things about Wayland - like better security and higher local GPU performance.  Performance is less important to my needs than solid network-agnostic program access.  I routinely run programs on other systems and have the window displayed on my current workstation. This is a way of life for me and has been for 30 yrs - before ssh existed.

Only you can decide which *color* is best for your needs.

---

### Post by SpaceManJack on 2023-06-15
So I switched from Nouveau to NVidia drivers and the mouse felt good but it's still not as good as on my 24inch monitor, what gives? Is it simply cause the 55inch screen is just too big? On the 24inch monitor the mouse feels perfect, but now that I've switched to the NVidia drivers the mouse feels better on the 55inch (but I do have to turn up the mouse speed in the settings) but the mouse movement just doesn't feel as smooth and accurate on the 55inch screen as it did on the 24inch. What gives?

Oh the Piper program can't even detect my mouse because I'm simply using a cheap $20 logitech mouse that I bought from Target a couple of years ago, it can't even detect my mouse lol. 

Is it possible a gaming mouse might make a difference here?

Also one final thing, I'm going to head over to the hardware section of this site and start a new thread there about AMD graphics cards because I'm thinking about just buying an AMD graphics card. Would an AMD graphics card fix my issue here? I know that Intel and AMD graphics cards work fine with Wayland, well ok, I know for a fact AMD graphics cards work fine with Wayland, not totally sure about Intel actually. So NVidia is closed source but AMD and Intel cards aren't?

p.s. Just to clarify, on the 55inch after I switched from Nouveau to NVidia drivers, the mouse movement felt better but I did have to go into settings and greatly turn up the mouse speed, but it's still just not perfect.

---


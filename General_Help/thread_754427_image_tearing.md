---
title: "image tearing"
date: 2008-04-13
forum: General Help
---

### Post by mike richards on 2008-04-13
hi ubuntuforums,

so i've had this issue with linux/xorg for a long time now (since i started using linux (3 years)). i get the same issue on 4 different systems. i've tried 3 different graphics cards, lcd monitor, crt monitor, both dvi and vga interfaces, and many distros and xorg versions. the problem persists on each configuration.

the issue im getting is, whats displayed on-screen is chopped up and teared. it almost looks like the screen is constantly progressive rendering each frame (from top to bottom) but very quickly, so its not very noticeable when doing suttle movements. but when theres faster movements on screen (like watching a video, moving a window quickly, or maximizing windows, etc..) it gets ugly, and you can see the tearing across the screen.

the the properties of my problem:
[LIST]
[*]its not application specific (like video or opengl). its everything in X. the tearing spans across the whole screen, no matter what applications.
[*]its nothing to do with my hardware, monitor, interface. (i've diagnosed each one, and all produce image tearing).
[*]it works fine in windows (full frames, no tearing). so its not a hardware issue.
[*]i have never used/seen a linux system wtihout this issue in person.
[*]have tried many combination of vsync, with no success.
[/LIST]
hopefully someone here knows about this issue. it cant be a coincidence that i've used 4 of the only systems that would produce this in linux. you guys must have had this. i cant possibly be the only one who notices this though. me and my buddy were starting to think that linux/xorg is just like this for everyone, its just the way it is.  i hope this is not the case. i mean i just bought a brand new lenovo, with intel x3100 and the opensource drivers that everyone seems to praise because of how well it works in linux. i was shocked to see that the issue still persisted.

here is an example. (dont mind the motion blur from the camera, just focus on the tearing, its pretty bad) [http://www.youtube.com/watch?v=xi_9zbwcA94]("http://www.youtube.com/watch?v=xi_9zbwcA94")

if you guys know of anything, or even why this happens. i would love to know. its been way to long, its just killing my eyes. thanks everyone.

---

### Post by mrsteveman1 on 2008-04-13
I think you're talking about screen tearing. I've noticed it on my HP laptop, which is a 945gm chipset, using both i810 and intel drivers on xorg.

It is, quite simply, a driver issue, one that i don't think they have resolved yet and i don't understand why. Intel supposedly provides direct support for these chipsets, and in fact releases drivers for them as well.

The same laptop running Vista, does not tear the screen anymore (it used to before one of the driver updates), and the same laptop running OS X has never had screen tearing at all.

I also have a mac mini, same situation, Linux drivers tear the screen, OS X doesn't.

---

### Post by mike richards on 2008-04-13
so you're saying its not only intel drivers right? its all video drivers in linux? because as i said i get the same issues with my nvidia 7800GT, an older ATI card, my friends 6800GT, aswell as my intel X3100.

---

### Post by mrsteveman1 on 2008-04-13
Since the people who work on the intel driver know about it, and said its a known issue they cant fix right now, perhaps its a limitation of x11? I've never liked X11 though i have few good reasons to hate it :D

---

### Post by mike richards on 2008-04-13
again.. like i said, its NOT only with intel. i have many systems and configurations here, with nvidia 7800GT, 6800GT, an old ati, etc.. all of them produce the same screan tearing. so it doenst have anything to do with intel.

and man.. i dont understand why everyone says their intel video works flawlessly in linux. its just the same as any other video in linux (crap). its dissapointing. after 3 years of using this garbage. i might consider returning my thinkpad and just buying a mac, with a real operating system.. its a shame though, since i like opensource and enjoyed using linux while i though this problem was fixable. but apparently thats just the way xorg is.. thats horrible..

and sorry for the rant. its just hard to believe..

---

### Post by trippinnik on 2008-04-13
If your using compiz try turning on vsync.  This used to be a major problem in 3d accelerated games.  There maybe a setting in xorg.conf to turn on vsync too, so you could try searching for that as well.

---

### Post by mike richards on 2008-04-13
again.. as i said its not application specific. for the record im not using compiz. but even if i have compiz enabled with vsync and everything, i still get the problem.

trippinnik, dont you have this problem also? i though that this is the way linux/xorg is.

i would love to see some evidence of a linux/xorg setup working with smooth, full-frames. as opposed to the tearing that i ALWAYS see in linux, regardless of the system.

---

### Post by Islington on 2008-04-13
can you post a screenshot/screencast of what this looks like? I haven't even heard of this problem.

---

### Post by mike richards on 2008-04-13
i bet you also have it you just dont really notice. move a black terminal over white wallpaper or something, and itll get more clear what im talking about. youll see horizontal tearing.

---

### Post by FuturePilot on 2008-04-13
Are you sure this isn't normal? You have to remember that Vista and OS X both use compositing, so of course there will be no tearing and everything will seem very smooth since you're drawing to a buffer. Without compositing you're pretty much drawing directly to the screen, so there's bound to be some tearing. Without Compiz I see some tearing around the edges of windows if I move them around very fast. Even in XP I see tearing if I move windows around fast.(XP=No composite) But it's very smooth with Compiz.

---

### Post by mike richards on 2008-04-14
thats relieving to hear. thanks. i hope you're right.. so now my problem has moved up a notch to something a little easier.

how can i get compiz to fix my issue? i still get tearing with compiz enabled, and even with the "sync to vblank" option enabled. any suggestions?

---

### Post by FuturePilot on 2008-04-14
I know if you have a Nvidia card there's 3 places you need to enable SyncToVblank. In CCSM  under General&#8594;Display Settings, and in nvidia-settings under Xserver Xvideo Settings and under OpenGL Settings
It also may help to add
```
 Option          "RenderAccel" "True"
        Option          "TripleBuffer" "True"

```
to the Device section in xorg.conf for Nvidia cards.

---

### Post by mike richards on 2008-04-14
i had an nvidia card in my old system, and i did try all of those, and each combination of them aswell. nothing seemed to work. right now though, im using an Intel X3100.
[URL="http://www.youtube.com/watch?v=xi_9zbwcA94"]
Here[/URL] is a short demo of the problem (forget the motion blur from the camera, just focus on the tearing, its pretty bad)

---

### Post by mrsteveman1 on 2008-04-14
I know its not related to the driver, im just saying the intel driver people specifically mentioned it in a notice i read one day, saying they knew about it and could do nothing to fix it, suggesting its X11 itself.

For the record though, I've noticed this on my laptop regardless of compiz or anything else.

I have managed to force OS X to tear the screen though, by turning off what they call beam sync, which i believe delays writes to match the screen refresh. Not sure if X11 does anything like that though.

BTW If you are already considering getting a mac i can't say how much i love mine :D theyre nice machines, and OS X is great.

---

### Post by izak on 2008-04-15
I've also noticed tearing on more than one Linux box. It usually occurs noticeably during video playback when there is a fast pan. Windows on screen move around all right, but video playback is not optimal.

---

### Post by ryth on 2008-04-15
I'm using a Radeon X1950 XT and noticed this (primarily when watching video).  It happened with both XGL+Compiz and without, as well  I happens with both VLC, Mplayer and Totem. I tried OpenGL and X11 in VLC and a few others but didn't notice that any of them improved the problem.  I sort of chalked this up to being an issue with the ATI drivers until I found this thread.  

It is quite annoying and REALLY not acceptable if you intend on using your linux box for home-theatre style things.  I mean i've become used to it, but that doesn't really make it okay.

Does anyone have any further insight into this perhaps?  there could be something we're missing maybe?

---

### Post by mike richards on 2008-04-15
i brought up the issue in #xorg and they were saying that its simply because X11 on its own redraws the screen instanstly without buffer. but with a composite extension, things get passed to a buffer and alow for full-frame output. 

this is the same as what i gather from FuturePilot. that both vista and mac os each have a hard-coded composite extension (Aero and Aqua, respectively), thus having a smoother, full-frame result out of the box. windows xp on the other hand did not, and therefor also had tearing issues. with a naked X11 though, you dont get any compositing, but rather have the choice of adding it (compiz, kwin, xfwm) to have things sent to buffer for a nicer result.

this makes sense to me, and i wish it was the case. but even with compiz enabled, and all forms of vsync, sync to vblank, i still get the same tearing issues. the framerate seems very nice, everything is smooth. i can tell that if there was no tearing it would be absolutely stunning. unfortunately it persists on all circumstances.

if you guys have any suggestions for me that would be great.

---

### Post by mike richards on 2008-04-16
anyone? it seems like a lot of people are having this same issue. no one knows of a solution? i simply cant work with it anymore, and it would be a pretty lame reason to switch to mac..

---

### Post by jongs on 2008-04-18
Sadly Mike, I'm in the same boat. No matter linux distro I use, Ubuntu, Sabayon, Mint, PCLOS, Mandriva I have the same problem.

My specs are:
Dell Inspiron 6400
Intel Dual Core 
Ati x1400 

But, I don't give up. I'm using linux for three years now and I still hope that in the near future my tearing problems will be solved.

---

### Post by mrsteveman1 on 2008-04-18
> I'm using linux for three years now and I still hope that in the near future my tearing problems will be solved.

Thats some serious loyalty :D

---

### Post by Batuhan on 2008-04-26
Ah, this was pretty much the only problem I had with ubuntu, yet a real showstopper, before I switched to macos.

As you said, everyone has this problem but very few actually care. When I was tinkering with the problem, I came to a point that I can enable vsync in opengl windows, but I had to disable compositing. So desktop would tear, but opengl content would be synced.

That, being cool, was not enough for me. Windows XP had the same problem from day one(they probably consider it as a feature) and now I'm using macos on my very same laptop(so it becomes a hackintosh) and it has no tearing issues. Everything is smoooooth. I'm gonna get a real mac soon.

Actually, why I came back tothe forum after months to look at the status of this issue is, if this was to be fixedsomehow, I might have considered going back to ubuntu, as I was very happy there too. But I'm also very happy on macos, and it has no tearing issues. Anyways, I'm wishing best of luck to you! This was one of my topics on the issue:

[http://ubuntuforums.org/showthread.php?t=570038](http://ubuntuforums.org/showthread.php?t=570038)

---

### Post by gruffy-06 on 2008-05-29
Isn't 60hz supposed to be 59.94hz, due to the nature of the signal?

---

### Post by occams_beard on 2008-07-03
> **mike richards said:**
> hi ubuntuforums,

 i mean i just bought a brand new lenovo, with intel x3100 and the opensource drivers that everyone seems to praise because of how well it works in linux. i was shocked to see that the issue still persisted.



Same problem here with tearing on the x3100- with or without compiz...  I also can't understand how everyone is praising the intel driver. Although, I too noticed tearing with Nvidia cards as well, so apparently people don't notice/care about screen tearing??  I just don't get it. Seems like this would be a top priority to fix, as it pretty much ruins all those pretty compiz effects.

Actually, this is the one thing that's keeping me from completely switching to Linux. As much as I loath Vista, one thing they got right was the display. Everything is silky smooth under Aero, with no tearing at all...

---

### Post by travelinman81 on 2008-07-16
I had this problem with compiz then I uninstalled it and built it from source and I have no more porblems I actually watch High resolution video with no problems. I notice on my poorer quality videos that they don't look as good as they did back in my window's days but, I think building compiz from source did the trick for me. Maybe I just don't notice it maybe I am just a big linux fanboy, maybe both. :confused:

---


---
title: "Love ubuntu but...."
date: 2006-11-27
forum: General Help
---

### Post by midna on 2006-11-27
Ok, I love ubuntu. Tried linux before finding ubuntu and it would never stick. Now, my main machine is ubuntu, my server is ubuntu, and any computer that just sits as a general use is ubuntu. :D I'm just missing some key apps/functionality that only seem to do well in other OS's.

First up, Dreamweaver. I love this utility, NVU just doesn't cut it. Quanta Plus works in a pinch, but I just love Dreamweaver. I've tried using it through wine and it never works right. The testing server, ftp, and main server integration is just wonderful. Any other alternatives? Any methods to making it work?

Second, uTorrent. This is more of a question as I have read that it runs fine in wine. Does the webui work ok while it runs in wine? What about running the uTorrent in wine with the webui enabled and still having a web server running on the same machine (so I can run jinzora).

Third, tv integration. My main ubuntu machine is my laptop for student use, but at times I like to connect it to my tv for viewing those wonderful commercial-free torrented television episodes. Currently the only method I have of doing that is restarting the xserver (ctrl+alt+backspace) after connecting the svideo cable. When its powering the tv however, my laptop screen gets all funkified (lines, bad refresh, etc), I think this is mostly just a problem with my laptop however as I have a zt3000 which likes a resolution of 1280x800 and a funky refresh rate which means I had to customize a line in the xorg.conf file. I have the ati drivers installed fine, but I would like a way to easily connect to the tv. Kinda how my friend's mac does it. He plugs the cables in, hits the detect displays button, and wala it works.

Fourth, and this is mostly nitpicky. I would love to have evdo card integration come standard in ubuntu instead of running a script to make it work. Just me being lazy.

Fifth, the ability to cancel the mandatory filesystem check after thirty boots, or at least the ability to push it back one boot. That way when I get to class, and boot the machine, I don't have to sit and wait while the machine checks itself, instead of taking notes](*,) . I can instead, push the check back one boot, take my notes, go to my room, reboot and walk away.

Sixth, a working hibernation/suspend setup. I give up on this again and again, but I would still love to have it.

Finally, a boot manager. I'm sure its there somewhere and I'm just a fool, but for the life of me I can't find the darn thing. I really don't need a torrent tracker running in my laptop for example, and I would love to speed the boot process up just a little bit. And add to it if need be for that matter.

Office isn't an issue as I have come to love open office. Gimp does most of what I needed in Photoshop. Amarok just kicks itunes/winamp's ***:mrgreen:. Automatix covered the rest of my needs just fine.

A long post I realize, but any idea's or help would be greatly appreciated. I don't mind solving my own problems as well, so if you know of a guide/article that solves a problem, just throw the link at me and I will give it a go.

---

### Post by kinson on 2006-11-27
> **midna said:**
> 
Second, uTorrent. This is more of a question as I have read that it runs fine in wine. Does the webui work ok while it runs in wine? What about running the uTorrent in wine with the webui enabled and still having a web server running on the same machine (so I can run jinzora).

Actualli I'm quite interested in this too. I'm a uTorrent user, and don't wanna switch to azureus in Ubuntu, and watch Azureus zap all all my memory/slow me system down :( At the very least, i'm hoping for something that will be a nice substitute for uTorrent in Ubuntu :p

Cheers,
Kinson

---

### Post by K.Mandla on 2006-11-27
> **kinson said:**
> Actualli I'm quite interested in this too. I'm a uTorrent user, and don't wanna switch to azureus in Ubuntu, and watch Azureus zap all all my memory/slow me system down :( At the very least, i'm hoping for something that will be a nice substitute for uTorrent in Ubuntu :p

Cheers,
Kinson
rtorrent works great for me. It runs via terminal window though, so for some it's too ugly to be a contender. :rolleyes:

---

### Post by kinson on 2006-11-27
> **K.Mandla said:**
> rtorrent works great for me. It runs via terminal window though, so for some it's too ugly to be a contender. :rolleyes:

I'm not too bothered about how it looks, but I'd honestly prefer a GUI, since it'd be easier to manage for a noob like me :P

But if its from the terminal, can the downloads resume? I mean, even after I've rebooted my pc or whatnot. (I ask the same for wget, can it resume too? :p )

Cheers,
Kinson

---

### Post by KuriKai on 2006-11-27
> First up, Dreamweaver. I love this utility, NVU just doesn't cut it. Quanta Plus works in a pinch, but I just love Dreamweaver. I've tried using it through wine and it never works right. The testing server, ftp, and main server integration is just wonderful. Any other alternatives? Any methods to making it work?
Dreamweaver is crap. I sugest using a text editor or notepad++ in wine

---

### Post by K.Mandla on 2006-11-27
So as not to stray off-topic. ...

> **midna said:**
> First up, Dreamweaver. I love this utility, NVU just doesn't cut it. Quanta Plus works in a pinch, but I just love Dreamweaver. I've tried using it through wine and it never works right. The testing server, ftp, and main server integration is just wonderful. Any other alternatives? Any methods to making it work?
The last I heard, nvu had become [KompoZer]("http://sourceforge.net/projects/kompozer"), but to be honest, I don't think it will aspire to the comprehensiveness of Dreamweaver any time soon. Check it out, though. It's always worth a look.

> **midna said:**
> Second, uTorrent. This is more of a question as I have read that it runs fine in wine. Does the webui work ok while it runs in wine? What about running the uTorrent in wine with the webui enabled and still having a web server running on the same machine (so I can run jinzora).
Sniff around for some other suggestions on torrent clients. Like I mentioned, rtorrent works for me, but there are plenty to choose from. Try searching packages.ubuntu.com for the word "torrent".

> **midna said:**
> Fifth, the ability to cancel the mandatory filesystem check after thirty boots, or at least the ability to push it back one boot. That way when I get to class, and boot the machine, I don't have to sit and wait while the machine checks itself, instead of taking notes](*,) . I can instead, push the check back one boot, take my notes, go to my room, reboot and walk away.
I know there's a way around this and for the life of me I can't find it now. ... No, wait. Is this what you want?

[http://www.ubuntuforums.org/showthread.php?t=295262](http://www.ubuntuforums.org/showthread.php?t=295262)

> **midna said:**
> Finally, a boot manager. I'm sure its there somewhere and I'm just a fool, but for the life of me I can't find the darn thing. I really don't need a torrent tracker running in my laptop for example, and I would love to speed the boot process up just a little bit. And add to it if need be for that matter.
Is [this]("http://www.ubuntuforums.org/forumdisplay.php?f=75") what you're looking for? What about [this]("http://ubuntuforums.org/showthread.php?t=89491")?

---

### Post by K.Mandla on 2006-11-27
> **kinson said:**
> But if its from the terminal, can the downloads resume? I mean, even after I've rebooted my pc or whatnot. (I ask the same for wget, can it resume too? :p )
Yebo yes. rtorrent does hash checks and resumes perfectly, even after reboots. Nice thing is, with no GUI to worry about, you can run rtorrent on a 200Mhz laptop (or slower, even) with no X. In other words, no background system load ... just the tty terminal and a network card. 

Wget ... does the same, I think. I very rarely use wget, unless I'm building something up from the CLI. And I don't think I've ever broken off a wget download. Now that you mention it, I shall have to try it. :mrgreen: I love breaking things. ...

---

### Post by kinson on 2006-11-27
> **K.Mandla said:**
> Wget ... does the same, I think. I very rarely use wget, unless I'm building something up from the CLI. And I don't think I've ever broken off a wget download. Now that you mention it, I shall have to try it. :mrgreen: I love breaking things. ...

Lol, i had to use it cause I haven't looked for a download manager for Ubuntu yet, and I needed to download the Xubuntu ISO for the other pc :p I'm certainly not trusting that to the firefox built in download manager :P

I'll look into that rTorrent thing, as long as it resumes it seems ok :) Hope it can handle multiple torrents though(I rarely go more than 4 torrents). I'll check it out when I get home.

Thanks again,
Kinson :)

---

### Post by K.Mandla on 2006-11-27
No problem. By the way, I've run like 16 or 20 torrents at a time on it. 

And if you want a sweet download manager for Firefox, try [this one]("https://addons.mozilla.org/firefox/201/"). I won't use anything else now.

---

### Post by kinson on 2006-11-27
> **K.Mandla said:**
> No problem. By the way, I've run like 16 or 20 torrents at a time on it. 

Cool, thanks :) btw, I think I've read in a couple of places that you shouldn't have more than 4 torrents running at the same time as it decreases the efficienty of the torrents. I don't understand the technical side of it, but thats what I've read :)

> 
And if you want a sweet download manager for Firefox, try [this one]("https://addons.mozilla.org/firefox/201/"). I won't use anything else now.

Thanks. I've got that installed on my Windows partition, but I honestly haven't tried it yet, ehehe. Been using Flashgot coupled with FlashGet in windows. I'll give it a try when I have sometime though, thanks for the suggestion :)

Cheers,
Kinson

---

### Post by K.Mandla on 2006-11-27
> **kinson said:**
> Cool, thanks :) btw, I think I've read in a couple of places that you shouldn't have more than 4 torrents running at the same time as it decreases the efficienty of the torrents. I don't understand the technical side of it, but thats what I've read :)
It's probably true. I did it to see how my wireless router would respond. It ground to a halt, of course, and I had to power the darn thing down before it would acknowledge anything but wired connections. :rolleyes:

---

### Post by kinson on 2006-11-27
> **K.Mandla said:**
> It's probably true. I did it to see how my wireless router would respond. It ground to a halt, of course, and I had to power the darn thing down before it would acknowledge anything but wired connections. :rolleyes:

Funny that it'd do that though :( I haven't heard of anything like that. Just not normally it slows down the other torrents, and I think it affects others in the swarm too. Never heard of anything regarding the router :s

Either way, as long as you got it working again, no worries right? ;)

Cheers,
Kinson

---

### Post by CatKiller on 2006-11-27
> **kinson said:**
> (I ask the same for wget, can it resume too? :p )

**wget -c**

From **man wget**:

>        **-c**
       **--continue**
           Continue getting a partially-downloaded file.  This is useful when
           you want to finish up a download started by a previous instance of
           Wget, or by another program.  For instance:

                   wget -c [ftp://sunsite.doc.ic.ac.uk/ls-lR.Z](ftp://sunsite.doc.ic.ac.uk/ls-lR.Z)

           If there is a file named _ls-lR.Z_ in the current directory, Wget
           will assume that it is the first portion of the remote file, and
           will ask the server to continue the retrieval from an offset equal
           to the length of the local file.

           Note that you don’t need to specify this option if you just want
           the current invocation of Wget to retry downloading a file should
           the connection be lost midway through.  This is the default behav&#8208;
           ior.  **-c** only affects resumption of downloads started _prior_ to this
           invocation of Wget, and whose local files are still sitting around.


---

### Post by kinson on 2006-11-27
> **CatKiller said:**
> **wget -c**

From **man wget**:

oooh. Muchos gracias ;)

I'll give it a try when I get home(assuming I can find the time today :( )

Cheers,
Kinson

---

### Post by CatKiller on 2006-11-27
Oh, and my preferred BitTorrent client is **btdownloadcurses**, since in conjuction with **screen** it is insanely good.

---

### Post by kinson on 2006-11-27
Lol, one thing I've noticed is that its a lot harder to find screenshots for linux programs,but I'm probably not searching enough(I'm at the office, just a quick scan :p )

Talking about screen and the linux terminal...If at the terminal I type "xmms" to launch xmms, then I can't enter anymore commands into that particular terminal without killing xmms? :| 
It seems to be processing whatever xmms is doing.

Cheers,
Kinson

---

### Post by CatKiller on 2006-11-27
If you put an & at the end of your command, you'll go back to the command line after the program is launched.

---

### Post by bailout on 2006-11-27
Have you tried ktorrent? I don't do much torrent downloading so I don't know really how it compares to other clients but it has worked well the times I have used it. If you do try it have search on these forums as I think someone here was doing some development on it and had some updated packages available.

---

### Post by AndyCooll on 2006-11-27
> **bailout said:**
> Have you tried ktorrent? I don't do much torrent downloading so I don't know really how it compares to other clients but it has worked well the times I have used it. If you do try it have search on these forums as I think someone here was doing some development on it and had some updated packages available.

This was going to be my suggestion too. I use KTorrent for all my torrent stuff. Handles multiple torrents, doesn't seem to take too much bandwidth etc.

:cool:

---

### Post by Patrick-Ruff on 2006-11-27
anyone notice that the origonal poster didn't post again? ;). anyways, I'm glad it's working out for these people, if I could get really good battery life in linux along with some better video performance (long story) I'd switch back right now. I'm actually considering it based on this, I'm really sick of windows vista using 377MB of ram 100% of the time.

anyways, good luck to you guys.

---

### Post by midna on 2006-11-27
I'm here, was just sleeping for the night (finally). Anyways, here's my input so far. 
Bonager was exactly what I was looking for, thank you K.Mandla.
The boot up threads look promising, well, more than promising. Thanks again K.Mandla. 
I'll definately give KompoZer a look. I'll post on my findings.

In the torrenting side of things, I really love my webui. I use it to access my torrenting machine (old pc at my house) from school which doesn't allow torrenting. Does rTorrent and/or KTorrent have a webui or similar function/plugin?

And to the router issues, I also have a similar problem if I have too many torrents try to run at once. Not really an issue for me since I just make use of the queuing system in utorrent.

Patrick, give edgy a try, I get great battery life with it. Better than windows in most cases. The video, well... I say "good game" to the video card manufactures and their "great" linux drivers.

---

### Post by kinson on 2006-11-30
> **bailout said:**
> Have you tried ktorrent? I don't do much torrent downloading so I don't know really how it compares to other clients but it has worked well the times I have used it. If you do try it have search on these forums as I think someone here was doing some development on it and had some updated packages available.

Cheers,
I've downloaded kTorrent and am running it now :)

I had some minor problems with trying to save the temp file in a fat partition, so I'm saving the temp somewhere else now.

Btw, any idea if there's a status light to let me know whether the port forward was successful? (ie. green ok, yellow NAT, red boo hoo) :p

Cheers
Kinson

---

### Post by ser1alsn1per on 2006-11-30
I have all of the macromedia studio 8 installed in wine and works a treet 

as for azureus zapping all the memory well not for me I had a look at ktorrent anywho which looked ok but havent used it yet 


also just a not on digg there was a new distribution called linux gobo with a filesystem kinda like apples im going to try it out and I suggets you do to just in vm ware like because ubuntu rocks

---

### Post by sgardne on 2006-11-30
> **K.Mandla said:**
> It's probably true. I did it to see how my wireless router would respond. It ground to a halt, of course, and I had to power the darn thing down before it would acknowledge anything but wired connections. :rolleyes:Some wireless routers have problems with not closing expired connections and after a while will lock up like that. Linksys wireless routers are a major culprit.

---

### Post by midna on 2006-11-30
> **ser1alsn1per said:**
> I have all of the macromedia studio 8 installed in wine and works a treet 

How did you do this?

---

### Post by underdog512 on 2006-11-30
> **midna said:**
> 
Second, uTorrent. This is more of a question as I have read that it runs fine in wine. Does the webui work ok while it runs in wine? What about running the uTorrent in wine with the webui enabled and still having a web server running on the same machine (so I can run jinzora).


Try Deluge. It is still in beta but I have never had any problems out of it.  Its also the fastest one I have seen. you can find it [Here]("http://deluge-torrent.org/"). They best way to install it is to add the repositories and install it through apt-get or synaptic.  lemme know if you need help with that.

---

### Post by sonicdevo on 2007-05-16
> **kinson said:**
> Actualli I'm quite interested in this too. I'm a uTorrent user, and don't wanna switch to azureus in Ubuntu, and watch Azureus zap all all my memory/slow me system down :( At the very least, i'm hoping for something that will be a nice substitute for uTorrent in Ubuntu :p

Cheers,
Kinson

I'm wondering if anyone ever found a solution for this?  I use some trackers which don't allow some of these Linux-native clients, so utorrent under WINE is my choice.  However, I'd love to use the WebUI.

EDIT: FYI I've found a solution to this over at the utorrent official forums.  It basically details where to place the "webui.zip" file.

---

### Post by midna on 2007-05-17
Currently I use kTorrent since its relatively good on my resources, has a webui, has rss functionality, and seems to work with all the trackers I use (private and public).

FYI this thread was almost 9 months old, I was just still subscribed to it for some reason..

---


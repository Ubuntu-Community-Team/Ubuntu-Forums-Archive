---
title: "The Linux/Flash problem"
date: 2013-09-11
forum: General Help
---

### Post by Extreedoc on 2013-09-11
I don't need to post here very often, my system works just fine except for: "The Flash problem"; I know that Adobe has withdrawn Linux support for Flash. This has caused me serious problems, I simply can't view most Youtube vids and I want to do an on-line course but the videos offered as part of the course are all Flash based, well, you can see my problem.

What I want to know is: is there a solution to this? If not, this is a deal breaker for me, I can't see any way out, other than to stop using Linux... _This, I do not want to do_, I really need your help and advice.

John

---

### Post by carl4926 on 2013-09-11
Install Google Chrome Browser
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

---

### Post by carl4926 on 2013-09-11
> **carl4926 said:**
> Install Google Chrome Browser
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

Ah, you're the 10.04 guy
Not sure how that would work out....

---

### Post by OmgItsPixelated on 2013-09-11
If these videos are on youtube, you could visit this link [www.youtube.com/html5]("http://www.youtube.com/html5") and avoid flash altogether.

---

### Post by Extreedoc on 2013-09-11
Thanks Guys, Carl: Yes, I'm stuck with an old distro because it is the most up-to-date one that my oldish computer will run, a new system is on the cards but not yet...
Omgits: thanks but HTML5 doesn't solve my problem, the vids still don't work. I get nothing, just a blank where the video should appear and in any case, I need to be able to watch Flash videos and not just on Youtube. (My course).

---

### Post by carl4926 on 2013-09-11
What about the FF extension Videodownload helper
Could you fetch the vids with that and watch in vlc?

---

### Post by ajgreeny on 2013-09-11
Does flash work at all for you, and what exactly do you mean by oldish computer; what is your hardware?

If you are stuck on 10.04 because you can't run unity, or because a non-pae kernel is a problem for you in 12.10 or 13.04, you could try something like Xubuntu 12.04 which is still available, I think with non-pae kernel.

If your cpu does not support sse2, meaning that flash version 11.2 is not working you can still get version 11.1, which should still work for you.  See [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") but if this si your situation, make sure you run flash-block or noscript add-on to keep security as tight as possible.

---

### Post by mastablasta on 2013-09-11
if computer can run 10.04 it can run Xubuntu 12.04. the desktop looks preety much the same.  Lubutnu 12.04 (or perhaps even better the LXLE) should run even better than your current 10.04.

furthermore i have an even older debian on one of the mashicnes and flash works just fine there.mashcine is really old (1,2Ghz) and with low memorry (224MB) yet i can watch youtube just fine. though not alway fullscreen due to slow CPU and low ram

---

### Post by Erik1984 on 2013-09-11
To find out if you have sse2 (in case of an old computer it's likely you don't)

```
cat /proc/cpuinfo | grep sse2
```

If nothing is returned your CPU does not have sse2.

---

### Post by carl4926 on 2013-09-11
> **Euroman said:**
> To find out if you have sse2 (in case of an old computer it's likely you don't)

```
cat /proc/cpuinfo | grep sse2
```

If nothing is returned your CPU does not have sse2.
Some get a reasonable work around to this by using flash 10.3

---

### Post by ajgreeny on 2013-09-11
> **carl4926 said:**
> Some get a reasonable work around to this by using flash 10.3

Better to use flash 11.1, surely as shown in my post #7, or is there a good reason for flash 10.3; is it more secure than11.1?

---

### Post by Extreedoc on 2013-09-11
> **ajgreeny said:**
> Does flash work at all for you, and what exactly do you mean by oldish computer; what is your hardware?

If you are stuck on 10.04 because you can't run unity, or because a non-pae kernel is a problem for you in 12.10 or 13.04, you could try something like Xubuntu 12.04 which is still available, I think with non-pae kernel.

If your cpu does not support sse2, meaning that flash version 11.2 is not working you can still get version 11.1, which should still work for you.  See [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") but if this si your situation, make sure you run flash-block or noscript add-on to keep security as tight as possible.

I have a 1.6GHz processor and 1.2 GiB memory, the computer is at least 6 years old, possibly more. 
I know about downgrading to an earlier version of Flash but there are security issues and I am not techy enough to do it, anyway.

From the answers I've received so far it sounds like there isn't a real solution to this problem, just work-arounds, am I right?

Is Flash working on newer distros and is this likely to become a problem for them also?

---

### Post by ajgreeny on 2013-09-11
What cpu do you have?  Many of the older AMD processors do not have sse2 capability and that was my problem for my old desktop with a Sempron 2400+ cpu.  I used the flash 11.1 workaround which I mentioned earlier, and it is really not difficult to do; just follow the info on that page to extract the libflashplayer.so file from the archive and put it in the hidden ~/.mozilla/plugins folder.  Simple and effective, and if you have a non sse2 cpu, it is your only option.

---

### Post by Extreedoc on 2013-09-11
I think you have hit the nail on the head AJ, I have an AMD Athlon CPU.

I'm sorry to see that this is my only option though, to my mind it shouldn't be a necessity to take a backwards step in order to keep things working properly. I'm wondering if this withdrawal of support from Adobe could signal the beginning of the end for Linux unless a programmer can write a new, direct replacement for Flash. It seems pretty big and serious.

---

### Post by Erik1984 on 2013-09-11
Chrome still gives you an updated Flash for Linux (11.8.something). see this page: [http://www.adobe.com/nl/software/flash/about/](http://www.adobe.com/nl/software/flash/about/) So for Linux in general it's not over for Flash.

---

### Post by kurt18947 on 2013-09-11
The current flash version in the repositories gets security updates from Adobe until something like 2017.  I haven't run into anything flash related that doesn't work with that flash version, most sites require version 10.x for video.  Games may be a different story.  Mozilla is working on something called Shumway.  I installed it and for sites that support it, you'd never know it wasn't Adobe flash.  As others have said, Chrome or there's a ppa around to install pepper flash on Chromium.  The lack of current flash may be a pain but I've never noticed any issues with the 11.2xxx whatever.  I had an AMD Athlon single core setup that had a real problem with flash so yeah, that could be an issue. Even a dual core Athlon II X2 runs about 50% on each core playing a flash video the last time I checked.  Flash is a pig but I'm sure it'll be around a lot longer than we'd prefer due to inertia.

---

### Post by ajgreeny on 2013-09-11
However that version of flash in chrome will still not work with your Athlon cpu, I'm afraid. I tried that with my Sempron but still no-go, which was very disappointing.

You say "**to my mind it shouldn't be a necessity to take a backwards step in order to keep things working properly.**" but in fact that is nothing new; there has always been a problem with software overtaking the ability of hardware, and this is just another example of that.

Progress, I'm afaid!

---

### Post by Extreedoc on 2013-09-11
> **ajgreeny said:**
> 
You say "**to my mind it shouldn't be a necessity to take a backwards step in order to keep things working properly.**" but in fact that is nothing new; there has always been a problem with software overtaking the ability of hardware, and this is just another example of that.

Not quite the same thing though AJ, this is more a case of a major software company throwing a strop and depriving us of an essential piece of software, if I understand what has happened correctly.

No one has yet answered my question: Does the latest distro of Ubuntu work with Flash videos ok, no issues at all?

---

### Post by Erik1984 on 2013-09-11
You can't say that in general. On my hardware Flash works fine with 13.04 and Firefox 23. Yeah I'm on Kubuntu not Ubuntu but that shouldn't make a difference for Flash comatability.

---

### Post by carl4926 on 2013-09-12
> **Extreedoc said:**
> 

No one has yet answered my question: Does the latest distro of Ubuntu work with Flash videos ok, no issues at all?

If you combine your options of Firefox + Google Chrome, it's 99% OK

---

### Post by craig10x on 2013-09-12
Why can't you use Google Chrome on there?  (i don't mean chromium)  Chrome (which you get from google's website) has pepper flash...you see , although Adobe no longer supplies newer flash versions for linux directly (last one was over 2 years ago and it only gets security updates now) they have an agreement with Google to provide the latest flash for Chrome for all platforms (Windows/Mac/Linux)....using that you should have no problem with you tube videos and other flash on the web...

---

### Post by Mephisto Pheles on 2013-09-12
If you go to youtube, click a video page, load it and let the player load... then right click on the player to determine if it is the flash player or the html5 player.
If it doesn't say anything like "About Adobe Flash Player XX.XX", the last item in the right click menu, then it is the html5 player. You can barely tell the difference.
I had problems with html5 not with flash, so I opted out.. and flash works fine on Mint and on Xubuntu both 12.04.
 On an AMD Sempron 64 bit box of over 8 years old!

Depending on your browser youtube **automatically** will opt you in on their html5 trial.
 You have to opt out of html5, not opt-in nowadays.
I've seen many people report flash problems while they were actually on html5 trial.
On Windows as much as on Linux.

Since I run a video site myself this was of course crucial. I would never have switched to Linux if Flash didn't work properly.

> The HTML5 Opt-in / Opt-out page is at:
[www.youtube.com/html5]("http://www.youtube.com/html5")
at the bottom of the page where it says:  "Join" or "Leave".  If you think that you seem to be enrolled in the trial, but the HTML5 page states otherwise, then you can try Joining and then Leaving the trial, followed by going back to a video and refreshing your browser page.
When all else fails, it never hurts to completely clear your browser cache and cookies both.

FYI I'm using Opera as my main browser. Like several people said before, if security is an issue for you use Chrome, as their Flash player is updated more frequently.

---

### Post by Extreedoc on 2013-09-12
I'm willing to try Chrome but opinion seems divided as to whether it will work on my system; AJ says it will not. Perhaps I'd better just try and get back to you all. Thanks to all for your advice so far.

---

### Post by Extreedoc on 2013-09-12
Ok, I've tried to install Chrome and I get the message: "Error: Dependency is not satisfiable: geonf service.

---

### Post by ajgreeny on 2013-09-12
> **Extreedoc said:**
> Ok, I've tried to install Chrome and I get the message: "Error: Dependency is not satisfiable: geonf service.

That's a new one on me.  Are you sure it wasn't "**gconf** service"?

For clarification purposes can you also show us the output of the command suggested earlier to see if your cpu is sse2 enabled ```
cat /proc/cpuinfo | grep sse2
``` If there is no output from that your cpu will not be able to use the pepperflash from Chrome, or it is unlikely, assuming sse2 is still needed by the new version.

---

### Post by Mephisto Pheles on 2013-09-12
I just checked your previous posts your system is faster than my old Sempron 3000, if you're running ubuntu you might want to consider switching to xubuntu 12.04.3. Your desktop manager might be draining too much of your power...
XFCE is a lot lighter on your system.

As for the dependency problem, no idea, somebody else will help you with that I guess

And please go to youtube and check if it is the flash player that is giving you problems or whether you're on the html5 trial.
 As I said html5 doesn't work for me, well it works, it just stops and stutters all the time. Flash works fine. Before you try to solve a problem make sure you know what the problem is.

By the way AMD Athlon 64 is supposed to have SSE2
[http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2)

 I think you're giving up to soon ;)

---

### Post by Extreedoc on 2013-09-12
> **ajgreeny said:**
> That's a new one on me.  Are you sure it wasn't "**gconf** service"?

For clarification purposes can you also show us the output of the command suggested earlier to see if your cpu is sse2 enabled ```
cat /proc/cpuinfo | grep sse2
``` If there is no output from that your cpu will not be able to use the pepperflash from Chrome, or it is unlikely, assuming sse2 is still needed by the new version.

This is how non techy I am: I can't get the command to paste into terminal; I select the text and Ctrl C but when I Ctrl V it's not there. What is more I can't type it in by hand because I can't make that vertical line symbol, can't figure out what I'm doing wrong...

Your first question: Yes, it probably was gconf, I must have miss-read it.

---

### Post by Extreedoc on 2013-09-12
> **JkbrrLJ said:**
> I just checked your previous posts your system is faster than my old Sempron 3000, if you're running ubuntu you might want to consider switching to xubuntu 12.04.3. Your desktop manager might be draining too much of your power...
XFCE is a lot lighter on your system.

As for the dependency problem, no idea, somebody else will help you with that I guess

And please go to youtube and check if it is the flash player that is giving you problems or whether you're on the html5 trial.
 As I said html5 doesn't work for me, well it works, it just stops and stutters all the time. Flash works fine. Before you try to solve a problem make sure you know what the problem is.

By the way AMD Athlon 64 is supposed to have SSE2
[http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2)

 I think you're giving up to soon ;)

Xbuntu? Fair comment, I'll bear it in mind if all else fails.

Your suggestion regards Youtube: I am on the HTML5 trial and I've tried opting out from it, same result. When I click on a video, nine times out of ten, the video screen goes black, no play/pause or progress bar at the bottom. When I move the cursor, the black screen goes white. No sound, no video. Sometimes I get Flash videos sent to me, these don't work either.

My CPU is 32 bit, not 64.

---

### Post by Erik1984 on 2013-09-12
> **Extreedoc said:**
> This is how non techy I am: I can't get the command to paste into terminal; I select the text and Ctrl C but when I Ctrl V it's not there. What is more I can't type it in by hand because I can't make that vertical line symbol, can't figure out what I'm doing wrong...

Your first question: Yes, it probably was gconf, I must have miss-read it.

You can paste commands in the terminal by right clicking with the mouse (on the position of the cursor) and select paste from the menu that pops up. Another key combination for pasting (from the dark ages of computing :P) is SHIFT + INSERT. CTRL + SHIFT + V also works.

---

### Post by ajgreeny on 2013-09-12
> **Extreedoc said:**
> This is how non techy I am: I can't get the command to paste into terminal; I select the text and Ctrl C but when I Ctrl V it's not there. What is more I can't type it in by hand because I can't make that vertical line symbol, can't figure out what I'm doing wrong...

Your first question: Yes, it probably was gconf, I must have miss-read it.

Just highlight the etxt with your mouse then middle click your mouse when in terminal for a quick paste of the copy-buffer; that is one of the tricks in linux that I don't remember working in windows.

Alternatively just **right click ->copy/paste** in terminal to do the same thing.  Generally in terminal you need **Ctrl+Shift+C** or V because Ctrl+C is already allocated to cancel a command, not copy.

---

### Post by Extreedoc on 2013-09-12
Thanks both, Ok then, I entered the text in Terminal and pressed enter and there was no result... Unless I've screwed up again does that answer your question AJ, no SSE2? So, no go with Chrome?

---

### Post by ajgreeny on 2013-09-12
I'm afraid that as you say, the pepperflash in Chrome will still not work if you have a non sse2 cpu, so I think you are stuck with an earlier version of flash, 11.1 from my previous link..

---

### Post by Extreedoc on 2013-09-12
Ok, I'll have to read up on it. Thanks AJ

---

### Post by Extreedoc on 2013-09-13
I have bitten the bullet and downloaded the earlier version of Flash, made a Plugins folder in Mozilla in my Home file and dragged the Libflashplayer.so into it. What now? Youtube vids just the same. Typing "about:plugins" into Firefox address bar shows the newer version of Flash, so, do I have to go into the synaptic and get rid of the newer version of Flash? The older version is not showing in the synaptic, is this to be expected? How do I get the computer to recognise the older Flash and ignore the newer version?

Edit: Sorry, don't know where that smiley came from, I didn't put it there...

---

### Post by carl4926 on 2013-09-13
The version of firefox isn't the issue. It's the flash-plugin.
Even if you get the variable correct, I think it's likely that you'll encounter issues with sites complaining back at you about your old flash-plugin. So it's catch22

---

### Post by ajgreeny on 2013-09-13
Yes, I suggest you use synaptic to remove the newer flash version from the system as otherwise it will continue to be updated, though I am surprised that you are having problems getting the older version to work and I am wondering if you were confused about where to put the libflashplayer.so file, as you talk about a Mozilla folder, not the hidden .mozilla folder, in your home.

I presume that you did not make a Mozilla/Plugins folder and that when you moved the libflashplayer.so it was to the newly made plugins folder in the hidden ~/.mozilla in your home.  Also can you confirm that you have closed and restarted firefox?  If not, try restarting firefox after removing any flash apps with synaptic.  Normally the plugin file in your own home ~/.mozilla/plugins folder takes precedence over the system folder versions, so your outcome is very different from what I expected.

EDIT:
Sorry, the folder to move the libflashplayer.so file to should be **~/.mozilla/plugins**, all in lower case, not ~/.mozilla/Plugins.  I have edited my original to put it right.

My mistake and it may be why you're seeing the problem with the older version not working. Apologies if that's the case; a slip of the fingers/keyboard.

---

### Post by Extreedoc on 2013-09-13
> **ajgreeny said:**
> Yes, I suggest you use synaptic to remove the newer flash version from the system as otherwise it will continue to be updated, though I am surprised that you are having problems getting the older version to work and I am wondering if you were confused about where to put the libflashplayer.so file, as you talk about a Mozilla folder, not the hidden .mozilla folder, in your home.

I presume that you did not make a Mozilla/Plugins folder and that when you moved the libflashplayer.so it was to the newly made plugins folder in the hidden ~/.mozilla in your home.  Also can you confirm that you have closed and restarted firefox?  If not, try restarting firefox after removing any flash apps with synaptic.  Normally the plugin file in your own home ~/.mozilla/plugins folder takes precedence over the system folder versions, so your outcome is very different from what I expected.

EDIT:
Sorry, the folder to move the libflashplayer.so file to should be **~/.mozilla/plugins**, all in lower case, not ~/.mozilla/Plugins.  I have edited my original to put it right.

My mistake and it may be why you're seeing the problem with the older version not working. Apologies if that's the case; a slip of the fingers/keyboard.

Hi AJ, thanks for coming to my rescue again; to confirm: I am talking about the hidden ".mozilla" file, (Ctrl H); there wasn't a plugins folder in it so I made one. I downloaded the tar.gz file to the desktop then "copied" it to the .mozilla file, opened it and dragged the .so file into the plugins folder. I called the folder "plugins", I hope that is ok? I did make the mistake of calling it Plugins at first but I have changed that now, (thank you). By the way, should I now delete the downloaded file, (tar.gz) from the .mozilla folder or will it sit there happily and not cause a problem?

I didn't have Firefox running at the time of doing all this so I just started it as normal, will that suffice?

Regards the Flash entries in the synaptic: should I remove all mention of Flash? I think there are a couple of entries.

Tomorrow I will follow your instructions and see what happens.

Thanks again, John.

---

### Post by Yellow Pasque on 2013-09-13
Not sure if minitube package is still functioning on 10.04/Lucid, but that may be an option.

---

### Post by D8r4bwQ on 2013-09-13
Folks,
Maybe this will help. I just saw this thread as I was looking for similar solutions to make flash work on my little old HP netbook using FireFox 23. (new Xubuntu 13.04 installation)  First I installed the "flash plugin installer" via the Ubuntu software center, but couldn't figure out where it was or how to use it.  Then I remembered the installation I did just a few weeks ago on my desktop (64-bit Xubuntu 13.04).  I recalled that I had installed "gstreamer ffmpeg video plugin" also via software center.  Did the same for the netbook and "Voila" flash works.  Tried it on YouTube and other sites and made sure audio worked, too, before sending this.

I really don't know if gstreamer was what did the trick - but it seemed to have worked for me.  Please give feedback.

XubunTed
RH Linux --> Ubuntu --> Lubuntu --> Mint XFCE --> Xubuntu (Home Sweet Home!)
Still using various versions of Ubuntu, Lubuntu, and Mint (in combination) on three other computers.
Primary: Asus M4A785-M; AMD Phenom 9850 Quad; 4GB 6400 DDR2; 64-bit Xubuntu 13.04
HP Netbook 1030NR: _16GB SSD, 1GB RAM_, 32-bit Xubuntu (SO much faster than it's original WinXP !!!)

---

### Post by Yellow Pasque on 2013-09-13
> I really don't know if gstreamer was what did the trick - but it seemed to have worked for me. Please give feedback.
I doubt gstreamer0.10-ffmpeg suddenly make flash work. Also, if you're talking about the netbook in your sig, it supports SSE2 and latest versions of flash, so it's not relevant to the OP's system :\

---

### Post by Extreedoc on 2013-09-14
Ok then, I think I can claim a partial success; some videos work and some still don't. I've uninstalled the Flash elements in the synaptic and here I am... On typing "about:plugins" in the Firefox address bar, I'm finding two versions of Flash show up: Shockwave Flash 11.2 r202 and: Shockwave Flash 11.1 r 102, (this last, the one I've just downloaded and installed.

Edit: There's that damn smiley again!

---

### Post by haresear on 2013-09-14
> **Extreedoc said:**
> Ok then, I think I can claim a partial success; some videos work and some still don't. I've uninstalled the Flash elements in the synaptic and here I am... On typing "about:plugins" in the Firefox address bar, I'm finding two versions of Flash show up: Shockwave Flash 11.2 r202 and: Shockwave Flash 11.1 r 102, (this last, the one I've just downloaded and installed.

Edit: There's that damn smiley again!

You might need to go to Firefox->Tools->Addons->Plugins and disable the new version of Flash and enable the old version.

As an asside, I'm running a Sempron 2400 CPU without sse2, and in spite of that Flash 11.2 r202 does actually run in Firefox -- but Firefox fills up my disk with Pending Crash Reports whenever Flash 11.2 runs, so I've disabled it.

---

### Post by ajgreeny on 2013-09-14
> **Extreedoc said:**
> Ok then, I think I can claim a partial success; some videos work and some still don't. I've uninstalled the Flash elements in the synaptic and here I am... On typing "about:plugins" in the Firefox address bar, I'm finding two versions of Flash show up: Shockwave Flash 11.2 r202 and: Shockwave Flash 11.1 r 102, (this last, the one I've just downloaded and installed.

Edit: There's that damn smiley again!
You must still have a flash package installed through the normal system methods, so check again in synaptic to make sure.  If it does not show anything I suggest you find the pathway to the newer plugin file with command ```
locate libflashplayer.so
```It should show two versions; the one you just put in ~/.mozilla/plugins and one other, probably somewhere like /usr/lib/adobe-flashplugin/libflashplayer.so which you can either delete for the moment with sudo rm /usr/lib/adobe-flashplugin/libflashplayer.so or just rename as  a backup file.

"That damn smiley" as you call it, has to be turned off by using Advanced text input, for each posting you make with a : between particular letters, and I also find them annoying.  Regrettably there is no way I know of to turn them off in your personal forum profile for all your posts.

---

### Post by Extreedoc on 2013-09-14
Thanks AJ, I found the offending versions with the "locate" command but can't find them among the files, I can find the "usr" and the "lib" folders but the files themselves aren't there. So, I did as Haresear suggested and went to Firefox>Tools>Plugins and disabled the sucker there. I'll report back when I've tested it again.

By the way, Vimeo videos don't work at all... might be useful info(?)

---

### Post by Extreedoc on 2013-09-14
Well that seems to have fixed it!! Videos that didn't work before now work fine. Only problem so far is I keep getting warned that the plugin is vulnerable and I should update it. This I did expect but how serious is this? If I update I'll end up with the version that doesn't work won't I? I should probably add "Noscript" but even so, how do I know what to allow and what to block?

PS. Vimeo videos work but picture is jerky.

---

### Post by deadflowr on 2013-09-14
> **Extreedoc said:**
> Not quite the same thing though AJ, this is more a case of a major software company throwing a strop and depriving us of an essential piece of software, if I understand what has happened correctly.

No one has yet answered my question: Does the latest distro of Ubuntu work with Flash videos ok, no issues at all?

They didn't stop, they chose sides. In this case they chose Google-Chrome.

I've had no issues with either flash running in firefox, or google-chrome's pepperflash.(though from time to time chrome's updates have broken pepperflash, which usually gets a fix fast)
This is across multiple PCs running distros from precise to saucy.
One of the first things I do when installing a new Ubuntu on any PC is try out flash on some site that uses flash.

---

### Post by ajgreeny on 2013-09-14
> **Extreedoc said:**
> Thanks AJ, I found the offending versions with the "locate" command but can't find them among the files, I can find the "usr" and the "lib" folders but the files themselves aren't there. So, I did as Haresear suggested and went to Firefox>Tools>Plugins and disabled the sucker there. I'll report back when I've tested it again.

By the way, Vimeo videos don't work at all... might be useful info(?)

Glad you got it working!

It is possible that the old flash plugin file was showing simply as a result of not having updated the system file database with ```
sudo updatedb
``` but I suspect if firefox can still see the old one in the **about:plugins** page, that it really is still installed.  I have no idea why you can not find it if that's the case.

---

### Post by Extreedoc on 2013-09-15
Can anyone advise me about the "vulnerability" issue? It makes me feel uncomfortable about ignoring the warning...

PS. Just run the plugins search again and it is now ok, just the one we want is showing... maybe I should have re-started the computer to make the others clear out.

---

### Post by carl4926 on 2013-09-15
> **Extreedoc said:**
> Can anyone advise me about the "vulnerability" issue? It makes me feel uncomfortable about ignoring the warning...

PS. Just run the plugins search again and it is now ok, just the one we want is showing... maybe I should have re-started the computer to make the others clear out.

Obviously the old flash player you are using is outdated with no up to date security patches.
So is it a risk - Obviously

What about running a windows based version of FF or other browser in wine? I never tried that, but it may be an option? You should be able to use the latest flash in there. And it locks everything in to .wine

---

### Post by Extreedoc on 2013-09-15
> **carl4926 said:**
> Obviously the old flash player you are using is outdated with no up to date security patches.
So is it a risk - Obviously

What about running a windows based version of FF or other browser in wine? I never tried that, but it may be an option? You should be able to use the latest flash in there. And it locks everything in to .wine

Thanks for this Carl; the problem with wine is that it leaves you open to Windows based vulnerabilities as far as I'm aware. I wonder what others think about this?

---

### Post by vasa1 on 2013-09-15
> **Extreedoc said:**
> ...
Edit: There's that damn smiley again!
Yes, that happens sometimes with a combination of characters being interpreted as a smiley. To avoid that, one has to remember to tick the **disable smilies in text** in the **Additional Options** found below the area where we type our post.

---

### Post by Extreedoc on 2013-09-15
Thanks Vasa :p (!)

---

### Post by Yellow Pasque on 2013-09-15
> **Extreedoc said:**
> Can anyone advise me about the "vulnerability" issue?
> Only problem so far is I keep getting warned that the plugin is vulnerable and I should update it.
Be more specific. What is giving you these warnings? Youtube? The add-ons tab?
If it makes you feel any better, even folks using the latest Linux plugin available for Firefox (11.2.202.310 at the moment) will receive a "vulnerable" warning even though Adobe updates the plugin for security issues.

---

### Post by Extreedoc on 2013-09-15
> **Temüjin said:**
> Be more specific. What is giving you these warnings? Youtube? The add-ons tab?
If it makes you feel any better, even folks using the latest Linux plugin available for Firefox (11.2.202.310 at the moment) will receive a "vulnerable" warning even though Adobe updates the plugin for security issues.

Youtube, Vimeo and the plugins tab.

I've never received such a warning before when I was struggling with the newer versions.

---

### Post by haresear on 2013-09-15
Firefox gives the warning if Flash 11.1 is enabled, and even "deactivates" it automatically. A mouse click is needed to activate it for every visit to a website using Flash. This seems like the best solution for those of us with older AMD CPUs.

---

### Post by Extreedoc on 2013-09-16
> **haresear said:**
> Firefox gives the warning if Flash 11.1 is enabled, and even "deactivates" it automatically. A mouse click is needed to activate it for every visit to a website using Flash. This seems like the best solution for those of us with older AMD CPUs.

Yes, this is what I'm getting. I'll have to live with it then.

Thanks to all who have helped, I'll call this thread "solved".

---

### Post by Yellow Pasque on 2013-09-16
You could try the Flashblock add-on to minimize the warnings.

---

### Post by ajgreeny on 2013-09-16
As I said in a previous post try double clicking on the **plugins.hide_infobar_for_outdated_plugin** line in about:plugins to toggle that on to true.  That should stop the warnings from appearing.  I don't think it will stop sites from totally blocking use of an outdated plugin, but I don't think I have ever been to one of those, so can't really comment.

---

### Post by Extreedoc on 2013-09-16
> **ajgreeny said:**
> As I said in a previous post try double clicking on the **plugins.hide_infobar_for_outdated_plugin** line in about:plugins to toggle that on to true.  That should stop the warnings from appearing.  I don't think it will stop sites from totally blocking use of an outdated plugin, but I don't think I have ever been to one of those, so can't really comment.

Hi AJ, This line should be on the about:plugins page? I've just been there and I can't find it.

---

### Post by kurt18947 on 2013-09-16
> **Extreedoc said:**
> Hi AJ, This line should be on the about:plugins page? I've just been there and I can't find it.

Not AJ but check in 
```
about:config

```
then search for "plugins.hide_infobar" and you should find that line.

---

### Post by Extreedoc on 2013-09-17
Thanks Kurt, done and done!! I feel a test coming on...

Edit: Ok, test completed: another partial success, some videos are warning free and others aren't but I'm satisfied.

Thanks again folks.

---

### Post by ajgreeny on 2013-09-18
> **Extreedoc said:**
> Hi AJ, This line should be on the about:plugins page? I've just been there and I can't find it.

Whoops!

My fingers were working faster than my brain that time; I did mean about:config but was also thinking about various plugins in the named config line and it all went to worms.

Sorry about that.

---

### Post by Extreedoc on 2013-09-18
> **ajgreeny said:**
> Whoops!

My fingers were working faster than my brain that time; I did mean about:config but was also thinking about various plugins in the named config line and it all went to worms.

Sorry about that.

AJ, you have been a star, thanks for the help and don't worry about a minor error... ):P

---

### Post by psfal on 2013-09-20
> **carl4926 said:**
> Some get a reasonable work around to this by using flash 10.3

I have the same problem with an old desktop that is still quite capable of running 12.04 32bit, but doesn't have SSE2, I won't use FF or any of it's derivatives because they're slow, I don't use the machine because of this issue, how would I install flash 10.3? I only use Chromium or Chrome as a browser

---

### Post by haresear on 2013-09-20
> **psfal said:**
> I have the same problem with an old desktop that is still quite capable of running 12.04 32bit, but doesn't have SSE2, I won't use FF or any of it's derivatives because they're slow, I don't use the machine because of this issue, how would I install flash 10.3? I only use Chromium or Chrome as a browser
You just need to get a copy of 'libflashplayer.so' for Flash version 10.3 and put it in the subdirectory under your home: ~/.mozilla/plugins/

---

### Post by haresear on 2013-09-20
> **ajgreeny said:**
> Better to use flash 11.1, surely as shown in my post #7, or is there a good reason for flash 10.3; is it more secure than11.1?

Perhaps Flash 10.3 is more secure -- it has a date of 23 May 2013 on the Adobe website, and Firefox does not deactivate it or issue warnings when using it (like it does for 11.1).

---

### Post by carl4926 on 2013-09-21
> **carl4926 said:**
> Some get a reasonable work around to this by using flash 10.3
Which I did already mention....
[http://ubuntuforums.org/showthread.php?t=2173741&p=12785637#post12785637](http://ubuntuforums.org/showthread.php?t=2173741&p=12785637#post12785637)

---

### Post by haresear on 2013-09-21
> **carl4926 said:**
> Which I did already mention....
[http://ubuntuforums.org/showthread.php?t=2173741&p=12785637#post12785637](http://ubuntuforums.org/showthread.php?t=2173741&p=12785637#post12785637)

So is 10.3 more secure than 11.1?

---

### Post by carl4926 on 2013-09-21
> **haresear said:**
> So is 10.3 more secure than 11.1?

No idea
I wouldn't really ever describe flash as being secure.

---

### Post by Extreedoc on 2013-09-22
> **haresear said:**
> Perhaps Flash 10.3 is more secure -- it has a date of 23 May 2013 on the Adobe website, and Firefox does not deactivate it or issue warnings when using it (like it does for 11.1).

What we need here is a definitive answer to this question... anybody?

---


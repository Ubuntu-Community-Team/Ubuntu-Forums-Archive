---
title: "Netflix Desktop not working anymore"
date: 2012-11-20
forum: General Help
---

### Post by colobix on 2012-11-20
Hello. Today I tried netflix desktop on ubuntu, and it tells me to upgrade silverlight. This froze the whole thing and I can only hear the audio. Any idea how to fix this or if it's even possible?
Is there something I can to to let firefox not see the newer silverlight version?

---

### Post by coldcritter64 on 2012-11-20
You could try with Moonlight (the linux equivalent of Silverlight for MS). Silverlight is designed for Windows. I have no idea though how good/useful Moonlight is.

I have read recently where some users have had luck running netflix in firefox under Wine. Another possibility maybe.

---

### Post by colobix on 2012-11-20
> **coldcritter64 said:**
> You could try with Moonlight (the linux equivalent of Silverlight for MS). Silverlight is designed for Windows. I have no idea though how good/useful Moonlight is.

I have read recently where some users have had luck running netflix in firefox under Wine. Another possibility maybe.
That's the tweak that doesn't work anymore.
The whole reason why netflix doesn't work under linux is because of silverlight. And now when silverlight has been upgraded, not even the new wine tweak works.
I can't believe people hyped this thing up like crazy though.
I mean, it was just a matter of time before this would happen.
Too bad it happened only 2 days after they made Netflix Desktop.
Coincidence? Nah, Microsoft hates it when you can use their products on other platforms. Especially their free products that'll make people switch over to linux:)

---

### Post by rai4shu2 on 2012-11-20
I think it's safer to chalk this up to a Wine issue. The Wine + Silverlight patch was always an iffy beta type of thing to begin with. I would say wait for proper support for Silverlight under Wine, and this issue should go away.

---

### Post by philinux on 2012-11-20
Moonlight is dead in the water. Development stopped ages ago. They couldn't keep up with silverlight versions anyway.

---

### Post by weasel fierce on 2012-11-20
It's still working here. Try running the firefox.exe with wine directly, rather than the desktop app and see if it that makes any difference?

---

### Post by colobix on 2012-11-20
> **weasel fierce said:**
> It's still working here. Try running the firefox.exe with wine directly, rather than the desktop app and see if it that makes any difference?

Thanks but no. from firefox.exe it doesn't recognize silverlight at all.
But since the silverlight version came out just a few hours ago, maybe it hasn't come to your location yet.
I live in Norway, so netflix.com here redirects to netflix.no.
Oh well. I'm glad Netflix Desktop is on a PPA, so hopefully this will be fixed before you all get this issue.
They usually release these updates in the smaller countries first.
If any of you know who's behind this netflix desktop patch, please tell them about this so they can upgrade and patch the latest version of silverlight.

---

### Post by rai4shu2 on 2012-11-21
Looks like a new build just went up.

[https://launchpad.net/~ehoover/+archive/compholio](https://launchpad.net/~ehoover/+archive/compholio)

---

### Post by Habitual on 2012-11-21
[http://www.iheartubuntu.com/2012/11/netflix-on-ubuntu-is-here.html](http://www.iheartubuntu.com/2012/11/netflix-on-ubuntu-is-here.html)

---

### Post by colobix on 2012-11-21
> **Habitual said:**
> [http://www.iheartubuntu.com/2012/11/netflix-on-ubuntu-is-here.html](http://www.iheartubuntu.com/2012/11/netflix-on-ubuntu-is-here.html)
I don't really know why you posted this link, but that's the netflix app we are talking about here.
I really hope they fix this issue though.

---

### Post by formol on 2012-11-22
I installed it. It works, but with no sound. I try to run winecfg, but it is not include in this build of wine.

---

### Post by sdowney717 on 2012-11-23
are you running 64 bit or 32 bit?

If you delete the hidden folder .netflix-desktop, then rerun the Netflix icon, the script will reinstall and register every instance of Firefox installed under wine to work with silver light. Then you can run full Firefox browser of the latest version 17, upgraed it from help - about menu.

There is some trick about 64 bit involving the sound

---

### Post by sdowney717 on 2012-11-23
from post 155
[http://ubuntuforums.org/showthread.php?t=2084592&page=16](http://ubuntuforums.org/showthread.php?t=2084592&page=16)

>  Originally Posted by BungaDunga View Post
I also don't get sound. I have sound in my normal Wine prefix, but not the Netflix one.

Specifically, when I open up winecfg and swap to the audio tab, I see:

Code:

ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave

It seems to be due to running a 32-bit Wine inside a 64-bit Ubuntu, see:
[https://bugs.launchpad.net/ubuntu/+s...bs/+bug/408615](https://bugs.launchpad.net/ubuntu/+s...bs/+bug/408615)
And in gentoo:
[http://forums.gentoo.org/viewtopic-t...6-start-0.html](http://forums.gentoo.org/viewtopic-t...6-start-0.html)

HOWEVER, there's an easy easy fix.

Code:

**sudo apt-get install libasound2-plugins:i386**



>  Originally Posted by Beardedturtle View Post
Tried your trick and now the audio is 4x faster then normal >_< (games and netflix)
You can try this. Someone in the wine forums had issues with sound speed and this helped.
[http://bugs.winehq.org/show_bug.cgi?id=31993](http://bugs.winehq.org/show_bug.cgi?id=31993)

Quote:
Erich Hoover 2012-11-07 17:26:47 CST
(In reply to comment #9)
> Update, I can play NetFlix on my 64bit Ubuntu after I created a 32bit PREFIX.
> ...

Could you please create a new bug for the 64-bit failure and put a dependency
on this bug?

(In reply to comment #16)
> ...
> The sound and video problems come back after one movie or TV episode. I can
> resolve if I move the slider bar multiple times back and forth to 'sync' or
> 'slow' the sound and video to normal speed. Not sure if the logs would show
> this behaviour.

I've not noticed this particular issue, but when I do (rarely) notice audio
issues with Wine I've noticed that they can be resolved by executing
"**pulseaudio -k**". You might give that a try.
Comment 18 

---

### Post by stevedude on 2012-11-23
Just for my 2 cents worth...

Yesterday I just installed the Netflix App from [http://www.webupd8.org/2012/11/how-to-use-netflix-in-ubuntu-through.html](http://www.webupd8.org/2012/11/how-to-use-netflix-in-ubuntu-through.html) following their instructions on my 64-bit system and Firefox 17.

Works perfectly.

---

### Post by howefield on 2012-11-23
> **colobix said:**
> Is there something I can to to let firefox not see the newer silverlight version?


Is it not possible to install the older version of Silverlight ?

---

### Post by formol on 2012-11-23
> **sdowney717 said:**
> are you running 64 bit or 32 bit?



64. I will try solutions I read here tonight. Thanks a lot.

---

### Post by colobix on 2012-11-25
> **howefield said:**
> Is it not possible to install the older version of Silverlight ?,
You misunderstood me.
Netflix desktop comes with an older silverlight version. And that's why firefox tells me there's a newer version available.
And that is why I can't use netflix-desktop.
The upgrade message pops up, and the stream doesn't start. So when I click**Cancel**, the screen is just black.

If I upgrade Silverlight, netflix desktop freezes when I try to watch a video.

---

### Post by howefield on 2012-11-25
And unchecking "Update Add-ons Automatically" doesn't work ?

---

### Post by regor210 on 2012-11-26
The Netflix app is working on my PC. I installed it yesterday. I got it via ppa from here.

[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

Installing  netflix-desktop places a new copy of wine called wine-compholio in your root opt file so the wine you use for everything else is not modified.

Its important to note   “You can exit out of the app completely by pressing ALT+F4. You can also press F11 to exit out of full screen mode. “

---

### Post by buzzmandt on 2012-11-26
For me removing .netflix-desktop hidden folder worked like a charm

---

### Post by jason saunders on 2012-11-27
i'm having a problem with the netflix desktop, where i can hear the audio but there is no video. In some cases with the desktop,the enabling DRM button appears, and in others it doesn't. What is recommended to fix the problem that i'm having. 
thanks for any and all help
jason

---

### Post by oldrocker99 on 2012-11-29
Netflix-desktop did not work at all on my 12.10 32-bit notebook (wine error with plugin-container.exe), but it installed and works quite well indeed on my 12.04 64-bit desktop. I had very garbled sound until I entered

pulseaudio -k

before starting netflix-desktop, and all is well.

Netflix streaming under Linux? This. Is. Big.

---

### Post by hongouru@hotmail.com on 2013-06-28
[COLOR=#333333][FONT=Ubuntu Mono]I came to the solution, check my post for it...
(pulseaudio consumes much of the cpu resources, just by slowing it down, it will fix it)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono][http://hongouru.blogspot.com/2013/06/solved-netflix-desktop-has-choppy-video.html](http://hongouru.blogspot.com/2013/06/solved-netflix-desktop-has-choppy-video.html)[/FONT][/COLOR]

---

### Post by colobix on 2013-06-28
THanks a ton.
Works like a charm

---


---
title: "Goodbye Pulseaudio (ALSA, WINE, Ubuntu 8.04)"
date: 2008-05-13
forum: General Help
---

### Post by laeg_ on 2008-05-13
Pulseaudio is supposed provide the functionality of individually adjusting the volume of simultaneously running applications as opposed to having to change the master ALSA volume for all of them at once. Unfortunately there are some issues.

I couldn't use Flash and another sound using application at the same time so I installed the libflashsupport fix which helped but even with that fix all of my programs are prone to having no sound at all and some crash as a result of this even when nothing else is contending the sound driver.

Bear in mind the sound works most of the time when I run WINE alone but when I'm multitasking it's a different story. I read online Pulseaudio are aware of issues with WINE (amongst other programs) before speaking with the developers from each camp who seem to have a bit of bad blood between them.

Pulseaudio claimed the coding assumptions WINE uses are incorrect, it doesn't require the sound access it currently requests and that their developer team has air of superiority about them whenever these issues arise. Correspondingly WINE told me that said assumptions are within the ALSA interface standard which is not defined by Pulseaudio, they need the sound access for performance reasons and they will never adjust their software to work with Pulseaudio as long as it remains inoperable anyway (crashing for various reasons including receiving assumptions that it doesn't understand or are incorrect).

Must I disable Pulseaudio to have sound working in all my applications when others are in the background and must this come at the price of not being able to adjust their volume individually? Is there a fix you know of?

As per the Ubuntu guide on disabling Pulseaudio I selected ALSA in all the dropdown boxes in system > prefs > and when that didn't work I disabled PulseAudio Session Management in system > prefs > sessions > startup programs only to find that after a restart ps aux | grep pulse is still returning: pulseaudio --log-target=syslog and pulseaudio/pulse/gconf-helper which means I wasn't surprised when I confirmed I still have the problem.

Thoughts, comments and suggestions are welcome.

---

### Post by wkulecz on 2008-05-13
I've a comment.

I don't think something as radical and apparently as untested as pulse audio is belongs in a LTS release.

I see only pain, no gain from pulse audio.  There were no sound issues for me in 6.06LTS,  IMHO this is a serious regression.

--wally.

---

### Post by laeg_ on 2008-05-13
> **wkulecz said:**
> I don't think something as radical and apparently as untested as pulse audio is belongs in a LTS release.


I've spoken to many that share this view. Pulseaudio makes me cry but I am new to linux and maybe my tears are uncalled for. 

I would rathered to have just disabled Pulseaudio because it is possible that their dev team and WINE will make the required changes at some point and it would have been nice to be able to just flick a switch back on to test it but I ended up having to completely remove it and set everything to ALSA. I'm left struggling to understand what I am possibly missing? I *am* able to change the volume on simultaneously running applicaions individually and everything seems to work perfectly now. Oh and alsa-pulse plugin which is cited as a fix in an Ubuntu guide killed my sound in some applications entirely.

---

### Post by Zorael on 2008-05-13
I like pulse, but then it Just Works for the apps that I actually use. The sole exception being Skype, I guess, which I must wrap the the OSS version with padsp to get sound. On the other hand, I **don't** like ALSA, and would love it if the pulse and OSS4 crews could make that combination work. Please see [http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5). Pulse or no pulse is the dealbreaker for me.

As for being an LTS release and containing some stuff that aren't rock-stable, this is unfortunate, yes. Were I Canonical I'd release two versions of Ubuntu, much like Kubuntu. Except maintain LTS status on the non-"remix" version.

Firefox 3, Pulse and other up-and-comic apps/frameworks included in this release may be the de facto standards in a few months, so luck willing this time of instability and bugs will become nothing more than an embarrassing (but passing) paranthesis in the history of 8.04. There are still just short of 3yrs left on the LTS.

---


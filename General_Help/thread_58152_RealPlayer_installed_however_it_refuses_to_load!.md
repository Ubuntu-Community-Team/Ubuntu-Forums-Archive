---
title: "RealPlayer installed however it refuses to load!"
date: 2005-08-19
forum: General Help
---

### Post by Solomon on 2005-08-19
Hey guys, I have an interesting problem. I installed RealPlayer via the terminal (followed the directions I was given correctly). When I go to Applications > Sound & Video, RealPlayer shows up. When I download an RM file, it shows the RealPlayer logo. By all rights, as far as I can tell, it should work. The problem is, it doesn't.

To put it as simply as possible, it will not load. I have tried launching it from the menu, no go. I have tried launching it from the terminal. It doesn't load. No error via the terminal either. I type in "realplay" but it does abolutely nothing. No message, no error... No RealPlayer appears on the screen. The interesting part to this is that if I go to System Monitor, it shows RealPlayer. For example, earlier this morning I tried launching it quite a few times. I ended up with 23 instances of RealPlayer in the System Monitor. I restarted, tried it again (both ways). No god. Hell, I've even tried install RP via Synaptic. So as you can tell, I'm in between a rock and a hard place.

Any advice?

---

### Post by kokiri on 2005-08-19
wow... that's really something... hrmm... when launching it via the terminal does it give any errors before aparently dying?

Other than that I'd try some good ol' windows mentality and reboot, maybe some other zombie process is inadvertantly killing realplayer from an application that didn't quit and exit cleanly in the past. I know that linux is really good for this and it usually isn't a problem, but with audio visual programs it can be a problem if something doesn't totally let go of the audio server or whatnot.

---

### Post by Solomon on 2005-08-19
If you had read my post, you would have realized that everything you've suggested... I've already tried... multiple times. I am just a tad frustrated.

---

### Post by sparkee_boy on 2005-08-19
[QUOTE=Solomon]Hey guys, I have an interesting problem. I installed RealPlayer via the terminal (followed the directions I was given correctly). When I go to Applications > Sound & Video, RealPlayer shows up. When I download an RM file, it shows the RealPlayer logo. By all rights, as far as I can tell, it should work. The problem is, it doesn't.

To put it as simply as possible, it will not load. I have tried launching it from the menu, no go. I have tried launching it from the terminal. It doesn't load. No error via the terminal either. I type in "realplay" but it does abolutely nothing. No message, no error... No RealPlayer appears on the screen. The interesting part to this is that if I go to System Monitor, it shows RealPlayer. For example, earlier this morning I tried launching it quite a few times. I ended up with 23 instances of RealPlayer in the System Monitor. I restarted, tried it again (both ways). No god. Hell, I've even tried install RP via Synaptic. So as you can tell, I'm in between a rock and a hard place.

Any advice?[/QUOTE]

I think I tried responding to your request for help in a different thread.  Anyway, I had the same problem.  It had to do with the sound setup.  Basically you have to set up ESD to not hold the sound resources indefinitely, get the ALSA library for ESD, setup the ALSA system, set the Multimedia Prefereneces to use ALSA, and possibly disable the "enable sound server startup" in the Sound Preferences (I didn't have to do the last step).  There are several great howto threads on setting up the sound settings.

Anyway, hope this helps you out.  Check out the other Realplayer thread you posted on for more info on what I did.

---

### Post by sparkee_boy on 2005-08-19
I found another thread that is supposed to allow Realplayer to use ALSA instead of OSS.  The link is [http://ubuntuforums.org/showpost.php?p=80282&postcount=21](http://ubuntuforums.org/showpost.php?p=80282&postcount=21)

Haven't tried it myself yet, but I will later today.

---

### Post by sparkee_boy on 2005-08-19
[QUOTE=sparkee_boy]I found another thread that is supposed to allow Realplayer to use ALSA instead of OSS.  The link is [http://ubuntuforums.org/showpost.php?p=80282&postcount=21](http://ubuntuforums.org/showpost.php?p=80282&postcount=21)

Haven't tried it myself yet, but I will later today.[/QUOTE]
 Well, that did it!  I can listen to sounds from various sources and applications now with Realplayer running!

---


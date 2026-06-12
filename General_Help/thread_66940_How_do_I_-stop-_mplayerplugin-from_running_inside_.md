---
title: "How do I -stop- mplayerplugin-from running inside Firefox?"
date: 2005-09-18
forum: General Help
---

### Post by Blueshell on 2005-09-18
I have a freshly-installed Hoary, onto which I also installed RealPlayer.  RP works fine for most sites, popping up its little player and playing audio just fine.

However, certain sites, such as the "Listen to the whole show" link of [http://www.npr.org/programs/waitwait/thisweek.html](http://www.npr.org/programs/waitwait/thisweek.html), instead run some bit of Javascript to compute the URL and then mplayerplug-in v2.70 starts running inside Firefox.  -That- plugin (a) buffers some amount of the stream and then hangs forever, having played no audio at all, (b) has no controls to get it to STOP, (c) caused my browser to instantly exit the one time I got it to do anything (on some other site) and then tried to stop the stream from playing, and (d) if I kill the window the plugin is running, and then do Edit -> Preferences, Firefox again vanishes instantly.

So really, I don't want this plugin to run at all, because it's incredibly buggy and crashes my browser.  I want RealPlayer to run instead if -any- site tries to give me RealAudio.

How can I accomplish this?

I found [http://mplayerplug-in.sourceforg.net/config.php](http://mplayerplug-in.sourceforg.net/config.php), but it's not all that helpful.  It points out three different config file locations, NONE of which (apparently, unless I'm looking for the wrong thing) claim that mplayer should try to play RealAudio (and one of which has every single line commented out, including the line enable-real=0 (so the -disabling- is commented-out, but I can't find a config file that turns it -on-, and yet it's claimed to be -off- by default).  That page also mentioned the "Configuration Dialog", with no hint about what program might be the one whose dialog I should select.

if I look in Firefox's Edit -> Preferences -> Downloads, it claims that RA types should run the RealPlayer that I downloaded and built, and for some sites, that's exactly what happens.  What's special about npr.org's site that is breaking this, and is instead causing mplayerplug-in, which I -do not want-, to run?

Thanks...

---

### Post by twowheeler on 2005-09-18
Well, you could uninstall mplayerplug-in completely in synaptic.  

Or you could get the latest mplayerplug-in which works perfectly.  The how-to is 
[here.](http://www.ubuntuforums.org/showthread.php?t=60505&highlight=mplayerplug-in).

I dumped realplayer because this is so much better.

---

### Post by Blueshell on 2005-09-18
Yikes---there's a lot of fuzz around the instructions on that page.  There are so many small changes that I'm not sure the final edits made it into the instructions without going through four pages of debugging to compare it to the final form.

I may just punt mplayerplug-in completely (it's hard to believe that a total uninstall is the easier way to just get it out of the way for -some- RealAudio files!) and hope that either when I upgrade to Breezy when it's finally released, it'll come back (correctly, with the newest version) on its own, or that I can install it if it doesn't.  I'd rather not have to muck around quite so much and take the risk that I'll leave Hoary in an inconsistent state such that the Breezy update won't update it...

(And---if I remove mplayerplug-in, will the RealAudio helper app then run for those streams for which mplayerplug-in tried to run before?  If so, why?  It's not at all clear to me what's going on here or what the implications are going to be of removing it.)

The big question is, though, -why- is mplayerplug-in trying to play -any- RealAudio streams -at all-?  It doesn't on -some- sites---why is it trying to play the ones from npr.org?  What's -really- going on here?  Seems to me that there should be some simple configuration item I can use to say, "Look, mplayerplug-in, just DON'T TOUCH ANYTHING RA" and leave it at that, without having to manually uninstall it, etc.  I mean, it -doesn't- try to play -some- RA streams...

---

### Post by Blueshell on 2005-09-20
So just to provide some closure---I decided not to mess around with getting the new mplayerplug-in installed, since the instructions had been hacked around with so much and since I figure I can wait a month and then just get Breezy's version when that release is out.  Instead, I closed Firefox, did a complete-uninstall of mplayerplug-in in Synaptic, restarted Firefox, and npr.org's streams instantly starting using RealPlayer instead. Problem solved with five seconds of work.  (But thanks for suggesting that I just get rid of MP-in; it wouldn't have occurred to me that this was going to just DTRT.  I guess I'm gunshy after so many more painful experiences in other distros.)

---


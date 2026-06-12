---
title: "Adobe Flash stopped working today after updates"
date: 2015-01-15
forum: General Help
---

### Post by JayArtist on 2015-01-15
[Solved] plus new update

Hi,

I ran my usual update today on 14.04LTS and there was a new version of Firefox (35 from 34) and an update to Adobe Flash.

All seemed to go well after the install, but when I went to Youtube, I just get a black screen on the clips.

I've uninstalled/reinstalled Flash and also Firefox 35, but still the problem persists.

I've read that it's an old version of Flash and that there are no updates (just security ones) in the pipeline for Adobe Flash in Linux, but as far as I know the old versions that's been around for the last few years works - it's just out of date compared to it's Windows counterparts. 

Firefox 35 has two listings in the Plugins, one 11.2.202.529. This would seem like a fix because I can view Youtube clips, or at least hear the sound and scroll through the time-line minus the actual video animating/streaming. So the HTML5 ain't working correctly either, although I don't know if it is supposed to as I've never tried it before.

According to [http://www.whatismyflash.com/](http://www.whatismyflash.com/) my version of Flash is 11.2.202

I did download Chrome for the time being, but I just don't like it as much as Fox, I've used that since they started!

Thanks, Jay.

Edit:

No idea why, but after uninstalling and reinstalling Adobe Flash, then trying the Chrome/Pepper (no luck there) then uninstalling that and re-installing Adobe Flash, all working again. Weird one, but at least it's sorted for the time being!



New Edit: Well all went well on my desktop PC, but when I updated my laptop running the same setup, things went haywire just the same too. I tried un-installing/re-installing Flash, but I didn't want to re-install Firefox even with the extension FBE as it takes too long.

I instead tried the alternative "Lightspark" as suggested by another user - it's available in the repo, but the plugin for Firefox didn't come with it, which I had to install manually. when it finally worked, it didn't, instead it crashed Firefox on every attempt trying to play video! 

So I looked into HTML5 which I know it's intended to be the future - although every time I opened Youtube without Flash, the clip would play with no picture, just audio.

But I found a link to enable it to work correctly ([https://www.youtube.com/html5](https://www.youtube.com/html5)), why it helps I don't know, and I'm assuming it's set in a cookie as I don't have a Youtube account, so not logged in. All works fine now, HTML5 runs with picture and audio all without outdated Flash, yay!

Whether other sites will fair the same I'm not sure, but Youtube is the main Flash site for me.

---

### Post by phidia on 2015-01-15
If you run into further problems with flash you might consider the [project lightspark]("https://launchpad.net/lightspark/+download"). Yeah it hasn't been updated in a while but people still use it.
Even on other platforms, I use OS X frequently, flash has occasional hiccups.

---

### Post by Impavidus on 2015-01-15
Good you already solved it.

In my experience html5 just works on youtube. I always watch youtube using html5. Feels better to me. You have to opt in to get html5, but if you don't have a flash player (or if you disabled it), html5 is the default.

---


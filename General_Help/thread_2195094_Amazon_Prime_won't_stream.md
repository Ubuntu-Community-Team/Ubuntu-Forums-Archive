---
title: "Amazon Prime won't stream"
date: 2013-12-22
forum: General Help
---

### Post by Linuxratty on 2013-12-22
I'm trying this using a friend's info (with permission) to see if it's worth getting. He's a Windows user..When I try to stream something it says my flash player needs to be upgraded. Why would this be? Or will this simply not work with Ubuntu? I was able to stream a preview just fine. I'm using Fire Fox,
What gives?

---

### Post by TheFu on 2013-12-22
e[http://blog.jdpfu.com/2013/07/26/linux-and-amazon-prime-streaming](http://blog.jdpfu.com/2013/07/26/linux-and-amazon-prime-streaming) is from July.  Sometime in May, Amazon enabled DRM which made it harder to stream. Strangely, it has worked with Mint. Ran out of reasons to try to get it working when a Roku arrived.

Adobe has stopped updating Flash on Linux and Android ... it has been months now since that announcement.  The only updated flash on Linux comes from Google via Chrome, not Chromium. I've never used Chrome, it is against my religion, so I don't know if that helps or not.g

---

### Post by Linuxratty on 2013-12-22
Ok, thanks so much. I think I'll get a vm and slap Mint or Open SUSE on it and see what happens.

---

### Post by CharlesA on 2013-12-22
Try it with Chrome. Can't hurt.

---

### Post by monkeybrain20122 on 2013-12-22
If DRM flash is the issue you may try pipelight, which allows you to get Windows' flash in native Linux browsers, may need an user-agent-switcher to work.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

Also I heard that hal works (that is probably why Mint works), in 13.10 hal is no more but there is a ppa.[URL="https://launchpad.net/~mjblenner/+archive/ppa-hal"]https://launchpad.net/~mjblenner/+archive/ppa-hal


[/URL]

---

### Post by monkeybrain20122 on 2013-12-22
> **CharlesA said:**
> Try it with Chrome. Can't hurt.

It won't work because Chrome's flash for Linux doesn't support DRM.

---

### Post by CharlesA on 2013-12-22
> **monkeybrain20122 said:**
> It won't work because Chrome's flash for Linux doesn't support DRM.

D'oh!

---

### Post by TheFu on 2013-12-22
> **monkeybrain20122 said:**
> If DRM flash is the issue you may try pipelight, which allows you to get Windows' flash in native Linux browsers, may need an user-agent-switcher to work.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

Also I heard that hal works (that is probably why Mint works), in 13.10 hal is no more but there is a ppa.[URL="https://launchpad.net/~mjblenner/+archive/ppa-hal"]https://launchpad.net/~mjblenner/+archive/ppa-hal
[/URL]

I installed HAL under Ubuntu in summer - didn't help. Good thought though.

After trying to get it working for a few weeks under Ubuntu 12.04 (that's what my XBMC runs), came across a few people at my LUG running Mint and streaming Amazon fine in a browser.  I wanted XBMC streaming - no a stock browser. My XBMC setup is 100% TV, no monitor, no keyboard, just a small E350+HDMI output.

Also some OpenSUSE folks claimed it worked too.  Nobody with Ubuntu made any claims. I tested with a stock Mint install inside a VM - it worked - but from what I could see, Mint never met a codec it didn't want installed - even had RealPlayer crapola along with 15 other codecs.  I was in the middle of trying to copy the Mint settings/packages back to my Ubuntu setup, then a death in the family side-tracked me completely for months - I'm still sorta side-tracked from that event.

I honestly haven't tried to stream anything form Amazon on Ubuntu 12.04 in 4+ months.  Nope. Still doesn't work.

I'm fairly certain that someone, somewhere has this working. After all, if Mint can do it, then Ubuntu should be able fairly easily.

---

### Post by Linuxratty on 2013-12-22
Ah,thanks much...

---


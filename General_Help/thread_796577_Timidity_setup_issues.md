---
title: "Timidity setup issues"
date: 2008-05-16
forum: General Help
---

### Post by montgoja on 2008-05-16
I don't know if this is the right forum to post this problem in, so I apologize in advance if this is the wrong area.

I just made a clean install of Hardy and I'm trying to put back a lot of the programs and settings, etc. that I had before I wiped everything.  One of the programs that looked interesting was a guitar tab writing program called songwrite.  Before I made the clean install, songwrite installed perfectly, though I have to admit I never got around to trying it out.

This time, though, when I checked songwrite in the add/remove program, I'm getting dependency problems all centered around Timidity.

When I apt-get install songwrite in the terminal, I get this:

[CODE]

Selecting previously deselected package songwrite.
(Reading database ... 120763 files and directories currently installed.)
Unpacking songwrite (from .../songwrite_0.14-2_all.deb) ...
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                   ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
                                                                         [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of timidity-interfaces-extra:
 timidity-interfaces-extra depends on timidity (= 2.13.2-19ubuntu1); however:
  Package timidity is not configured yet.
dpkg: error processing timidity-interfaces-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of songwrite:
 songwrite depends on timidity | playmidi | pmidi; however:
  Package timidity is not configured yet.
  Package playmidi is not installed.
  Package pmidi is not installed.
dpkg: error processing songwrite (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 timidity-interfaces-extra
 songwrite
E: Sub-process /usr/bin/dpkg returned an error code (1)

[CODE]

Sorry it's not in the special box... I think I used to know how to do it but I can't remember now.  (Shows how long it's been since I've been on here haha)


And now any time I use the update manager, terminal upgrading, anything at all, I end up getting the error message that timidity isn't configured yet.

What do I need to do to either get timidity to configure correctly or at least stop making these error messages come up?

I tried deselecting songwrite, but it leaves me still with the unresolved timidity issue.

Any help is appreciated.  Thanks!

---

### Post by montgoja on 2008-05-23
Weird, but for whatever reason, my problem managed to work itself out.  I love linux.  haha.

I removed songwrite AND timidity after a little while fiddling with what little terminal know-how I posess, and still had a few packages that tried to install themselves, but had issues with timidity.  After a reboot and a apt-get update/upgrade, the issues seemed to iron themselves out.  I ran an apt-get install on both timidity and songwrite, and they installed NO problems this time around.  Weird.

:guitar:

---


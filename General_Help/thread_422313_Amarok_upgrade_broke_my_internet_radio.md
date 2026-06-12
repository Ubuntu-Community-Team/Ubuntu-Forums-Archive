---
title: "Amarok upgrade broke my internet radio"
date: 2007-04-25
forum: General Help
---

### Post by MagisterJoe on 2007-04-25
I upgraded via the official method from edgy to feisty in kubuntu, so I also got Amarok 1.4.5 as part of the package.  Suddenly though, several of my internet radio streams fail to play.  Two error boxes pop up when I try to play them:

The top box says:
[INDENT]Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
[http://129.89.70.125/](http://129.89.70.125/)[/INDENT]

The second box:
[INDENT]The connection was refused for the URL: 
xine parameters: http status not 2xx: [/INDENT]

I haven't been able to find any way to fix this in any of the bug reports that I've examined for things like Last.fm.  Anyone know why this is happening?

If there is no way to fix this, is there a way for me to downgrade to 1.4.3, or an older version of xine, whichever would fix this problem?

---

### Post by meldroc on 2007-05-08
I'm getting similar issues, after running apt-get dist-upgrade and upgrading my box from Edgy to Feisty.  For the most part, the upgrade went pretty smoothly, a few glitches here and there.

But now, with some streams, in particular, the internet radio stream found at am760.net (so help me, I'm addicted to liberal talk radio) no longer works.  Amarok throws me this "no suitable input plugin" error, after hanging and being completely unresponsive for a full minute.  Strangely, other radio streams work fine.  Maybe I'm missing the one coded that this particular stream uses, though I did go to medibuntu and commit some felonies by installing the w32 codecs and libdvdcss, so most of that stuff works fine.

Any ideas?  I can't get this particular stream working in Firefox, mplayer, xine, or their front ends like kmplayer or kaffeine.

---

### Post by toupeiro on 2007-05-12
I'm getting the exact same errors from sites with Streaming media.  I also did the upgrade from edgy to feisty.

I've tried several different things up to and including removing all xine related packages and firefox packages and reinstalling them.  (at least all the relative ones I could think of)

I would really like to get this one fixed.  Up until I upgraded to Feisty, I was almost at the point of removing  windows from my system entirely.  I don't like having excuses to change back because I  love the feel of ubuntu.

---

### Post by tgalati4 on 2007-05-13
Time to dust off that old radio dial.

---

### Post by meldroc on 2007-05-14
Just following up on my own gripes, it looks like my broken radio started working on its own.  Maybe it was a corrupt stream, or the server was down or overloaded, and maybe Amarok's a little finicky, but now it's working.

---


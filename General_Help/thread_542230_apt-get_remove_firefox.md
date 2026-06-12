---
title: "apt-get remove firefox"
date: 2007-09-03
forum: General Help
---

### Post by Frinky on 2007-09-03
Hi,

I was having a play with my system and foolishly thought I knew what I was doing. I wanted to try to remove Firefox so from a terminal I typed:
[FONT="Arial Black"]
  sudo apt-get remove firefox[/FONT]

and got the following message:

[FONT="Arial Black"]The following packages will be REMOVED
  eclipse eclipse-jdt eclipse-pde eclipse-platform eclipse-source firefox
  firefox-gnome-support gnome-user-guide gramps mozilla-mplayer ubuntu-docs
  yelp
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 220MB disk space will be freed.[/FONT]

Stupidly I didn't read the message and just went with "Y". Whoops there went my install of eclipse (amongst other things).

Now, first of all I can't quite understand how eclipse had such a dependency on firefox. Does apt-get remove <application> remove all of the packages (in their entirety) that require <application> ? If so, is there a way to turn off this behaviour (or would you even want to)? It appeared to me a bit harsh to remove lots of other applications, just because one has gone. 

Secondly, is this stuff really gone? I can easily re-install most of it, it's just that eclipse is a 100Mb download. Any shortcuts rather than just apt-get install eclipse ?

Maybe I'm not really getting my head round apt-get correctly...

Thanks,
Frinky

---

### Post by jamvegan on 2007-09-04
The eclipse-platform package lists firefox as a dependency, and the other eclipse packages depend on eclipse-platform.

The nice thing (to my mind) about Debian package management is that it does a really good job of preventing broken dependencies, but it does mean that trying to remove one little app can lead to...well, just what you encountered.  Think about the alternative, though.  If apt-get were to happily remove firefox, and nothing else, and eclipse really does need it, you might suddenly find that eclipse didn't work anymore, but have no idea why.

I don't think that remove deletes the package files automatically.  I believe that you have to run clean to do that.  If they are still hanging around on your hard drive, apt-get will use them rather than downloading them again if you install again.  But maybe you've already tried and found that out by now?

---

### Post by Frinky on 2007-09-05
Hi,

Thanks for the response. It's interesting that when things go wrong that you can use it as a learning experience.

I tried apt-getting install eclipse and it started an 88Mb download which wasn't great for me. So it would appear that apt-get remove really does wipe out the contents (apt-get remove did say it was going to recover 220Mb of space after all).

Fortunately for me, I had the install tar file of eclipse kicking around on my hard drive, so I could just re-install that.

Guess I'll chalk this up to experience and not be so quick to use apt-get. Back to Synaptic package manager for me.

Thanks,
Frinky.

---


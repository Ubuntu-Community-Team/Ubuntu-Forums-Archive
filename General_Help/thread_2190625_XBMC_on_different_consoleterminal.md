---
title: "XBMC on different console/terminal"
date: 2013-11-28
forum: General Help
---

### Post by NertSkull on 2013-11-28
I just started playing around with this stuff.  But my understanding is there are different consoles by doing the ctrl+alt+f1.  From what I've read, F8 and above are different GUI sessions (I'm sure I have my terminology all wrong).

Basically what I'm thinking is this.

I have my main computer setup hooked to two monitors that I use daily.  Just a typical dual monitor setup.  But I also have my TV plugged into an HDMI out on my graphics card (it has three outputs).

Currently, whenever I want to watch a movie on XBMC, I have to go to nvidia settings and turn off the dual monitors and turn on the TV output.  Then I log off and log back in and now my video out is going to the TV instead.

So my thought was.  Instead of doing it that way.  Set up a 2nd GUI on F9 or something.  And then just hit ctrl+alt+F9 and have that switch from dual monitors to my TV.  Then when I'm done do ctrl+alt+F7 and I'd be back to dual monitors.

I was thinking of starting a second X session by doing the following in the first console

```
startx -- :1 
```

And that does start a new X session for me.  But I don't know how to link it up to a 2nd xorg.conf where I can change which monitor things are on.

Is there any way to do this?

If not, is there at least a way I can do it without logging off and logging back in?

Thanks all.

---


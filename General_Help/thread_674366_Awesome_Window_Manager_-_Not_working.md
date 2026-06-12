---
title: "Awesome Window Manager - Not working"
date: 2008-01-21
forum: General Help
---

### Post by ~LoKe on 2008-01-21
Well, I've been using Awesome for a few weeks/months now, but I just reinstalled Ubuntu so I had to grab it again.  I downloaded the 2.1 source and compiled it.  Now it's spitting errors about  "Missing title for section 'statusbar'" from my ~/.awesomerc.  I haven't changed my config since the last time it was working, so it must be the new version.

Here's the important part:
```
    statusbar
    {
        position = "bottom"
    }
```
I tried just doing title="whatever" but it didn't work.

So...what do I do?

---

### Post by mali2297 on 2008-01-21
The syntax for the configuration file has changed somewhat. Either install version 2.0 or update your .awesomerc. The new syntax is described in [this man page]("http://www.calmar.ws/awesome/awesomerc.1.html").

There seems to be new cool features for the status bar. I tried to implement them when I realised that I had the wrong version. I will however wait for a stable release before I upgrade.

---

### Post by ~LoKe on 2008-01-21
Jesus that's confusing..  I don't even know where to start.

But at least I know why I'm having problems.  Thanks. =]

---

### Post by ~LoKe on 2008-01-21
Could they make this any more confusing?

```
    statusbar <identifier> [MULTI]
    {
        position = <{top,bottom,left,right}>
        height = <integer>
        width = <integer>
        taglist <identifier> [MULTI]
        {
            x = <integer> y = <integer>
            mouse [MULTI]
            {
                button = <integer> modkey = {<mod>, ...}
                command = <uicb-cmd> arg = <uicb-arg>
            }
        }
```
What is identifier?  Just a name? What's with the taglist?  What the hell?

---

### Post by ~LoKe on 2008-01-21
Anyone have a sample of .awesomerc for 2.1?  Or has a link for the old version?

---

### Post by mali2297 on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=642808&page=3?post#85](http://ubuntuforums.org/showthread.php?t=642808&page=3?post#85)

---


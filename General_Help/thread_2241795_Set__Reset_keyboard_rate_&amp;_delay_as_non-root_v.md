---
title: "Set / Reset keyboard rate &amp; delay as non-root via command line"
date: 2014-08-28
forum: General Help
---

### Post by Krupski on 2014-08-28
[SIZE=1](Mods if this is in the wrong spot my apologies and please move it).[/SIZE]

Hi all,

My office computer is running Linux with KDE (RHEL6 to be exact). Of course, I have to log into this computer as a "user" since the IT people are "root". :(

Anyway, for some strange reason, once in a while my keyboard will drop offline, requiring me to unplug and replug it to get it working. Unfortunately, doing this resets the keyboard to it's hardware default key repeat delay and rate (which is really slow).

I can go into KDE "System Settings" and reset the delay and repeat rate graphically, but I can't do it via the command line.

Obviously the keyboard CAN be set as non-root because "/usr/bin/systemsettings" can do it.

So, is there a *command line* utility that I can use to do the same thing as opening the GUI and clicking on the settings? (Note "kbdrate" does not work - it's not allowed access to the keyboard as non-root).

I want to automate the resetting so that if the keyboard drops off, I can either click a simple icon to run the script and fix it, or else detect when it fails of and reset it automatically or simply do it periodically.

Whatever, I need to set the keyboard delay and repeat rate _via the command line **as non-root**_ (in KDE). Of course, I searched Google - nothing. Anyone know how to do this?

Thanks!

-- Roger

---

### Post by connor12 on 2014-10-03
I have this exact same problem of needing to re-connect my keyboard frequently, and I believe what you want is the `xset` command.

```
xset r rate 200 25
```

This will set the key repeat rate to 25 ms and the delay to 200 ms.

---

### Post by Krupski on 2014-10-08
> **connor12 said:**
> I have this exact same problem of needing to re-connect my keyboard frequently, and I believe what you want is the `xset` command.

```
xset r rate 200 25
```

This will set the key repeat rate to 25 ms and the delay to 200 ms.

That did the trick! Thank you so much!  [IMG]http://www.hobbytent.com/images/smilies/thumbsup.gif[/IMG]

---


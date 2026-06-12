---
title: "Sleep key on dell keyboard KB113p"
date: 2014-10-25
forum: General Help
---

### Post by Gottier on 2014-10-25
I've got a Dell keyboard model number KB113p, and it has a sleep key (crescent moon). This sleep key does the same thing as Suspend from the gear menu. It works awesome. So it got me thinking, and wondering how Ubuntu knows what that key is. I have other keyboards without sleep keys, and if I can make one of the keys a sleep key, that would be great!

I was able to come up with a solution using xbindkeys:

```

# Sleep using Pause/Break key
"dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend"
  Mod2 + Pause

```

This works too, but it doesn't work as fast. When I use the sleep key suspend is instantaneous. The pause/break key works, but there is about a 1 second delay before suspend.  So I wonder, how does the Dell keyboard sleep key work? What could I do to make the pause/break key suspend instantaneously?

A 1 second delay is no big deal, right? It's just that I am so curious about the Dell keyboard. What do you think?

---

### Post by Gottier on 2014-10-28
Well, in theory what I did works, but the problem is when the computer wakes from suspend, there are some weird display issues. For instance, the Unity bar missing with a pixelated background as a replacement. So, there's definitely a difference in the command that I was using and what happens when Suspend is chosen from the gear menu. It's a real bummer, and the convenience of a Suspend key on the keyboard is really nice.

---


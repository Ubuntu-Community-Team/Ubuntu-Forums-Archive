---
title: "GAIM randomly crashing"
date: 2007-04-17
forum: General Help
---

### Post by Fireblend on 2007-04-17
So, sometimes it's after 15 mins, sometimes just after I start it, it just crashes, but always during a conversation. Is there any way to solve this? Some way that a newbie can actually follow? Thanks in advance.

---

### Post by Brucevdk on 2007-04-18
Are you using the latest beta release (beta 6)? If not, you should probably install it via apt/synaptic (at the moment you'll have to add a third party repository for this). I'll explain how to do so via the user interface. Try to use a clean profile too (move the folder called .gaim in your home directory somewhere temporary).

System -> Administration -> Software Sources -> Tab (Third Party) -> Add

Add the following line:
```

deb http://repository.debuntu.org/ edgy multiverse

```

Then update Gaim/Pidgin using System -> Administration -> Update Manager

If it still crashes, you could try with one of the Pidgin builds mentioned in the thread  [Howto compile Pidgin IM]("http://ubuntuforums.org/showthread.php?t=404508"). If nothing helps, perhaps [read the following post]("http://ubuntuforums.org/showpost.php?p=2472969&postcount=3").

---

### Post by llebegue on 2007-04-18
My gaim (2.0.0 beta3.1) kept crashing when someone sent me some emoticons from MSN.

I found a workaround by disabling formatting in incoming messages

Tools -> Preferences -> Conversation tab -> disable "Show formatting on incoming messages" checkbox.

---


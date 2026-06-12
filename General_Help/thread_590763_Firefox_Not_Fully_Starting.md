---
title: "Firefox Not Fully Starting"
date: 2007-10-25
forum: General Help
---

### Post by MtnCoder on 2007-10-25
I'm trying to launch FF, but it doesn't fully load. I will most often get the "Session Manager - Restore after Crash" dialog, but regardless of which I choose (Don't Restore vs Restore Session), the dialog closes and FF never appears

If I run:

```

ps -e | grep fire

```

I get:

```

7370 ?        00:00:00 firefox
7386 ?        00:00:02 firefox-bin

```

I've tried deleting .mozilla/firefox, and was presented with the "Import" dialog. Going through that path resulted in the same as above.

Some other information:

[LIST]
[*]IBM Lenovo T60p ThinkPad
[*]Dual boot XP
[*]Running Gutsy
[*]Trying to run FF 2.0.0.8
[*]Trying to also run swiftweasel, but same results
[*]Not getting anything in /var/log/messages
[*]Running firefox -safe-mode (to disable plugins) does not help
[*]This is sporadic - FF will occasionally work with no discernible rhyme or reason
[*]Opera runs fine, if that's relevant
[*]I can't say if this was happening on Feisty - this is my first Ubuntu foray
[*]Have tried deleting .mozilla/firefox, but no help
[/LIST]

Thoughts?

Thanks!

---

### Post by MtnCoder on 2007-10-25
Alright, got some more information.

This morning FF started just fine, as did Thunderbird. Swiftweasel, however, did not. When I ran it from the command line, I got:

```

*** glibc detected *** ./swiftweasel-bin: free(): invalid next size (fast): 0x08ea4c28 ***

```

as well as a whole bunch of other stuff, but that seemed the most pertinent.

I presume this is the same thing that's happening when FF won't start. What do I do about an "invalid next size"?

Thanks!

---

### Post by MtnCoder on 2007-10-25
*bump*

---

### Post by MtnCoder on 2007-10-26
*bumpity-bump-bump*

---

### Post by MtnCoder on 2007-10-26
*bump*

Anyone?

---

### Post by 9387 on 2007-10-28
i went through the same exact problem. uninstall fire fox. kill the proces id. delete all firefox files. reinstall fire fox using sudo apt get. should work.

i spent 5 hours figuring this out.

---

### Post by MtnCoder on 2007-10-29
Hey 9387, thanks for the reply.

When you say "kill the process id," do you mean the following:
```

killall firefox-bin

```
?

Sorry if that's an obtuse question. I'm pretty new to Ubuntu and Linux in general.

---

### Post by 9387 on 2007-10-29
Well for some reason even if you Uninstall fire fox the process remains running even after un-install. Even if you delete all firefox files, directories including ./mozilla it still remains as a process thereby blocking any succesfull reinstall.

Solution:

enter Terminal.

type:

kill 7326
kill 7328


where 7326 and 7328 represent your fire fox process. First you might want to run that command you did before to identify the process ID # then kill it by typing "kill #"

Then reattempt clean install of Firef0x

---

### Post by MtnCoder on 2007-10-29
Great, thank you, 9387. I'll try the reinstall and report if it works.

---


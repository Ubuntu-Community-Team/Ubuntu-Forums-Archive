---
title: "What does the &quot;-a&quot; option do in regards to installing held back package update-instal"
date: 2023-01-18
forum: General Help
---

### Post by Butthead on 2023-01-18
Quickly installing held back packages, I see a caution on using the "-a" (no quotes) option when installing update-installer-common.  By that time it was too late for me to stop.  Exactly what does the "-a" option do in regards  to that package (i.e. important somehow?).  Thanks for any info!

---

### Post by ian-weisser on 2023-01-19
What was the complete, exact command that you input?

---

### Post by Butthead on 2023-01-19
"sudo apt install update-notifier-common" was what I input into terminal (being a suppposed held back package).

Then Konsole blabbered something back about using an "-a" option that I failed to catch (and can't find anything now concerning "-a" or update-notifier-common when Googling it now).

---

### Post by Bashing-om on 2023-01-19
hello -

In terminal do:
```

apt list update-notifier-common

```

Me thinks that the -a switch meaning will become quite apparent :D

 [INDENT]ubuntu: No secrets
[/INDENT]

---

### Post by Butthead on 2023-01-20
Huh? :o

I'm dumb, humor me.

Looks like the ouput of running "apt list -upgradable" with nothing left to upgrade as far as I can tell. :-k

---

### Post by Bashing-om on 2023-01-20
Huh ?
what does "apt list -upgradable" have to do with the inquiry for -a switch ?

> 
sysop@x2204mini:~$ apt list update-notifier-common
Listing... Done
update-notifier-common/jammy-updates,jammy-updates 3.192.54.3 all [upgradable from: 3.192.54]
N: [color=red]There is 1 additional version. Please use the '-a' switch to see it[/color]
sysop@x2204mini:~$ 

-all in that process of learning-

---

### Post by Butthead on 2023-01-21
> **Bashing-om said:**
> Huh ?
what does "apt list -upgradable" have to do with the inquiry for -a switch ?


-all in that process of learning-

Yeah, I guess so. :guitar:

You would think they could give you a hint where it goes though. :|

Anyway, thanks for your kind assistance!

---

### Post by Bashing-om on 2023-01-21
well ---

> 
You would think they could give you a hint where it goes though.


it is a switch - General useage is to place the switch after the command and before the execution target; However after the target is also accepted.
For example:
```

apt list -a update-notifier-common

```

```

apt list update-notifier-common -a

```

[INDENT]a step up on the learning curve
[/INDENT]

---

### Post by Butthead on 2023-01-22
Thank you.  Most helpful examples. :KS

---


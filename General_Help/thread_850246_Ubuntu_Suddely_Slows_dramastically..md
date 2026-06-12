---
title: "Ubuntu Suddely Slows dramastically."
date: 2008-07-05
forum: General Help
---

### Post by desm on 2008-07-05
Ubuntu works really well, but then suddenly slows down, and pauses lots. To the extend where a restart is required and no sound plays.

I'm running Hardy Heron (8.04.1), and the problem usually occurs after attempting to load a page in a tab in firefox 3.
I disabled ipv6, but that made no difference at all.

I checked the processes and firefox didn't seem to be using a bloated amount of cpu or memory, less than totem.

I don't know anything else I can do to help diagnose the problem. But it's incredibly frustrating, and it used to happen on my previous ubuntu install too.

---

### Post by coolaj86 on 2008-07-05
This is a trick that generally works in any OS when you have random problems like that:

Create a new user (Sys > Admin > Users & Groups) and log in as that user. If you don't experience any problems, then your problem lies in an error in your configurations and you can remove your configuration files from your main user account

```

mkdir OLD_CONFIGS
mv ~/.mozilla OLD_CONFIGS
mv ~/.gconf* OLD_CONFIGS
mv ~/.gnome* OLD_CONFIGS
```

If that does or doesn't help (and it may not) post back and let us know.

---

### Post by f37u5g0d on 2008-07-05
If you don't use firefox but put load on your system does it still suddenly slow down and you have to restart?  My point is maybe you're just overheating.  Taking a can of compressed air, and de-dusting the inside of your case never hurts.  Especially the processor heatsink.

---


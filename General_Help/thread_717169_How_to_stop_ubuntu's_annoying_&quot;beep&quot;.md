---
title: "How to stop ubuntu's annoying &quot;beep&quot;?"
date: 2008-03-06
forum: General Help
---

### Post by ilowtf on 2008-03-06
Like title says, how can  I stop this annoying "beep"? The one that sounds when you press delete in the keyboard when there's nothing to delete, or when you press a key that you're not supposed to press?

Thanks for your help!

BTW, I'm running ubuntu gutsy on a laptop dell inspiron 6400.

---

### Post by cmnorton on 2008-03-06
Try System --> Preferences --> Sound and select the System Beep tab. Try de-selecting system beep. I don't know if that will solve your problem or not, but it seems like it is worth a try.

---

### Post by ilowtf on 2008-03-06
> **cmnorton said:**
> Try System --> Preferences --> Sound and select the System Beep tab. Try de-selecting system beep. I don't know if that will solve your problem or not, but it seems like it is worth a try.

Hey thanks that worked!!

---

### Post by dasunst3r on 2008-03-06
I added this line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```

This disables the beep system-wide.

---

### Post by ilowtf on 2008-03-06
> **dasunst3r said:**
> I added this line to /etc/modprobe.d/blacklist:
```
blacklist pcspkr
```

This disables the beep system-wide.

Thanks, I'll try that too.

---

### Post by mrsteveman1 on 2008-03-06
I usually blacklist the pcspkr module.

OpenSUSE actually compiles that module in, which really really pissed me off.

---

### Post by 3rdalbum on 2008-03-06
Is there any way to get it to play a sound file rather than do the PC speaker beep? That would be really nice!

---


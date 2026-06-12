---
title: "Screen resolution, Not high enough"
date: 2007-04-04
forum: General Help
---

### Post by lynxus on 2007-04-04
Hi guys,

Ive just installed 7.04 however having a blonde moment.

Normally theres an option somewhere to choose your monitor type.
However i cant seem to find it now?

Its only letting me use a max res of 1024x768 and yet i know the LCD panel can do the one higher..

Has anyone got any idea where i can configure it to go higher? The screen resolution dialog only lets 1024x768 be the max. @ 61hz


Cheers
G

---

### Post by dreadlord_chris on 2007-04-04
> **lynxus said:**
> Hi guys,

Ive just installed 7.04 however having a blonde moment.

Normally theres an option somewhere to choose your monitor type.
However i cant seem to find it now?

Its only letting me use a max res of 1024x768 and yet i know the LCD panel can do the one higher..

Has anyone got any idea where i can configure it to go higher? The screen resolution dialog only lets 1024x768 be the max. @ 61hz


Cheers
G

you need to reconfigure your xorg.conf

first <CNTRL><ALT><F1> to get a login prompt - login in to your account

```

sudo dpkg-reconfigure xserver-xorg

```

follow the prompts, answer all the questions - when you get to the Monitor config part choose **Medium**. Then select the resolution & refresh rate you want as default. Go through the rest and save. You should get a warning "overwriting possibly-customised configuration" - this just lets you know the name of the old (backup) config.

now type:

```

sudo /etc/init.d/kdm restart

```

If all goes well it *should* restart with your new resolution.

---

### Post by toddjumper on 2007-09-15
[COLOR="Red"]/etc/init.d/kdm[/COLOR]

When entering that, I get a response saying "Command not found"

Are you using a different version of Ubuntu?  I'm on 7.04:confused:

---

### Post by MrHippocampus on 2007-09-15
/etc/init.d/kdm is if you using KDE's login manager, youll probably want /etc/init.d/gdm if your using normal ubuntu

---


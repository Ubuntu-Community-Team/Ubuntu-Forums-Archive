---
title: "Compiz - no window borders after Gutsy"
date: 2008-05-08
forum: General Help
---

### Post by scottburton11 on 2008-05-08
EDIT: Oops, I meant Hardy. Gutsy => Hardy
[COLOR="DarkRed"]
I used Update Manager to upgrade Feisty => Gutsy.[/COLOR]

Afterwards, compiz stopped drawing window borders. It's as if there is no window management at all. Looks like this:

[IMG]http://img110.imageshack.us/img110/4442/nowindowmanagerweirdbp1.png[/IMG]

I know that Compiz is running properly otherwise. All compiz effects (transparency, windows open/close, etc.) seem to work fine. 

If I run another wm, like "metacity --replace", it properly replaces compiz and window borders appear. 

I've tried dpkg-reconfigure, and I've tried removing all of compiz and re-installing it. Anyone know what I should try next?

Thanks

---

### Post by chewearn on 2008-05-09
Install CCSM:
[apt://compizconfig-settings-manager](apt://compizconfig-settings-manager)

Open CCSM
Top panel menu > System > Preferences > Advanced Desktop Effect Settings

Go to:
Effects > Window Decoration

Under the command item, you should have /usr/bin/compiz-decorator

.

---

### Post by scottburton11 on 2008-05-09
I have CCSM, /usr/bin/compiz-decorator had USE_EMERALD set to "no". Either way, running it doesn't start any window decorations :( Same with running Emerald directly with --replace. It just hangs and never does anything. 

I'm investigating further....

---

### Post by silentb on 2008-05-11
I have the same problem. Though I have a fresh Gutsy installation.

> emerald --replace
and
> gtk-window-decorator --replace
keep running forever without anything happening. It would be helpful if these programs displayed some error message.

---

### Post by coloured on 2008-05-11
have you guys tried
> metacity --replace

---

### Post by SteelDragon on 2008-05-23
> **coloured said:**
> have you guys tried
> metacity --replace

This brings back the window decorations by removing desktop effects completely.

---

### Post by scottburton11 on 2008-06-04
> **silentb said:**
> I have the same problem. Though I have a fresh Gutsy installation.

> emerald --replace
and
> gtk-window-decorator --replace
keep running forever without anything happening. It would be helpful if these programs displayed some error message.
I'm still struggling with this, no matter what I try I can't get window decorations up with compiz running. No output whatsoever from emerald --replace, gtk-window-decorator --replace or compiz-decorator --replace, they just hang and do nothing.

Any ideas?

---

### Post by Kronie on 2008-06-04
i use compiz with emerald for window borders, and it works flawlessly.. got myself clear vista theme :D

---

### Post by castironpants on 2008-06-12
I've been having the same problem: the titlebars/borders go invisible constantly when I change window focus. It's driving me crazy! It happens with metacity themes AND emerald themes.

---

### Post by Grishka on 2008-06-12
> **scottburton11 said:**
> I'm still struggling with this, no matter what I try I can't get window decorations up with compiz running. No output whatsoever from emerald --replace, gtk-window-decorator --replace or compiz-decorator --replace, they just hang and do nothing.

Any ideas?

use fusion-icon. it takes care of many such problems.

---


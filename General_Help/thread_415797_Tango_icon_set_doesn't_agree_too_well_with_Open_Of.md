---
title: "Tango icon set doesn't agree too well with Open Office"
date: 2007-04-20
forum: General Help
---

### Post by FuturePilot on 2007-04-20
In Feisty if I set the icon theme to the Tango icons, and then start Open Office, all of the icons in Open Office are missing and in their place just text. (See attached screen shot) But if I then close OO and change the icons to something else, then reopen OO everything is back to normal. Is there anyway to fix this? Should I report a bug? I really like the Tango icons, but I can't use them if they do this.:( This is a fresh install by the way.

---

### Post by floke on 2007-04-20
What happens in OOo if you try Tools/Options/View - and then select a different set of Ooo icons from there?

---

### Post by FuturePilot on 2007-04-20
Ok, I tried that and the only ones that made a difference were the Human icons. All of the other ones didn't change anything no matter what system icon theme I was using. It's like there's only one Open Office icon theme.:confused:

---

### Post by floke on 2007-04-20
I've just tried my Tango icons and OOo and it still looks fine, so the problem must lie elsewhere.
Does this still happen with other icon themes?

---

### Post by FuturePilot on 2007-04-20
I tried out all of the different icons in Open Office with the Tango system icons set and then with the Human icons. And the only set that works in OO is the Human one. All the other ones make the OO icons disappear.

---

### Post by FuturePilot on 2007-04-20
This is interesting. I just checked the /usr/lib/openoffice/share/config directory where the icon themes are stored and there's only one icon .zip file and it's the images_human.zip. So I'm guessing I'm missing the other ones for some reason:confused:

Edit: Just booted the live CD and there's still only one icon theme. Hmmm

---

### Post by FuturePilot on 2007-04-20
Ok, figured it out. The other icon themes in Open Office are not installed by default but are available in Synaptic. And on my install, they're not installed.

---

### Post by floke on 2007-04-20
Very strange.

Well go get them dude!

---

### Post by ramjet_1953 on 2007-04-21
Yep!

Same problem here.
Itried to change to the Crystal Icon theme in my fresh install of Feisty and I ended up with no icons at all.

The developers have obviously left something out, as thsi was not a problem in Dapper, or Edgy.

Regards,
Roger :cool:

---

### Post by zhengw3 on 2007-04-21
> **FuturePilot said:**
> Ok, figured it out. The other icon themes in Open Office are not installed by default but are available in Synaptic. And on my install, they're not installed.

Thanks, good point. I just installed the package "openoffice-style-tango" and finally can use my favorite tango icon theme.

---


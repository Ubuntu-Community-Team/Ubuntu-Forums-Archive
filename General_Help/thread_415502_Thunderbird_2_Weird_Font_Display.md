---
title: "Thunderbird 2 Weird Font Display"
date: 2007-04-20
forum: General Help
---

### Post by explemonk on 2007-04-20
I installed Thunderbird 2 alongside my 1.5 install and in TB2, all of the fonts in my emails (whether they be HTML or plain text) look very off.  When using TB 1.5, they look completely normal.  I've gone over all the settings and did some googling, but I can't seem to figure out what's going on.  Is anyone else experiencing this weirdness?

Screenshot (the top of each part is 1.5, the bottom is 2.0):

---

### Post by mega on 2007-04-22
same problem here, no matter what I set it to, it's ulgy

but I have this problem in feisty with thunderbird 1.5

---

### Post by itchanddino on 2007-04-24
Same problem.  The fonts in OpenOffice look bad too.

---

### Post by itchanddino on 2007-04-25
The only "fix" I've found is to install msttcorefonts, although they are screwy with firefox.  This also fixes my OpenOffice problems.  There's gotta be some better way though.

---

### Post by mega on 2007-04-25
> **itchanddino said:**
> The only "fix" I've found is to install msttcorefonts, although they are screwy with firefox.  This also fixes my OpenOffice problems.  There's gotta be some better way though.

I have those installed, and the apple os-x fonts, but thunderbird ignores them on most emails

---

### Post by explemonk on 2007-04-25
My fonts in OpenOffice look fine.  Installing the msttcorefonts package does nothing to fix the fonts in Thunderbird for me.  I really want to use TB 2, but I can't stand reading emails in it because of this.  Hope someone can find a solution soon.

---

### Post by itchanddino on 2007-04-27
I use TB for all my school emails, it's annoying that it looks like this :/

---

### Post by mdurham on 2007-04-27
the only difference I see is size, is that what you are complaining about?

---

### Post by explemonk on 2007-04-27
> **mdurham said:**
> the only difference I see is size, is that what you are complaining about?

It's not the size that's the problem, it's the rendering.  Resizing the text doesn't get it to look better.  Also notice that for some reason, in Thunderbird 1.5 the plain text email is using a sans serif font while 2.0 is using a serif, even though they are using the exact same profile and settings.

---

### Post by FakeOutdoorsman on 2007-04-28
I'm also having troubles with this.  I can choose which fonts I like:

Edit -> Preferences -> Display -> Formatting Tab -> Fonts

But it always resets to the ugly defaults after I reboot.  It seems that the preferences file is being reset or not saved correctly.

---

### Post by tuga on 2007-04-30
The font on Thunderbird is looking nice after change the monspace font (even after reboot). I my case to Verdana.
>Edit>Preferences>Display>Formatting>Fonts>Monospace>Verdana.

---

### Post by itchanddino on 2007-05-01
Verdana isn't even a choice.

---

### Post by tuga on 2007-05-02
Verdana is installed with Microsoft Core Fonts.
Applications>Add/Remove...>Microsoft Core Fonts

---

### Post by mega on 2007-05-02
this does not fix it for me

the preview window ignores my font setting and picks really really nasty fonts, I even have "allow messages to use custom fonts" unchecked so they cannot

I believe it's only html format emails that look really really nasty

---

### Post by explemonk on 2007-05-04
Well, I cannot recommend this as a fix, but it worked for me:  I upgraded to Gutsy.  Now all my fonts in Thunderbird 2.0 are just as they were in 1.5.

---

### Post by altonbr on 2007-05-19
The transition from 1.5 to 2.0 for Thunderbird was messy for me too: [http://ubuntuforums.org/showthread.php?t=317708](http://ubuntuforums.org/showthread.php?t=317708)

---

### Post by FakeOutdoorsman on 2007-09-08
As I mentioned before, my preferences for monspace fonts were not being saved (on a FAT partition).  I would choose Courier New instead of monospace.  However, the fonts would eventually revert to the default monospace.  I looked at my prefs.js file before and after and noticed that my font preference wasn't persistant:

```

user_pref("font.name.monospace.x-western", "Courier New");

```

For some reason the above string will vanish after I reboot and make my monospace fonts ugly again.

---


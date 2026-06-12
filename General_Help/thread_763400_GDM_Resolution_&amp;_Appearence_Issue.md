---
title: "GDM Resolution &amp; Appearence Issue"
date: 2008-04-23
forum: General Help
---

### Post by Fehrant on 2008-04-23
(using GNOME. Have restricted nVidia drivers installed and working properly. AMD processor)

I've been pretty much been able to solve (or configure, whenever necessary) all the issues that I came across. For a complete newbie like myself, I think that's good enough. However, for this particular issue, I cannot find straightforward solution.

It appears that the GDM cannot save the settings. No matter which themes I choose, and no matter what resolution I set, it always goes back to default. I don't mind the themes much, but sometimes with the resolution it doesn't let me change it back once logged in, forcing me to restart to fix the issue.

I'd rather not *remove* resolutions from the conf file. I mean, I'm pretty confident I'll be using the one I have for a long time if not forever, but you never know.

---

### Post by stream303 on 2008-04-23
If it's a case of the gdm resolution being wrong, the fix for me was to add a "virtual" line to my /etc/X11/xorg.conf file just before the "modes" and make it match my native resolution.

```
SubSection "Display"
.
.
virtual 1024 768
modes "1024x768" "800x600"
.
.
.EndSubSection
```

note there is no "x" in the virtual line, nor quotes.

Does this help?

---

### Post by Fehrant on 2008-04-23
Hmm, that's weird. My xorg.conf file does not have a display section. I guess that would explain the issues.

Thanks for the info.

---


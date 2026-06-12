---
title: "OOo Writer crashes with templates"
date: 2008-01-24
forum: General Help
---

### Post by Krydahl on 2008-01-24
This is a weird one. My OOo was running fine. Suddenly, whenever I try to create a new document in writer by using a template, OOo crashes.

If I click new it opens a doc using my default template with no trouble. If I go through file-> new->templates and docs and select any template (even the default) it immediately crashes.

It's only started doing this in the last few days. I haven't changed anything I can track down (unless upgrading to a widecreen monitor counts :confused:).

Googling all I've come up with is references to templates not working if you haven't got OOo base installed - but I have, I'm using the default set up from my Gutsy install.

I've seen threads on different themes causing problems, so I've tried it with Compiz turned off and using the human theme (that was the default, wasn't it?) Still does the same thing.

Any suggestions on what I try next gratefully received.

---

### Post by Krydahl on 2008-01-27
By coincidence, I've just installed Gutsy on a new latop. Writer works fine on there with the same templates.

I've tried deleting the .openoffice.org2 folder in home. The problem persists so it can't be a config option. Anyone got any other ideas?

---

### Post by Hagar Delest on 2008-02-01
As a workaround, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Krydahl on 2008-02-01
Thanks, I might have to try that.

I've tried using synaptic to remove OOo and then reinstall it. I thought it had solved the problem at first. I didn't have the packages openoffice.org-gnome and openoffice.org-gtk installed (which meant my theme didn't match and a few other integration problems. Once I added those packages the templates stopped working again. Don't know if that gives any clue to what the problem is.

I've also noticed that it's not just opening the templates. If I use the new button -> templates and documents it crashes OOo whatever I try to open from that window.

---


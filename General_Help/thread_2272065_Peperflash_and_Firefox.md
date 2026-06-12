---
title: "Peperflash and Firefox"
date: 2015-04-03
forum: General Help
---

### Post by SuperFreak on 2015-04-03
I installed Peperflash according to [http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html]("http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html") while regular Flash was still installed (ver 11.2). Now both Flash plugins are enabled. Should I remove the old Flash 11.2 (how?). Reason I am asking is Firefox crashes quite frequently now (ver 37)

---

### Post by kerry_s on 2015-04-03
you should just disable it in add ons, you may need for other sites or if an update kills it.

---

### Post by SuperFreak on 2015-04-03
> **kerry_s said:**
> you should just disable it in add ons, you may need for other sites or if an update kills it.

If I disable Flash it disables both flash and pepperflash on reboot

---

### Post by kerry_s on 2015-04-04
i see, 1 or the other,

sudo apt-get purge flashplugin-installer

---

### Post by SuperFreak on 2015-04-04
> **kerry_s said:**
> i see, 1 or the other,

sudo apt-get purge flashplugin-installer


Thanks that got rid of the older Flash plugin. Unfortunately Firefox still crashes (on exit) so the problem must lie elsewhere

---

### Post by pissedoffdude on 2015-04-04
Does it crash if you disable flash entirely?  If so, it's the pepper flash plugin.  The firefox implementation of it is really nothing more than a 'hack' so you should expect to see instability.

---

### Post by SuperFreak on 2015-04-04
> **pissedoffdude said:**
> Does it crash if you disable flash entirely?  If so, it's the pepper flash plugin.  The firefox implementation of it is really nothing more than a 'hack' so you should expect to see instability.

True . I had trouble with a few other plugins which was resolved by disabling them so I may have to lose pepperflash too

---

### Post by pissedoffdude on 2015-04-04
> **SuperFreak said:**
> True . I had trouble with a few other plugins which was resolved by disabling them so I may have to lose pepperflash too

Boo.

Yeah, they can cause some instability.  Just be sure it is pepper flash for sure, otherwise we should investigate your firefox installation.  I wish adobe provided an updated flash, but yeah, what can we do?  Narrow it down and maybe we can find a workaround for your main use-case.

---

### Post by SuperFreak on 2015-04-04
> **pissedoffdude said:**
> Boo.

Yeah, they can cause some instability.  Just be sure it is pepper flash for sure, otherwise we should investigate your firefox installation.  I wish adobe provided an updated flash, but yeah, what can we do?  Narrow it down and maybe we can find a workaround for your main use-case.
The problem was not pepperflash and to be honest I am not sure which addon was the problem but I disabled a few including the non default theme and it is working now.

Thanks:p

---


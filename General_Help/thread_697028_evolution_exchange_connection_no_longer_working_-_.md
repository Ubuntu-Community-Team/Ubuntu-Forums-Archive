---
title: "evolution exchange connection no longer working - possibly after updates"
date: 2008-02-14
forum: General Help
---

### Post by vanndrage on 2008-02-14
hello, just a couple days ago i rebooted my laptop after doing a bunch of updates and 1 or more required to reboot. after that i opened up evolution as usual and it just shows my local inbox and my exchange connection is listed but nothing under it. the arrow is just pointing to the right and not down. i have tried the obvious stuff like click on it or the arrow to drop down the list of folders and nothing. i have also tried removing the exchange account, closing evolution and then going back into evolution and re-entering the exchange account and then again restarting evolution but still same thing happens. i am not sure if this was maybe a recent update or something. i do not reboot my laptop unless required to by something like an update so this was the first set of updates in a long time that required a reboot and it started after that. i have also verified my exchange account is working by logging into my web based exchange. any help is greatly appreciated.

---

### Post by jken146 on 2008-02-14
Try removing the .evolution folder in your home directory (probably best to rename it rather than delete it so you have a backup) and see if this helps.  Evolution and exchange don't seem to play nicely all the time.

---

### Post by vanndrage on 2008-02-15
> **jken146 said:**
> Try removing the .evolution folder in your home directory (probably best to rename it rather than delete it so you have a backup) and see if this helps.  Evolution and exchange don't seem to play nicely all the time.
thanks for the reply, i tried this and same thing happens. any other ideas?

---

### Post by pete on 2008-02-15
I'm seeing the same behavior.  Started yesterday morning after a series of updates and reboot (which may or may not have been related).

Evolution now keeps prompting for my Exchange password, which I have confirmed works fine via both OWA and Outlook.  Tried renaming my .evolution folder, but no change.  I have also tried setting up my Exchange account in a fresh install of Evolution on a different machine, but can't even get past the authentication step in the setup assistant--it hangs for a while on the "Enter password" window, and then tells me "Could not configure Exchange account because an unknown error occurred.  Check the URL, username, and password, and try again."

I don't recall seeing any Evolution-related items in any of the recent updates.  Is it possible there's been an Exchange update that might have broken Evolution's connector?

---

### Post by allegre on 2008-06-16
First time Evolution user for Exchange, and I'm seeing the same errors reported previously.

Evolution configuration does not progress using the standard configure tool past the [authenticate] or using the /usr/bin connector.

Error displayed is "Could not configure Exchange account because an unknown error occurred. Check the URL, username, and password, and try again."

Tried every variant of url, bare http, https, IP/ IP/OWA, IP/exchange, /OWA, /exchange.
Tried username, domain/username, domain\username, DOMAIN\username, etc.
Tried correct password, wrong password, no change to message.

running Hardy Heron, full updates as of Jun 17,

help?

---

### Post by boobldo on 2008-07-22
I now have exactly this same problem.  Literally evolution worked fine yesterday.  I did not install any updates, but today it does not work at all.  I am continually prompted for my password when I do "send and receive", it either hangs.  I see down an error ""Error while scanning exchange folders in "Exchange server ##.##.##.##""

Help please.  This is debilitating as I can't get my corporate email now and my whole team is on evolution.  I am worried that my entire user base will be without email soon.

Thanks!

---


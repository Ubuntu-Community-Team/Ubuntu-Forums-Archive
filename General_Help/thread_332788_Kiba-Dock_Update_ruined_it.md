---
title: "Kiba-Dock Update ruined it"
date: 2007-01-06
forum: General Help
---

### Post by CCBalla10 on 2007-01-06
Hey guys have Kiba-Dock CVS installed and today's update (1-6-2007) ruined it.  when i go to terminal and type kiba-dock it returns 

austin@myUbuntu:~$ kiba-dock
Segmentation fault (core dumped)
austin@myUbuntu:~$

Anyone know what happend?

---

### Post by thebinz on 2007-01-07
Same thing happened to me. Hopefully this gets fixed soon. 

*Bump*

---

### Post by Steveway on 2007-01-07
Gravedigga (danielb) is working on a plugin-system for Kiba-dock and there are still some problems with it.
He's working on a fix, at the meantime you should stick with the previous version.

---

### Post by CCBalla10 on 2007-01-08
ah i think i'll just wait....i'll just not have to be lazy and actually go to applications and pick what i want lol :D

---

### Post by thebinz on 2007-01-09
It would be greatly appreciated if someone would post a reply or new thread when the update is fixed. That way when i go to install the update, i will install a working version. 

I uninstalled the update so right now that annoying orange icon is sitting in my system tray just asking for me to update it.

Grr little bugger. 

I'm a bit of a minimalist when it comes to the appearance of my desktop so i hate it when there are icons in my system tray that don't need to be there.

Anyways,
Peace & Love.

---

### Post by CowzRule on 2007-01-09
> **thebinz said:**
> It would be greatly appreciated if someone would post a reply or new thread when the update is fixed. That way when i go to install the update, i will install a working version. 

I uninstalled the update so right now that annoying orange icon is sitting in my system tray just asking for me to update it.

Grr little bugger. 

I'm a bit of a minimalist when it comes to the appearance of my desktop so i hate it when there are icons in my system tray that don't need to be there.

Anyways,
Peace & Love.
Go into "Synaptic Manager", find "Kiba-Dock" and click on it. Now go up to "Package" and select "Lock Version". That will stop Kiba-Dock from being updated. It'll also stop it from showing in Update Manager so you don't have to worry about unselecting it if there are other updates to get. When you learn that Kiba-Dock is fixed, just go back into Synaptic and repeat to unlock it.

---

### Post by thebinz on 2007-01-09
Great and much appreciated tip CowzRule.

Thanks! :cool:

---

### Post by CowzRule on 2007-01-09
> **thebinz said:**
> Great and much appreciated tip CowzRule.

Thanks! :cool:Glad I could help :)

---

### Post by random guy on 2007-01-11
does anyone know where i can get a deb of the old version.  i was silly enough to upgrade aswell and i usually isntall from the cvs but i cant really use the cvs now.

thanks for the help

---

### Post by d3v1ant_0n3 on 2007-01-11
Uninstall kiba-dock, then recompile it from the cvs- it's been fixed and is working again.

---

### Post by CCBalla10 on 2007-01-13
Deviant could you show me how to do this?

---

### Post by CCBalla10 on 2007-01-13
^ Or can anyone help me recompile the Kiba-Dock CVS....the one that works

---

### Post by franestepona on 2007-01-14
Try this [http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)

---

### Post by CCBalla10 on 2007-01-15
thanks for the link but i'm close.... when running the steps in terminal i get this....

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by CCBalla10 on 2007-01-15
^Bump!

---

### Post by CCBalla10 on 2007-01-16
Nevermind **Solved** used this how-to [HTML]http://ubuntuforums.org/showthread.php?t=268645&highlight=Kiba-dock[/HTML]

---


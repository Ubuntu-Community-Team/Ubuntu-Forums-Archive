---
title: "&quot;custom&quot; settings option disappeared in hardy (8.04)"
date: 2008-04-30
forum: General Help
---

### Post by deruberhanyok on 2008-04-30
Hey all,

I've recently installed the final release of 8.04. It was a clean install, not an upgrade, though I did preserve my /home directory. I made sure to install ccsm ("Advanced Desktop Effects Settings") and can access the settings and change them without issue.

Anyways, in 7.10, installing ccsm added a "custom" option to the "visual effects" tab of the "appearance" control panel, but that doesn't seem to have happened here.

Oddly, when I first noticed this it seemed to reset my effects settings to the default "normal" effects but didn't mark it as such.

Has anyone else run across this? Is this something I should file a bug report about?

---

### Post by seismicmike on 2008-04-30
I have a similar problem. I have CCSM installed and supposedly configured the way I want it, but when I Go to Change Desktop Background > Visual Effects, I only see "None", "Normal" and "Extra".

Moreover, I cannot even set it to Normal or Extra. It will only allow me to set it to None. If I try to do the other to, the screen flashes and it says "Desktop Effects Could Not Be Applied" but gives me no reason as to why nor any kind of information I could use to get support.

---

### Post by mtbsoft on 2008-05-01
deruberhanyok - I can confirm the same issue on my laptop, CCSM and conpiz works but not the same way as Gutsy.

seismicmike - the type of graphics card you have may be a clue, ATI and NVIDIA have been problematic in the past (and present) though I, myself, am delighted with the current ATI improvements.  Search for the error you are getting "Desktop Effects Could Not Be Applied" and you should be able to start diagnosing the problem.

---

### Post by deruberhanyok on 2008-05-04
seismicmike - it sounds like the 3d drivers for your graphics haven't been installed. If you have an nvidia or ATI card / onboard solution you probably need to enable the restricted driver and install it... if it's Intel graphics, I think they are all open source so I'm not sure what else to suggest.

mtbsoft - I found a bug report for this here:

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/210525](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/210525)

I went to synaptic and installed "simple-ccsm" and the custom option has appeared for me again. Unfortunately I can't remember if I installed ccsm via synaptic or from add/remove "advanced desktop effects settings" but whichever one I did seems to have not required the above package.

Hopefully this fixes it for you as well.

---

### Post by mtbsoft on 2008-05-06
> **deruberhanyok said:**
> mtbsoft - I found a bug report for this here:

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/210525](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/210525)

< snip >

Hopefully this fixes it for you as well.
Thanks for the info. but, to be honest, I'm not too concerned - once I get it configured correctly it won't be touched much and since I can get to it the other way it's not a real problem.

---

### Post by altonbr on 2008-05-08
I have 'compizconfig-settings-manager' installed and I can enable 'normal' and 'extra' settings which means my nVidia driver is set up properly (see: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)) and I STILL see no 'custom' button. What happened?

---

### Post by Forlong on 2008-05-09
You have to install Simple-CCSM now to make it appear:
```
sudo apt-get install simple-ccsm
```

See [http://bugs.launchpad.net/bugs/191650](http://bugs.launchpad.net/bugs/191650)

---

### Post by mtbsoft on 2008-05-10
> **Forlong said:**
> You have to install Simple-CCSM now to make it appear
Perhaps it depends on install order but installing simple CCSM after "normal" CCSM does add the custom radio option and button but that button then only displays the simple-CCSM dialog, not the full CCSM screen.

If all you are wanting is the extra radio button to enable fast toggling between custom and one of the other three then this will work, otherwise you will still need to use the CCSM from the main menu.

---

### Post by Roasted on 2008-05-12
After installing simple ccsm, can I still use the advanced one to make changes? Will the simple vs advanced clash with one another?

Also - How in the world do I edit a key to initiate the cube? For some reason it's not liking me... I want my key to be ALT Z for what it's worth...

---

### Post by mtbsoft on 2008-05-12
> **Roasted said:**
> After installing simple ccsm, can I still use the advanced one to make changes? Will the simple vs advanced clash with one another?
Yes you can, though I actually uninstalled simple-ccsm as its functionality is too limited for me and I don't need to keep toggling compiz on and off.

---


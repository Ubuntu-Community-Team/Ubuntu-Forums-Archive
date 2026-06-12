---
title: "Display Corruption after Login"
date: 2018-11-28
forum: General Help
---

### Post by kidhash on 2018-11-28
Hey. I'm having a weird display corruption issue since upgrading to Ubuntu 18.10. I have a 5 year old Dell XPS 13 Developer Edition, that came preinstalled with some much older version of Ubuntu, that I have kept upgraded. This laptop has no standalone graphics card, just an Intel HD Graphics 4400. I ran Memtest and it reported no problems.

This problem happens reliably if I log in immediately after gdm3 loads, and usually doesn't happen if I wait 15 seconds or so once gdm3 has loaded. 
The display becomes all corrupted (like someone was using a large magnet behind an old CRT display), even when using an external monitor, yet taking a screenshot results in a picture of a normal display, without the weird graphics corruption.

This seems to only happen when I boot into 'Ubuntu' xsession, but not when I use 'Ubuntu on Wayland'.


Could anyone provide some advice on how to troubleshoot this?

---

### Post by logix2 on 2018-11-28
One thing that comes to mind is to see if this also happens when using LightDM, or only with GDM. You can install LightDM using:

```
sudo apt install lightdm
```

You can switch between GDM and LightDM (once both are installed) by using this command:

```
sudo dpkg-reconfigure gdm3
```

In case you later remove lightdm, make sure to run "sudo apt autoremove" to remove any dependencies lightdm leaves behind.

---

### Post by kidhash on 2018-11-28
> **logix2 said:**
> One thing that comes to mind is to see if this also happens when using LightDM, or only with GDM. You can install LightDM using:

```
sudo apt install lightdm
```

You can switch between GDM and LightDM (once both are installed) by using this command:

```
sudo dpkg-reconfigure gdm3
```

In case you later remove lightdm, make sure to run "sudo apt autoremove" to remove any dependencies lightdm leaves behind.

Thank you, I should have included in my post that I had already tried this. Exact same behaviour with lightdm.

---


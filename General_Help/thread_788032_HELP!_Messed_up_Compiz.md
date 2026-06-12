---
title: "HELP!: Messed up Compiz"
date: 2008-05-09
forum: General Help
---

### Post by IHATEDLINK on 2008-05-09
Hey
I was playing with Compiz-Fusion and i think I broke it.
I was fallowing a guide for doing the "Genie Effect" from Mac OS X on Compiz, I had already done it a couple of times, this never happened to me.
Now i have absolutely NONE desktops effects. If I try to change the settings on the System>Appearance>Desktop Effects nothing happens. The screen flashes, a dialog prompts asking if I want to keep this settings, clicked yes and then NOTHING, not even one desktop effect, then i go again to the desktop Effects tab and the desktop effects are set to "None" again.
Also tried changing some stuff on Settings>Preferences>Advanced Desktop Effects Settings with no luck. 
AWN doesn't work either
Please HELP!!

I was fallowing [THIS]("http://ubuntuforums.org/showthread.php?t=557491&highlight=magic+lamp") guide

---

### Post by Perfect Storm on 2008-05-09
Try via terminal;
```
compiz --replace
```
It might spit out some errors.

---

### Post by IHATEDLINK on 2008-05-09
> **Artificial Intelligence said:**
> Try via terminal;
```
compiz --replace
```
It might spit out some errors.

Did it, I think something is wrong:

```
paco@Paco-Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0171 (rev a3) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault

```

Should I reinstall every compiz package via synaptic? :S

---

### Post by Perfect Storm on 2008-05-09
What about use the guide to revert the changes?

Properly downgrade the package the guide suggested as well.

---

### Post by IHATEDLINK on 2008-05-09
> **Artificial Intelligence said:**
> What about use the guide to revert the changes?

Properly downgrade the package the guide suggested as well.

I don't want to revert the changes, LOL
I had already done this with another hardy installation with no problems at all.
How do I downgrade the packages?
Shouldn't I reinstall them?

---

### Post by Perfect Storm on 2008-05-09
I just checked the guide date - it's outdated as it request you install a lower version of compiz on Hardy. It suggest 0.5.5~git20070921+3v1ubuntu0 where in hardy it's 0.7.4

You can find the package here and install the default one: [http://packages.ubuntu.com/search?keywords=compiz&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=compiz&searchon=names&suite=hardy&section=all)

---

### Post by IHATEDLINK on 2008-05-09
> **Artificial Intelligence said:**
> I just checked the guide date - it's outdated as it request you install a lower version of compiz on Hardy. It suggest 0.5.5~git20070921+3v1ubuntu0 where in hardy it's 0.7.4

You can find the package here and install the default one: [http://packages.ubuntu.com/search?keywords=compiz&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=compiz&searchon=names&suite=hardy&section=all)

Nevermind.
I just reinstalled all the compiz packages via synaptic and disabled my nVidia restricted driver. Then restarted, enabled the driver, reinstalled and voila, fixed. :)

Thanks a lot for your help!

---


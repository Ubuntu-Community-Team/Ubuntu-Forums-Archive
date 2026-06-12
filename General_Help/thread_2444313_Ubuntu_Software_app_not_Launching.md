---
title: "Ubuntu Software app not Launching"
date: 2020-05-28
forum: General Help
---

### Post by mr-bear on 2020-05-28
Hey there,

So when I click on the Ubuntu Software it doesn't load.

It was working and then boom, it stopped.

Any ideas?

Please keep in mind I am a total newb at this.

---

### Post by CelticWarrior on 2020-05-28
First of all make sure the system is fully updated:

```
sudo apt update && sudo apt full-upgrade
```

---

### Post by mr-bear on 2020-05-28
Done

It said;

Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What should I do next?

---

### Post by Dennis N on 2020-05-28
What version of Ubuntu? 20.04, 18.04, or 19.10?

---

### Post by mr-bear on 2020-05-28
> **Dennis N said:**
> What version of Ubuntu? 20.04, 18.04, or 19.10?

Apologies, 20.04

I uninstalled it following an article and reinstalled it, but it's now no where to be found on my computer. I'm using the regular Software app at this point, as Ubuntu Software appears to have completely left the building.

Do I need it? Or will regular Software get the same job done?

Thanks for the help in advance folks.

:)

---

### Post by Dennis N on 2020-05-28
In 20.04, the icon labeled 'Ubuntu Software' is a snap package version of gnome-software. The icon labeled 'Software' is the Ubuntu repository version of gnome-software. You can use either one - they appear the same to the user, and both can handle snaps as well as regular packages from the repository.

---

### Post by Impavidus on 2020-05-28
They should both work, although some problems have been reported with the snap version. You don't need either of them, as there are more tools for handling software, notably synaptic (doesn't handle snaps) and various command line tools.

---

### Post by mr-bear on 2020-05-28
well now there is something called Snap Store on my machine after reinstalling the Ubuntu Software, so I guess that's that. 

Thanks guys, I appreciate the help. You rock :)

---


---
title: "Black Screen after Updating PCmanFM"
date: 2016-01-06
forum: General Help
---

### Post by ben147 on 2016-01-06
I am using Lubuntu LTS 14.04 and tried to update PCmanFM and the LibFM it uses. I did not find a proper way, from the synaptic it did not update the LibFM. I had to do this because of an issue that was solved in LibFM. So I uninstalled PCmanFM and autoremoved all packages afterwards. Then I reinstalled PCmanFM with success and now the updated LibFM was used. However, when rebooting and after logging in I get a black dark grey screen with a mouse cursor and thats it - nothing else. Anyone an idea how to solve this?

---

### Post by claracc on 2016-01-06
When you have removed pacmanfm I suspect you have removed following packages too: lubuntu-core lubuntu-default-settings lubuntu-desktop lxde-core. You can try to look for these packages in your system.I there isn't lubuntu-desktop,  try to install lubuntu-desktop again: ```
sudo apt-get install lubuntu-desktop
```

Please see: [http://ubuntuforums.org/showthread.php?t=1942034](http://ubuntuforums.org/showthread.php?t=1942034)

---

### Post by mörgæs on 2016-01-06
No, lubuntu-desktop is a metapackage (often referred to as a shopping list). If it's lost there is no harm done and there is no point in adding it.

---


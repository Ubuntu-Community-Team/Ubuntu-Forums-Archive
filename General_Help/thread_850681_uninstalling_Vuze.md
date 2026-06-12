---
title: "uninstalling Vuze"
date: 2008-07-05
forum: General Help
---

### Post by zer0net on 2008-07-05
hi guys, 
i'm new to linux, I managed to install vuze using the instructions from following site
[http://www.computerhaters.com/howto/linux/linux-applications/install-azureus-vuze-in-ubuntu/](http://www.computerhaters.com/howto/linux/linux-applications/install-azureus-vuze-in-ubuntu/)

when i run it ( only works from terminal) it downloads some update and then gives me a message that /usr/shared/vuze is not writeable and updates will fail. and after that when i close it, it opens up all by itself.

I just wanna uninstall it.
can anyone please help me?

Thank you

---

### Post by f37u5g0d on 2008-07-05
sudo apt-get uninstall vuze.  If that doesn't work open synaptic package manager and search the word "vuze" and mark it for complete removal and then apply.

---

### Post by cariboo on 2008-07-05
See as you installed it from a tarball you will have to remove it manually. From the looks of it you will have to remove :

```
/usr/share/applications/Azureus.Desktop
/usr/share/azureus
/usr/bin/azureus
```

How you remove these files and directories is up to you. I would suggest in a terminal run:

```
gksu nautilus
```

and navigate to the directories in question.

Jim

---

### Post by zer0net on 2008-07-06
so ran that command in terminal and navigated to the locations u mentioned and manually deleted those files. I hope that its now deleted.

Thank you very much

---

### Post by heatblazer on 2008-07-06
You are welcome :)

---

### Post by heatblazer on 2008-07-06
> **heatblazer said:**
> You are welcome :)

Sorry, messed the forum windows, this was not for the ubuntuforums :)

---

### Post by spike_naples on 2009-03-27
I hate Vuze for Ubuntu.

I would recommend KTorrent or Deluge.

Vuze doesnt even uninstall correctly. To uninstall go to SPM and search for Azureus then choose to completely uninstall all packages to get rid of the remnants of Vuze.

---

### Post by greylander on 2009-04-13
Cannot uninstall vuze using synaptic or apt-get uninstall, if it was not installed by those means.  I want to uninstall it as well, and I don't even remember what process I used to install it.  (Quite possibly the same was as the OP).

I agree, vuze is very annoying like some combination of adware and social networking.  I find that utorrent (microtorrent) works great under Wine.

@cariboo907:   How sure are you that those are the only files that need to be deleted?

---

### Post by bonbeeno on 2009-07-30
Lol I am not even apart of this thread but it helped me.

Thank You,

---

### Post by Galactic_Overlord on 2009-12-09
Vuze is definitely a pain in the *** that doesn't set up correctly.

---


---
title: "Skype not showing up in the top bar"
date: 2013-05-05
forum: General Help
---

### Post by MaZaMo on 2013-05-05
I have ubuntu 13.04. I just installed the skype .deb from skype.com that's for ubuntu 12.04, since it's the newest version they have. But it's not working! When I open it it doesn't show up in the top bar of unity, so i need to keep it running in the launcher. Otherwise, if it's closed from the launcher, it's still running but there's no way to get to it or quit out of it except for logging out!

---

### Post by timgood on 2013-05-05
Uninstall Skype and then add the partner repository and install from there. It will pull down the necessary dependencies to allow Skype to add the icon in the top bar.

---

### Post by Hexxus on 2013-05-22
> **timgood said:**
> Uninstall Skype and then add the partner repository and install from there. It will pull down the necessary dependencies to allow Skype to add the icon in the top bar.


I have done 

```
Sudo apt-get purge skype
```

Search for skype and cannot find it on my machine and its not running.

```
Sudo apt-get update && sudo apt-get install skype
```

After having the problem, I launched skype and found that it was still somehow running. You may need to run top and kill the process. After doing so and re-launching skype this fixed my issue. 

Thanks!

---


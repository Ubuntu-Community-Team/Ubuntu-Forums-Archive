---
title: "How to completely uninstall WINE"
date: 2020-01-14
forum: General Help
---

### Post by lwalper on 2020-01-14
I installed WINE and tried to run a couple of Win apps -- didn't really work out very well. How do I remove WINE? I have followed the [askubuntu suggestions]("https://askubuntu.com/questions/1111353/unable-to-remove-wine") to no avail. There are still icons on my desktop and WINE folders/files I would like to delete. When I try to delete the files I'm told that I am not the owner and can't delete them. Have tried chmod without success. Any help is appreciated.

And BTW, since I'm just trying to figure this all out and have a fairly new install, it might just be easier to reformat the partition and start from again from scratch with a clean install??

---

### Post by CelticWarrior on 2020-01-14
How did you install wine?

---

### Post by bernard010 on 2020-01-14
sudo apt purge wine*
sudo apt autoremove rm -r .wine

Restart 
dpkg --list | grep wine 

To see if Wine is still installed.

---

### Post by lwalper on 2020-01-14
> **CelticWarrior said:**
> How did you install wine?

I used the process outlined at [https://wiki.winehq.org/Ubuntu]("https://wiki.winehq.org/Ubuntu")

---

### Post by lwalper on 2020-01-14
> **bernard010 said:**
> sudo apt purge wine*
sudo apt autoremove rm -r .wine

Restart 
dpkg --list | grep wine 

To see if Wine is still installed.

OK, thanks. I'll try that next time. I have just cleared the Ubuntu partition and reinstalled 18.04 from scratch. That should fix it. At least I'm getting more proficient at installing the OS.;)

---

### Post by CelticWarrior on 2020-01-15
Now, if you intend to install Wine again, always prefer the version already in the official Ubuntu repositories. And if you need different versions then install PlayonLinux to mange them in different containers.

Of course, avoid emulated software as much as you can, always prefer native versions or alternative native software. If you really need that much Windows programs then use Windows.

---

### Post by bernard010 on 2020-01-15
I have installed Ubuntu over and over again also and i agree... 
You can get the Snap: ' Synaptic ' , Type it in the snap search bar. It is the Synaptic Package Manager.
Here is the documentation: [URL="https://help.ubuntu.com/community/SynapticHowto"]https://help.ubuntu.com/community/SynapticHowto

[/URL]Install the entire wine package if you need it again. Or uninstall it easier with Synaptic.

---


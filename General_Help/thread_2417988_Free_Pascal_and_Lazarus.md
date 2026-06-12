---
title: "Free Pascal and Lazarus"
date: 2019-04-30
forum: General Help
---

### Post by radu19842 on 2019-04-30
Good morning , i need to install these two elements on my xubuntu 18.04 , on windows was so easy but on xubuntu i have no ideea ! I don't want to get back to windows ever ,anyway on windows i only installed lazarus as a *.exe witch was 2 in 1 as he contained both F.P. and Lazarus in one . Thank you very much ! :)

---

### Post by lisati on 2019-04-30
Is [this link]("http://wiki.lazarus.freepascal.org/Install_on_Ubuntu") of some help? (And no, I haven't tried it with a more recent version of Ubuntu)

---

### Post by The Cog on 2019-04-30
> **lisati said:**
> Is [this link]("http://wiki.lazarus.freepascal.org/Install_on_Ubuntu") of some help? (And no, I haven't tried it with a more recent version of Ubuntu)
Well, I just tried ```
apt search lazarus
``` and it returned lots of info. I think this will do the trick: ```
sudo apt install lazarus
```

---

### Post by radu19842 on 2019-04-30
**lisat** and **The Cog** thank you so much , i will try latter since i am not at home for the moment but i hope that contains both Free Pascal and Lazarus and not just the Lazarus IDE ! A great day ! ;)

---

### Post by radu19842 on 2019-04-30
I have found a video on youtube on how to install Free Pascal and Lazarus [https://youtu.be/mU7d2ubaysM]("https://youtu.be/mU7d2ubaysM") i just downloaded a package from the next link [https://www.ubuntuupdates.org/package/core/bionic/universe/base/lazarus]("https://www.ubuntuupdates.org/package/core/bionic/universe/base/lazarus") downloaded and installed the last one bellow called **APT INSTALL** , then i tested it and it works , it has Free Pascal with compiler,libraries,etc. and the Lazarus IDE , i know this cause i searched in Synaptic Package Manager ! What do you think . P.S.-I run Xubuntu 18.04 Bionic Beaver witch has XFCE Desktop and o installed debian version of FPC+Lazarus , is there any problem ? All the best ! :)

---

### Post by The Cog on 2019-04-30
OMG what is that video doing??? You don't need to go downloading random stuff from teh interwebs. This isn't windows. Just run the command **sudo apt install lazarus** and apt will go and fetch lazarus from the official repos. No searching the web for pirate versions or malware infected versions. 

You should always just check if apt can install what you want first. Packages that apt fetches from the repositories and installs have been compiled especially for Ubuntu, sometimes with ubuntu-specific fixes. And you get notified when there are security updates to them. Only search teh interwebs when you have a really good reason, like the app you want is not in the repos, or (as sometimes happens) you need a later version than is in the repo for a new feature. The repos really have an astonishing amount of software in them, and they are a trustworthy source.

Incidentally, the repos for Ubuntu 19.04 contain lazarus v2.0.

---

### Post by radu19842 on 2019-04-30
Oh no so what should i do now **The Cog** , uninstall it from Synaptic Package and then reinstall it trough terminal , can ny system be in any danger ? Thank you and all the best !

---

### Post by The Cog on 2019-04-30
Do you trust that web site not to put adware/malware in the package? If so, and it works, you're probably OK. It's just that the normal and safer thing to do is to use apt to download the packages from the official Ubuntu repos whenever possible. I have very little non-repo stuff installed on my PCs. I've not heard of ubuntuupdates before, and so to me it's just another web site trying to get you to install their stuff. Maybe I'm doing them an injustice, maybe not.

---

### Post by radu19842 on 2019-04-30
> **The Cog said:**
> Do you trust that web site not to put adware/malware in the package? If so, and it works, you're probably OK. It's just that the normal and safer thing to do is to use apt to download the packages from the official Ubuntu repos whenever possible. I have very little non-repo stuff installed on my PCs. I've not heard of ubuntuupdates before, and so to me it's just another web site trying to get you to install their stuff. Maybe I'm doing them an injustice, maybe not.
Good evening , i have reinstalled Xubuntu 18.04 Bionic Beaver x64 and will do it the way you sugested to do , this way i "feel" safer :) Thank you very much for your help,i am new to linux and i do enjoy xubuntu ! 
All the best and have good evening ! :)
P.S. - Am i right when i say i dont need antivirus/antimalware on xubuntu if i use only safe ubuntu/linux software ?

---

### Post by sisco311 on 2019-04-30
The "APT INSTALL" link on that page (for now) is just an [AptURL]("https://help.ubuntu.com/community/AptURL") so you should be fine. The package was most likely installed via your local package manager.

To check the source and version of the installed package, you can run:
```
apt policy lazarus
```

EDIT: too late :)


In general don't do this: [https://www.gnu.org/fun/jokes/evilmalware.html](https://www.gnu.org/fun/jokes/evilmalware.html) :)

---


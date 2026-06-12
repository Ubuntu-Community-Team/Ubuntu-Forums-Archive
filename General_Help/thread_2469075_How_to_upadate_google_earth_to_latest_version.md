---
title: "How to upadate google earth to latest version"
date: 2021-11-18
forum: General Help
---

### Post by Ralph L on 2021-11-18
I am running xubuntu 18.04.  I have google earth installed in /opt/google. I don't remember how I installed it, but the location must have been picked by the installer, because I would not have installed it there. When I bring up google earth, it asks if I want to install a newer version. I clicked download and it asked me where I want to save it. At this point I am unsure what to do. Should I save it to /opt in a new folder or should I do something else? What are the other steps for getting it correctly installed? Should I delete the current version?
Any help appreciated.......

---

### Post by monkeybrain20122 on 2021-11-18
If you installed google-earth pro by downloading the .deb from [here]("https://www.google.com/earth/versions/"), then it should add a repository and upgrade normally (via sudo apt upgrade) like all other software.
> 
I clicked download and it asked me where I want to save it. At this point I am unsure what to do

You just download an installer (a .deb file) which you can put anywhere. To install it, right click, the software store will open and do the rest of the work.

---

### Post by Impavidus on 2021-11-19
If you install normally from a .deb, the installer will add a repository, from which GE gets upgraded automatically. There are some things that can go wrong. When you release upgrade, third party repositories like this get disabled, so you have to enable them again after the release upgrade. Or you could have disabled the repository manually. Finally, the files in the repository are signed with a key. If this key isn't present on your system, you'll get an warning message when you run apt update and GE will not be upgraded.

So, have you got the file /etc/apt/sources.list.d/google-earth-pro.list? If so, what are the contents? The repository should be there and not commented out. And does apt give you a warning for a missing key?

Just downloading the .deb installer again and installing it over the existing GE package works, but can't be automated to make it happen whenever Google releases an upgrade.

---

### Post by Ralph L on 2021-11-19
I went to [https://www.google.com/earth/versions/](https://www.google.com/earth/versions/) clicked on "Google Earth Pro on Desktop. This brought up a download window asking if I wanted to save the file or open it with Software. I clicked Open. It seems to update what was in /opt to 7.3 and google earth seems to run ok. What I don't understand is after the update I brought up Software again and couldn't find googleearth-package. I normally use Synaptic rather than Software so maybe I did something wrong when I searched for it. Any ideas????
I also brought up Synaptic and searched for googleearth-package and found it, but Synaptic listed version 1.22 and said it was not installled. This seems very strange.
I went to /etc/apt/sources.list.d and found google-earth-pro.list and google-earth-pro.list.save. Why did both Software and Synaptic not find that I had google earth installed and the 7.3 version??? Does not Software and Synaptic use /etc/apt/sources.list????  Something seems very goofy to me.
Any explanation would educate me a lot.

---

### Post by monkeybrain20122 on 2021-11-19
> I also brought up Synaptic and searched for googleearth-package and  found it, but Synaptic listed version 1.22 and said it was not  installled.

"googleearth-package" is not google-earth, but "utility to automatically build a Debian package of Google Earth" according to synaptic's description.

---


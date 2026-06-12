---
title: "K3b wont let me burn mp3's?"
date: 2005-10-18
forum: General Help
---

### Post by Fern_azul10 on 2005-10-18
I was trying to make a music cd using k3b but when I choose an mp3 file it says "Unable to handle the following files due to an unsupported format" What do I have to do to correct this problem? Please Help!!

---

### Post by bored2k on 2005-10-18
You need to install k3b-mp3
```
sudo apt-get install k3b-mp3
```
> k3b-mp3 - The KDE cd burning application library - MP3 decoder


---

### Post by Fern_azul10 on 2005-10-18
ohh thanks man your a life saver domo arigatou!!

---

### Post by ohman11 on 2005-10-19
I get this message

Package k3b-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package k3b-mp3 has no installation candidate

---

### Post by WW on 2005-10-20
Do you have the [universe repository](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu) enabled?

---

### Post by ohman11 on 2005-10-20
[QUOTE=WW]Do you have the [universe repository](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu) enabled?[/QUOTE]


That was the problem, Thanks!

---


---
title: "I need (very basic) help adding a repository so that I can install Tellico"
date: 2024-09-26
forum: General Help
---

### Post by Green_Mac on 2024-09-26
HI,

I have tried searching the forums for this, but can't find anything pitched at my level.

I have just bought a new laptop, running Ubuntu 24.04, and I need to install Tellico (a collection manager, [https://tellico-project.org/](https://tellico-project.org/)). It does not seem to be available from the repositories that come with Ubuntu by default. I have been using this package for years, so must have added an appropriate repository on my old laptop, but can't remember what I did. The repository list for Tellico is at [https://repology.org/project/tellico/versions](https://repology.org/project/tellico/versions) and I'm guessing I need to use Arch if I want to get the latest version.

I have made two attempts to do this via the Software and Updates module, both of which ended with Software and Updates not being able to run again until I used a text editor to remove the entries I had added from the appropriate file.

If someone could walk me through literally every step I need, I would be extremely grateful.

---

### Post by maglin2 on 2024-09-26
Tellico is in the 24.04 ubuntu repositories (kde universe)
```
$ apt-cache policy tellico
tellico:
  Installed: (none)
  Candidate: 3.5.3-1ubuntu5
  Version table:
     3.5.3-1ubuntu5 500
        500 http://gb.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
```

---

### Post by Green_Mac on 2024-09-26
When I type that in Terminal I get exactly the same result. I assumed that if it was in the repositories, I would be able to find it via the App Centre, but all I get is "No results found for tellico".

This is why I said "very basic help" in the subject, assume I know nothing.

Thanks.

---

### Post by Holger_Gehrke on 2024-09-26
If you're happy with version 3.5.3 then a simple
```

sudo apt install tellico

```
will get and install it. The reason it doesn't show up in the snap-store - or whatever other descendant of gnome-software you mean by App Centre - is that applications need to have additional metadata stored outside of the repositories to show up and the maintainer of tellico didn't bother to do that.

If you absolutely insist on version 4.0 then you will have to install flatpak, enable flathub as a repository for flatpak and install it from there. Since I don't use flatpaks - no, not for any ideological reasons, I just never had the need - I can't give you step-by-step step instructions, but tutorials for each step should be within reach on your favourite search engine.

Holger

---

### Post by Green_Mac on 2024-09-26
Thank you so much. I didn't know that about the metadata, I'll try to remember it in future. I now have version 3.5.3 on my new laptop, and will look at upgrading to version 4 when I'm feeling brave.

Thanks again.

---

### Post by maglin2 on 2024-09-26
To search and install from the repositories I have always used synaptic. That's how I knew tellico was there.
You can install that from the App Centre.

---

### Post by Holger_Gehrke on 2024-09-26
Actually flathub has instructions for most of the process at [https://flathub.org/setup/Ubuntu](https://flathub.org/setup/Ubuntu) ... 

Upgrading is not quite how I'd describe switching from a Debian package to a flatpak, since flatpaks (and snaps) basically exist outside the normal packaging system. You can in theory have different versions of the same program installed at the same time in different kinds of packages but obviously any changes in data format between the packages will lead to interesting - meaning catastrophic - problems. Better to uninstall the version from the repositories ('sudo apt remove --purge tellico') before installing the flatpak.

Holger

---

### Post by Green_Mac on 2024-09-26
Thanks! Another new thing learned.

---


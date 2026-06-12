---
title: "Dropbox and software sources"
date: 2020-12-17
forum: General Help
---

### Post by shmu26 on 2020-12-17
I am running Kubuntu 20.04 and I installed Dropbox from Discover. It says it will install the proprietary dropbox. 
But I don't see an entry for it in Software Sources. Is that right?

---

### Post by Bashing-om on 2020-12-17
shmu26; Hey - 

I would expect dropbox's source to be installed in the 3rd party sources directory.
What shows:
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT]maybe Yes
[/INDENT]

---

### Post by CelticWarrior on 2020-12-17
I stopped using Dropbox a long time ago but I remember it adding the Dropbox repository only after running it for the first time.
What is in the Ubuntu repositories is a sort of "web installer". When run for the first time it downloads what it needs and add the repository for future updates.

---

### Post by shmu26 on 2020-12-18
> **Bashing-om said:**
> shmu26; Hey - 

I would expect dropbox's source to be installed in the 3rd party sources directory.
What shows:
```

tail -v -n +1 /etc/apt/sources.list.d/*

```[INDENT]maybe Yes
[/INDENT]


I am confused. What I see in the terminal is not what I see in the screenshot
```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-focal.list <
==



==> /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-focal.list.s
ave <==



==> /etc/apt/sources.list.d/brave-browser-release.list <==



==> /etc/apt/sources.list.d/brave-browser-release.list.save <==



==> /etc/apt/sources.list.d/dropbox.list <==



==> /etc/apt/sources.list.d/dropbox.list.save <==



==> /etc/apt/sources.list.d/google-chrome.list <==
###
###
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may b
e lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main



==> /etc/apt/sources.list.d/google-chrome.list.save <==
###
###
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may b
e lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main



==> /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-focal.list <==



==> /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-focal.list.save 
<==



==> /etc/apt/sources.list.d/skype-stable.list <==

==> /etc/apt/sources.list.d/skype-stable.list.save <==

==> /etc/apt/sources.list.d/virtualbox.org.list <==
# deb http://download.virtualbox.org/virtualbox/debian/ focal non-f
ree contrib



==> /etc/apt/sources.list.d/virtualbox.org.list.save <==
# deb http://download.virtualbox.org/virtualbox/debian/ focal non-f
ree contrib



```

[ATTACH=CONFIG]287575[/ATTACH]

---

### Post by deadflowr on 2020-12-18
I'm going to guess the source .list file for dropbox is empty.
I'd open those list files in the text editor and if they open empty then somehow the entries were either:
1)deleted from the file, somehow, some way.
2)never properly written to the file in the first place.

Seems you have a few in a similar state, like the flatpak ppa list files...

---

### Post by shmu26 on 2020-12-18
> **deadflowr said:**
> I'm going to guess the source .list file for dropbox is empty.
I'd open those list files in the text editor and if they open empty then somehow the entries were either:
1)deleted from the file, somehow, some way.
2)never properly written to the file in the first place.

Seems you have a few in a similar state, like the flatpak ppa list files...
I opened the files. Yes, they are empty. Why? Probably because I edited my software list through the GUI, as shown in my screenshot, but it did not delete the files themselves.

Let me explain what happened here: I had a bunch of applications -- including Dropbox -- that I originally installed from the vendor's source. Then I decided I wanted to get rid of my third-party sources as much as possible. So I deleted those applications, edited the software list through the GUI, and then installed what I needed straight from Discover. This is what I did with Dropbox. 

So the question remains: why didn't installing Dropbox from Discover recreate an active entry in software sources?
Maybe it is because I had this blank file sitting there, and that created an issue? Or maybe there is not supposed to be such an entry at all, so I have no problem at all?

---

### Post by deadflowr on 2020-12-18
> So the question remains: why didn't installing Dropbox from Discover recreate an active entry in software sources?
I'm fairly sure it never did that. By that I mean it never adds the repos.
Most user who want dropbox manually add the repos,
as the version that ships with Ubuntu tends to age terribly.

Edit: I believe if you install dropbox from dropbox's available deb file from them directly instead of through Ubuntu's repositories, that version will adds the repos.

---

### Post by shmu26 on 2020-12-19
Now there is a flatpak version of Dropbox, too. I just installed in on Kubuntu 20.04 and it seems to work well, and it is on an up-to-date version

---


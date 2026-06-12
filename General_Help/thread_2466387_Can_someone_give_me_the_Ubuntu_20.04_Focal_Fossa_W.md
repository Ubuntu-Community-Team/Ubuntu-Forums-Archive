---
title: "Can someone give me the Ubuntu 20.04 Focal Fossa WALLPAPER?"
date: 2021-08-26
forum: General Help
---

### Post by dialyt-7 on 2021-08-26
Today I upgraded to Hirsute Hippo, but I would really like the Focal Fossa wallpaper file (default focal fossa on purple background). Any images I can find online are not hi-res images. I didn't realise that the files do reside on the computer, and I could have saved it myself before I upgraded. Could someone give me the file?

---

### Post by dragonfly41 on 2021-08-26
Perhaps you can find it in a 20.04 LiveUSB lying around?

---

### Post by coffeecat on 2021-08-26
> **dialyt-7 said:**
> Any images I can find online are not hi-res images. I didn't realise that the files do reside on the computer, and I could have saved it myself before I upgraded. Could someone give me the file?

How would they do that? Any image uploaded to the forum would be resolution downgraded. But don't despair! A simple terminal command should get you the whole set:

```
sudo apt install ubuntu-wallpapers-focal
```

Adapt the command as necessary for any other release.

**Edit**: Oops. That might not work. For some reason I have never been able to fathom, the default wallpaper for each release has the filename warty-final-ubuntu.png, so I'm not sure what will happen when you run that command in Hirsute. But there is another way. 

Download this file (click on the link): [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_20.04.2-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_20.04.2-0ubuntu1_all.deb)

Then extract the deb. Then extract data.tar.xz inside the extracted deb. Then navigate to usr/share/backgrounds inside the data folder and you'll find the full 4096x2304 warty-final-ubuntu.png file with the focal image you want.

---

### Post by dialyt-7 on 2021-08-26
> **dragonfly41 said:**
> Perhaps you can find it in a 20.04 LiveUSB lying around?
That would work I'm sure, thanks for the tip!

> **coffeecat said:**
> How would they do that? Any image uploaded to the forum would be resolution downgraded. But don't despair! A simple terminal command should get you the whole set:

```
sudo apt install ubuntu-wallpapers-focal
```

Adapt the command as necessary for any other release.

**Edit**: Oops. That might not work. For some reason I have never been able to fathom, the default wallpaper for each release has the filename warty-final-ubuntu.png, so I'm not sure what will happen when you run that command in Hirsute. But there is another way. 

Download this file (click on the link): [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_20.04.2-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-wallpapers/ubuntu-wallpapers_20.04.2-0ubuntu1_all.deb)

Then extract the deb. Then extract data.tar.xz inside the extracted deb. Then navigate to usr/share/backgrounds inside the data folder and you'll find the full 4096x2304 warty-final-ubuntu.png file with the focal image you want.

Thanks, I tried the first step and realised it was missing, and then did the second! :-)

---


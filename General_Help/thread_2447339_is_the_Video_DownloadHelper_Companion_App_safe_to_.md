---
title: "is the Video DownloadHelper Companion App safe to install and use?"
date: 2020-07-16
forum: General Help
---

### Post by ardouronerous on 2020-07-16
[COLOR=#1A1A1B]I'm running Lubuntu 18.04 and I have the Firefox addon [Video DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/") installed. For  some operations, Video DownloadHelper needs me to install their [Companion App]("https://www.downloadhelper.net/install-coapp"), which is a separate program that I have to install on my  system, there's a DEB file available. According to the website, the full code of the companion application is released in open-source to 					ensure full transparency, which can be found [here]("https://github.com/mi-g/vdhcoapp").


I'm  really reluctant to install third-party applications to my operating   system. Is it safe? 


For  those who will say, use YouTube-DL, I have that installed also. The  reason why I have Video DownloadHelper  installed is because not all  sites are supported by YouTube-DL, so I use Video DownloadHelper for  those unsupported sites.

[/COLOR]

---

### Post by dinkidonk on 2020-07-17
The companion app is basically just ffmpeg with an extra app to communicate with firefox, I have installed it and have not experienced any issues, the [source code is public]("https://github.com/mi-g/vdhcoapp"). However, DownloadHelper does not work very well anymore and a lot of downloads does either not complete at all or they are defunct. The ffmpeg part of the companion app is quite fond of putting an annoying watermark into the downloaded videos - unless you pay for a license that is.

---

### Post by monkeybrain20122 on 2020-07-17
There is a better way but I am not allowed to mention its name here. ;) It also works as a plugin to mpv for streaming and is in the repo though the repo's version is useless since it is very out of date.

---

### Post by ardouronerous on 2020-07-17
> **dinkidonk said:**
> The companion app is basically just ffmpeg with an extra app to communicate with firefox, I have installed it and have not experienced any issues, the [source code is public]("https://github.com/mi-g/vdhcoapp"). However, DownloadHelper does not work very well anymore and a lot of downloads does either not complete at all or they are defunct. The ffmpeg part of the companion app is quite fond of putting an annoying watermark into the downloaded videos - unless you pay for a license that is.

Thanks, I've installed it and it seems to be pretty much okay.

---

### Post by ActionParsnip on 2020-07-18
Your entire operating system is made by 3rd parties. Canonical doesn't make the component parts of Ubuntu. Mozilla make Thunderbird and Firefox. The kernel team including Linus Torvalds make the kernel. The Gnome team make the desktop environment and so on. Canonical just package the OS together in a coherent manner for you. They make some bits but large chunks of your OS are made outside of Canonical 
It's all nearly all 3rd party software dude.

---

### Post by dinkidonk on 2020-07-18
> **ActionParsnip said:**
> It's all nearly all 3rd party software dude.

Yes, and it's all in repositories where malicious code is quite rare. Downloading an installer from a dubious location may feel uncomfy for some/many so the post is in that regard justified, dude.. :tongue:

---


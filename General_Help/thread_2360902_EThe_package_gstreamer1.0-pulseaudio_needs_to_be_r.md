---
title: "E:The package gstreamer1.0-pulseaudio needs to be reinstalled, but I can't find an ar"
date: 2017-05-09
forum: General Help
---

### Post by gravity1988 on 2017-05-09
Hi,
       When I was updating the softwares, I found that it cannot be done because....."E:The package gstreamer1.0-pulseaudio needs to be reinstalled, but I can't find an archive for it."
How can I come out from this problem..? Please help me. 

Bests,

Supriya

---

### Post by ian-weisser on 2017-05-09
Download the .deb using apt or manually (sudo apt install --download-only gstreamer1.0-pulseaudio)

If you download it manually, then place it in /var/cache/apt/archives and make sure it's owned by root.

---

### Post by gravity1988 on 2017-05-10
Sorry, I tried to download it by sudo apt...but again it shows the same problem...that is:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package gstreamer1.0-pulseaudio needs to be reinstalled, but I can't find an archive for it.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Could you please take a look at it ?

---

### Post by howefield on 2017-05-10
Which version of Ubuntu are you using ?

---

### Post by ian-weisser on 2017-05-10
> **gravity1988 said:**
> Sorry, I tried to download it by sudo apt...but again it shows the same problem.

Yes, that's why there are manual instructions in Post #2.

---

### Post by gravity1988 on 2017-05-10
I am using Ubuntu 16.04

---

### Post by gravity1988 on 2017-05-10
Ok...let me see...thanks again ...

---

### Post by howefield on 2017-05-10
This should put you in the correct directory and download the package if you haven't got it from the above.

```
cd /var/cache/apt/archives/ && sudo apt-get download gstreamer1.0-pulseaudio
```

---

### Post by gravity1988 on 2017-05-12
Thank you very much.

---

### Post by gravity1988 on 2017-05-12
I am sorry, I am new in ubuntu, so please don't mind for asking some stupid questions. I followed the same as you suggested...first manually downloaded the .deb file (gstreamer1.0-pulseaudio_1.8.0-1ubuntu1_amd64.deb), then I kept this file into /var/cache/apt/archives/  and then finally wrote [COLOR=#000000][FONT=&quot]cd /var/cache/apt/archives/ && sudo apt-get download gstreamer1.0-pulseaudio
But, I could not download it. It appears 

[/FONT][/COLOR][COLOR=#000000]E: The package gstreamer1.0-pulseaudio needs to be reinstalled, but I can't find an archive for it.

Please give me some ways out. [/COLOR]

---

### Post by #&amp;thj^% on 2017-05-12
Please return the output of this from a terminal:
```
sudo apt install --reinstall gstreamer1.0-pulseaudio

```
Copy and paste from the terminal back here so we can see a bit of what's going on.

---


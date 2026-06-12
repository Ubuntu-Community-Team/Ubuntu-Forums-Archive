---
title: "Ubuntu 19.04 black screen after login - nvidia"
date: 2019-06-02
forum: General Help
---

### Post by stubanger27 on 2019-06-02
Hi guys, I've just done a fresh install of Ubuntu 19.04 on my Dell Latitude E6510. Installation ran smoothly. As soon as i type my password to login to gnome the screen goes black. After some googling I found this to be a common problem with nvidia drivers so i tried a couple of 'fixes' that helped others. I added the PPA repo and did the auto install - still blank screen. Any advice would be greatly appreciated. Cheers, Stu

[IMG]https://drive.google.com/file/d/140BgllV8oj9_wz7GyMncQaTPs0w70dBl/view?usp=sharing[/IMG]  [ATTACH=CONFIG]283355[/ATTACH]

---

### Post by LwIh%*7 on 2019-06-02
Could you try the latest nvidia driver in the repository 
```

sudo apt-get install nvidia-driver-418 

```
Please see if that fixes it for you.

---

### Post by stubanger27 on 2019-06-02
Thanks for your reply @ImpWarfare I tried removing the old driver and installing driver 418. This changed the login/desktop environment to 640x480. I was unable to change the resolution as control centre wouldn't open.

I then tried removing driver 418 and installing driver 340. This results in perfect resolution at login then black screen.

---

### Post by JTiburzi on 2020-02-16
I've just done a fresh install of Ubuntu 19.10 on my Dell Latitude E6510, with the exact same results. Were you able to resolve this issue?

---


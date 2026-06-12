---
title: "2nd monitor does not work."
date: 2013-01-10
forum: General Help
---

### Post by Zirts on 2013-01-10
Hi,

so I have this problem with my second monitor..
I am using a laptop and when I connect another monitor into it and go to system settings --> Displays and press ON for the new monitor.

Now I hit apply and it gives me this error:
```
required virtual size does not fit available size: requested=(2646, 1024), minimum=(320, 200), maximum=(1600, 1600)
```

It does not matter which resolution I pick for the monitor, it still keeps giving me that error. 
What am I doing wrong here?

I have installed latest AMD GNU/Linux beta drivers also if it matters anything.

---

### Post by Muratturat on 2013-01-10
> **Zirts said:**
> Hi,

so I have this problem with my second monitor..
I am using a laptop and when I connect another monitor into it and go to system settings --> Displays and press ON for the new monitor.

Now I hit apply and it gives me this error:
```
required virtual size does not fit available size: requested=(2646, 1024), minimum=(320, 200), maximum=(1600, 1600)
```

It does not matter which resolution I pick for the monitor, it still keeps giving me that error. 
What am I doing wrong here?

I have installed latest AMD GNU/Linux beta drivers also if it matters anything.

1. ```
sudo add-apt-repository ppa:webupd8team/jupiter
```
2. ```
sudo apt-get update
```
3. ```
sudo apt-get install jupiter
```

Then restart your computer and then there is video displays menu and there you can try to select internal of external ot both..
If it doesn't work then we can try another method.

---

### Post by BicyclerBoy on 2013-01-10
Very old GPU with little video RAM ?

Your error indicates 1600x1600 max..

Can you allocate more video ram in BIOS (assume IGP laptop)?

You can stack screens 1 above/below other so the max vertical pixels limits your choice & not horizontal pixels..

---

### Post by Zirts on 2013-01-10
Its Hd 5650 with 1gb ram, should be enought, I will try what Muratturat sayd now.

---

### Post by Zirts on 2013-01-10
Okay, installed it and the video displays menu shows a new empty menu. Nothing there. Now what... ? :D

---

### Post by Zirts on 2013-01-11
bump

---


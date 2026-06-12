---
title: "Mouse cursor disappears"
date: 2017-03-07
forum: General Help
---

### Post by torill1984 on 2017-03-07
We have a totally fresh installation of 16.04.2 LTS, and the mouse cursor won't show on bottom half of screen. A Google search suggested I should try installing lightgdm in terminal, but that did not help. Does someone know how to fix this? It really makes the whole desktop useless.

---

### Post by mörgæs on 2017-03-08
Hi, welcome to the fora.

Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by NMrpHzy on 2017-03-08
I'm also having the same issue, although I'm running 16.10, and mine isn't a recent installation. I'm having to work on everything in the top half of the screen to see the cursor.
Below is my print-out from lshw was too long to be allowed to paste it here, so it is here: [https://paste.ubuntu.com/24142059/](https://paste.ubuntu.com/24142059/)

---

### Post by mörgæs on 2017-03-09
Good to have an extra post here. Maybe we can solve two problems in one go.

In which applications does the problem occur?

---

### Post by NMrpHzy on 2017-03-09
Thanks for responding, the problem is with everything, even when there's no program open and it's just the desktop showing.

---

### Post by mörgæs on 2017-03-10
You have new AMD graphics running 16.10 in which the open source Radeon driver is in use. 

While we are all happy that AMD is going all-in supporting open source there might be some areas in which the Radeon drivers have not yet caught up with the closed source Fgl-rx available in 14.04.

If you have the space you could try installing one of the 14.04's (I don't know which is the best, someone else please chip in) for comparison.

---

### Post by NMrpHzy on 2017-03-10
So I tried installing the fglrx driver, I got it directly from the AMD site. It installed, and then I restarted. Unfortunately, I can no longer get onto unity (I can't log-in). The log-in screen appears (although on an apparently low resolution), but when I log in, the screen flashes black, (some code appears on the screen, but not for long enough to read) and then I am taken back to the log-in screen. Any idea how to revert the driver back, without being able to log-in?

---

### Post by NMrpHzy on 2017-03-10
So I've followed some advice online, and managed to get the installed drivers back off through the command prompt, without getting onto the gui. So I'm just back to the initial problem of having no  cursor in the bottom half of the screen.

---

### Post by mörgæs on 2017-03-11
As mentioned here

> **mörgæs said:**
> ... closed source Fgl-rx available in 14.04.


the place to experiment with closed source drivers, if you so desire, is 14.04.

'Experiment' means that I can't promise you that it will solve your problem in 14.04 but I can promise you that it will fail in 16.04.

---

### Post by torill1984 on 2017-03-12
Hi, and thanks for your feedback. We decided to install an older version Ubuntu (14.04) instead. No problems with invisible cursor there.

---

### Post by mörgæs on 2017-03-13
Good, please mark the thread solved. 

Ubuntu 14.04 is supported through april 2019 so there is no rush to change that.

---


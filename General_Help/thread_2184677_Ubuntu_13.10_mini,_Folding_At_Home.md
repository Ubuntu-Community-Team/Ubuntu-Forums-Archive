---
title: "Ubuntu 13.10 mini, Folding At Home"
date: 2013-10-30
forum: General Help
---

### Post by tmontney on 2013-10-30
I run the Folding@Home software, and I use Ubuntu. I wanted the absolute lightest install of Ubuntu I could get. So I did Ubuntu mini install. During the install, it asked how I wanted it to personalize the install to my needs. I didn't select anything and kept the core OS. The F@H client is in a .deb package. Is it possible to install such a package on the core OS?

---

### Post by nativehound on 2013-10-30
You will need to startx to install FAHv7.3.deb

To get X to work
```
sudo apt-get install xinit 
```
```

startx
```
and then download the file 
```
wget https://fah.stanford.edu/file-releases/public/release/fahclient/debian-testing-64bit/v7.3/fahclient_7.3.6_amd64.deb
```
and finally 
```
sudo dpkg -i ~/fahclient_7.3.6_amd64.deb

```

I hope that helps.

---

### Post by tmontney on 2013-10-30
I'll try that out!

---

### Post by tmontney on 2013-10-31
It worked. FAHCLIENT is running.

However, after I restarted my VM and tried running "startx" again it seems to load then black screens. However, I can see in my remote F@H client that F@H is running. How do I fix this?

---

### Post by nativehound on 2013-10-31
If you got a black screen hit Right CTRL and f1 or 2 that should get you a command prompt. Then type startx and that should get x working again. Just remember to type ```
exit
``` in the white terminal when your done with x and it shouldn't happen again.

---

### Post by tmontney on 2013-10-31
I get a black screen after starting startx, not before. Still black screen.

---

### Post by nativehound on 2013-10-31
That one I haven't seen. When I get a blackscreen on my setup it's becuase i left x running and some kinda screen/power saver kicks in and leaves me with a black screen i cant use. I have to f1 and the startx it comes right back on. I'm at a loss, you could try reinstalling xinit.

---


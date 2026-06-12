---
title: "Firefox needs too much resources"
date: 2008-06-08
forum: General Help
---

### Post by huepfend_schof on 2008-06-08
Firefox uses 100% of my cpu resources, when visiting a lot of homepages with flash. Even if the homepage only has a small flash advertisement. Is this normal? What can I do against it?

---

### Post by Nepherte on 2008-06-08
It's probably not Firefox itself but the flashplugin. If you experience the same problem again, check what's using a lot of cpu and memory by typing in the terminal:
```
top
```
The first entries are the ones that need the most resources.

---

### Post by huepfend_schof on 2008-06-08
I checked it out, and it is really firefox. Top gives:
>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7909 laurent   20   0  398m 216m  30m R 73.8 14.2  48:17.02 firefox            
 5765 root      20   0  312m 132m  12m R  6.3  8.7  47:12.55 Xorg               
 6296 laurent    9 -11 36828 6592 4008 S  6.3  0.4  20:51.02 pulseaudio
...         

I received the full utilization of the cpu by visiting [www.20min.ch](www.20min.ch) in some tabs simultaneously. But it happens also with other homepages.

---

### Post by Kinnza on 2008-06-08
i had some simmilar probs with firefox (way back on windows, and im pretty sure its the same)

the more plugins i installed the more cpu and ram it took, untill it got to a point when the computer got so stuck that it was annoying

i suggest that you pick your favorit addons and remove the ones you dont use to make it work faster and take less resources

---

### Post by bingoUV on 2008-06-08
I don't have the solution to your problem, but I think you don't need to view all those flash animations. If you install the flashblock extension ([https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)), no flash animations will run unless you click on their space and allow them to run.

---

### Post by FakeOutdoorsman on 2008-06-08
You might have better luck with Firefox 2.  Backup your Firefox profile:
```
mv ~/.mozilla ~/.mozillaold
```
Then remove Firefox 3:
```
sudo aptitude purge firefox

```
Now install Firefox 2:
```
sudo aptitude update
sudo aptitude install firefox-2
```

---

### Post by knutschr on 2008-06-08
> **bingoUV said:**
> I don't have the solution to your problem, but I think you don't need to view all those flash animations. If you install the flashblock extension ([https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)), no flash animations will run unless you click on their space and allow them to run.

Very good! Thx!
Firefox3 now uses 5-10% of CPU instead of 70-80% :-)

---

### Post by huepfend_schof on 2008-06-09
> **bingoUV said:**
> I don't have the solution to your problem, but I think you don't need to view all those flash animations. If you install the flashblock extension ([https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)), no flash animations will run unless you click on their space and allow them to run.

Thanks for the tip. With this addon, when I open the same homepages as before(which took before 75% cpu), firefox now needs only 2% of my CPU!

---


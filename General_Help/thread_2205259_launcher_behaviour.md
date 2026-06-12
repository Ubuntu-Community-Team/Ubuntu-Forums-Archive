---
title: "launcher behaviour"
date: 2014-02-12
forum: General Help
---

### Post by plaxton on 2014-02-12
Not sure how this happened, but I recently unplugged my computer for a couple days while doing some renos, and after I re-connected, my launcher acts differently (perhaps the default setting?) Little diificult to explain, but I will try. The way it was - All my icons were 'squished' to fit on the launcher, and I just had to hover my mouse over the launcher, move the pointer up and down, and the icons would scroll rapidly, until I found what I needed. Currently, all my icons show full size, and I have to hover my mouse at the top (or bottom) of the launcher to scroll to find the item I want, and it is much slower this way. I've tried messing with appearance settings and the compizconfig setings manager, but I can't find anything to alter that particular behaviour. Any suggestions would be greatly appreciated.

---

### Post by deadflowr on 2014-02-12
Is this Ubuntu 12.04?

Edited: See post no.3.
Basically I think the same thing.

---

### Post by 3rdalbum on 2014-02-12
Sounds like you have logged into Unity 2D. This might have happened in error if your graphics card was temporarily not recognized. Log out and click the Ubuntu logo, choose Ubuntu and log in. Everything should be back to normal.

---

### Post by plaxton on 2014-02-13
Sorry, yes I am using 12.04. Tried loggong out, but to no avail. How would I know if I'm using Unity 2D or 3D?

---

### Post by plaxton on 2014-02-13
Ok, looks like my ATI HD 3650 driver is longer installed for some reason. It doesn't come up under additional drivers, so I downloaded the driver from ATI website. How do I execute a .run file?

---

### Post by deadflowr on 2014-02-13
AMD no longer supports cards for the HD2000,3000, and 4000 series.
And because of this those drivers do not work with any version of Ubuntu, I believe, beyond 12.04.1.
So yuou're stuck with open-source drivers or bust.

On another matter, there are several ways to tell if you're running unity or unity2d.
Firstly, a basic visual idea. And that would be that with unity the launcher. when packed full, will start to scrunch like an accordian.
Unity2d will not, and the extra icons will seem to down forever down, sometimes looking cutoff at the bottom.

Another way is run
```
/usr/lib/nux/unity_support_test -p
```
and then
```
echo $DESKTOP_SESSION
```
if the first one shows all yes and the second says ubuntu, then you are running unity-(3d).
if the first has any no(s) no matter what the second one says, it'll be unity2d.
if the first says all yes but the second says ubuntu2d, then you are running unity2d.
and if the first says no and the second says ubuntu2d, then of course, it's unity2d.
Hope that helps, somewhat.
I know there are easier ways to figure out which session is running, but I forget 'em.

---

### Post by Dennis N on 2014-02-13
> How would I know if I'm using Unity 2D or 3D? 

In Ubuntu 12.04. you can select Ubuntu or Ubuntu 2D from the login screen selector: it's the little ubuntu icon in the top right of the login box (where you type your password.)

---

### Post by plaxton on 2014-02-13
> **deadflowr said:**
> 

On another matter, there are several ways to tell if you're running unity or unity2d.
Firstly, a basic visual idea. And that would be that with unity the launcher. when packed full, will start to scrunch like an accordian.
Unity2d will not, and the extra icons will seem to down forever down, sometimes looking cutoff at the bottom.



That is exactly what is happening. It appears that the lack of driver support is the issue. :mad: So I guess I'm stuck with it for now.

I found a Ubuntu page that explains a rather quick way to check whether running Unity 2D or 3D:

*'You can determine if you are running Unity 3D or 2D by open the system monitor. If you see a process named compiz in the processes tab, you are using Unity 3D. If it's running metacity instead, you're working with Unity 2D. '*

Thanks everyone for your assistance.

---


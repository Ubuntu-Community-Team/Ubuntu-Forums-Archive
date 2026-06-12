---
title: "Firefox Scroll very slow"
date: 2007-11-18
forum: General Help
---

### Post by tresdey on 2007-11-18
I don't know why mi Web browser Firefox update up to date 2.0.0.9 has an imcompatibility wih some plugins of compiz (I think) And when compiz is on, the browswer's scroll works very very very slow, when its off its all right. I have ati driver propietary and compizfusion core Git on Gutsy. Plis if someone know how can i solutionate this problem, i need some hepl.

Thanks all!!

I wait your answers.

---

### Post by gsiliceo on 2007-11-18
Try disabling one plug in at the time and testing Firefox.
You'll need 
> sudo apt-get install compizconfig-settings-manager
And you can find the manager in system>preferences i think.

---

### Post by tresdey on 2007-11-19
The really question was: There are any compatibility between Firefox and Compiz??
Tank you very much! I'm trying but everything is the same.

thank you!

---

### Post by DimitrisC on 2007-11-19
I have the same problem. After a clean installation of Gutsy on my Dell Inspiron 6000 laptop firefox was working fine and desktop effects were enabled by default. When I installed the ati driver and enabled some extra compiz plugins then firefox slowed down and scrolling was almost impossible. Because of the fact that firefox was working fine with desktop effects enabled after the clean install I come to think that the problem may has something to do with the ati driver. I read about a lot of people having the same problem but no solution thus far.

We'll wait and see. :(

---

### Post by tresdey on 2007-11-19
So we only can wait for a new ati driver?

thanks!!

---

### Post by DimitrisC on 2007-11-19
> **tresdey said:**
> So we only can wait for a new ati driver?

thanks!!

Well if the problem is indeed the ati driver then the only thing we can do is wait for a new driver to come out or someone releases a patch or any other way to fix the problem. I will try again with a new installation tonight, this time without installing the ati driver. I will let you know how it goes.

---

### Post by aJayRoo on 2007-11-19
Have you tried changing the smooth scrolling setting in firefox? Might be worth a try as it is simple to do.

---

### Post by tresdey on 2007-11-19
is disable and firefox still working slow. Thank you very much. 
I'm trying others browsers and i have the same problem, with firefox opera and konqueror. I think is a problem of something else.Maybe the Wifi driver?

 Thanks all very much!

---

### Post by DimitrisC on 2007-11-20
Well I did a clean install last night, this time without installing the ati driver. Desktop effects were enabled by default after the installation (although I dont have all the bells and wistles) and firefox works just fine. So in my opinion it has something to do either with the ati driver or with the extra compiz plugins or both.

---

### Post by tresdey on 2007-11-20
Thank you. I did a clean installation too, the last time, and i had a lot of problems with mi video card, so i will keep my installation waiting for a new driver. I had loose a lot of time configurating it. I will report what happend with a new driver.

Thank you very much. :)

---

### Post by Lagos on 2007-11-24
I just had the same issue, and i think i figured out why it happens. The problem comes from the XGL server that we need to install in order for compiz to work. When you install XGL it disables your direct rendering, and thats what slows down scrolling.  

type in:
 glxinfo | grep direct

it should report :
direct rendering: Yes

When you XGL, direct rending will be turned off. It actually affects the entire desktop, but you notice it the most in fire fox because its the most graphics intensive.

Go to the synapis package manager, search for xgl and mark it for uninstall. then reboot, check to make sure your direct rendering is ON, and the scrolling problem should be fix. Only down side is that compiz will no longer work.

---

### Post by zippy028 on 2007-11-25
I don't know what the cause to this is but i seemed to have improved my mousewheel scrolling by changing a couple of keys in firefox config.

In firefox address bar type
```
about:config
```

find the keys
```
mousewheel,withnokey,numlines
```

```
mousewheel,withnokey,sysnumlines
```
  

The value I changed *mousewheel,withnokey,numlines* to is "12"
the value for* mousewheel,withnokey,sysnumlines* is "false"

This seems to give me a decent scroll speed without jumping to many lines at a time which was an issue that annoyed me since 6.06.

HTH,
John

---

### Post by ankara on 2007-11-26
another quick solution is to goto firefox prefernces, Edit > preferences > advanced, and disable smooth scrolling.
hth

---

### Post by mech7 on 2008-01-27
I have the exact same thing with latest ATI driver, and compiz.. on X700 mobility :( it's superslow

---


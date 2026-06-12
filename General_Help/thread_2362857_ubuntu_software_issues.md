---
title: "ubuntu software issues"
date: 2017-06-02
forum: General Help
---

### Post by technomancer420 on 2017-06-02
Hello everyone, I've been having issues with the ubuntu software app. Firstly let me start by saying I now have two different ones, the first, named Ubuntu Software, whenever I click on it my cursor animates like it is loading but it never opens and the cursor eventually stops the loading animation. The second one is called Ubuntu Software Center, and it loads fine, but when I'm browsing it, it doesn't load all of the information for the software, which is annoying, but at least it works. Do you guys have any idea what's going on?

---

### Post by RobGoss on 2017-06-03
Hello and welcome to the forums, Which version of Ubuntu are you using? I know they been having some problems with the software center in some distributions not sure if they sorted things out. I have 16.04 installed on one of my machines and it seems to do well

Have you tried using **[Synaptic package manager]("https://help.ubuntu.com/community/SynapticHowto") ** I feel it's a better way to install application and is much faster


You can also try reinstalling the Software and see it that fixes any issued you maybe having with it


[B]
To uninstall Software Center:[/B]

```
sudo apt-get remove software-center

```

```
sudo apt-get autoremove software-center
```


**To re-install Software Center:**


```
sudo apt-get update
```

```
sudo apt-get install software-center
```


I hope this will helps solve your issue

---

### Post by oldos2er on 2017-06-03
+1 to using Synaptic, it will not hide information from you like Software Center does.

---

### Post by arkmundi on 2017-06-04
Hi, software-center was working fine for me up until the 16.04 upgrade.  Now its not.  The menu icon animates as if trying to load, but the app never launches.  I've tried completely removing and re-installing as suggested by that achieves nothing.  Yes, I also have and use Synaptic, and that's my go-to now.  But I liked and used software-center and hope to see it work again.  There is some underlying issue that is beyond me.

---

### Post by monkeybrain20122 on 2017-06-04
+ 2 for synaptic. The Soft-ware-center seems to be completely broken in 17.04. It doesn't even start. In 16.04 it seems to be working, but I don't use it.

---


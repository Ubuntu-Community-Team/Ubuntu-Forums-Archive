---
title: "[SOLVED] Java problems"
date: 2008-04-09
forum: General Help
---

### Post by yao_man on 2008-04-09
I apologize if this is the wrong forum, but this seemed most appropriate to me. I am using Firefox on Ubuntu 7.10. I tried to run a JavaScript game, and Firefox prompted me to install a Java plug in. I selected GCJ, and now I cannot run any JavaScript anything on my browser. I tried using synaptic to remove GCJ but it wasn't listed. I also tried the command (not sure if it's right but oh well) sudo apt-get remove gcj. I installed GCJ from Firefox so I wouldn't expect Ubuntu to recognize the package. How do I go about removing it so that I can instead install the Sun Java 6? Thank you for any help.

As a side note, does anyone know a good free Java IDE for Ubuntu (the only Java IDE I have used was JCreator on Windows).

I appreciate any help.

---

### Post by FuturePilot on 2008-04-09
Try
```
sudo apt-get remove --purge gcjwebplugin
```
I would recommend the Java 6 plugin
```
sudo apt-get install sun-java6-plugin
```

---

### Post by ibutho on 2008-04-09
Some plugins you install manually via firefox are in ~/.mozilla/plugins. You can remve the plugins using rm or if you prefer to do it via nautilus, make sure that you have the option to show hidden files, navigate into .mozilla/plugins and delete the gcj plugins. I personally think you should install the sun java plugins because they seem to work better than gcj.

---

### Post by yao_man on 2008-04-09
Thank you FuturePilot, your advice worked to perfection. I now have Sun Java6, thank you very much.

---

### Post by jsjrod on 2008-04-13
Try installing netbeans.  I use it to code in java and its great.  Click [COLOR="Navy"][here]("http://download.netbeans.org/netbeans/6.0/final/")[/COLOR] to download it.

---

### Post by brento73 on 2008-04-15
I tried this

> **FuturePilot said:**
> Try
```
sudo apt-get remove --purge gcjwebplugin
```
I would recommend the Java 6 plugin
```
sudo apt-get install sun-java6-plugin
```

but recieved the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by wrecche on 2008-04-15
> **brento73 said:**
> I tried this



but recieved the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate


Same with me, and it's a bit disappointing that there are no replies to you after 15 hours :(

here we go again... ;/

---

### Post by ibutho on 2008-04-15
If you are using Ubuntu 7.10, try the icedtea-java7-plugin. You need to have the multiverse repository enabled and then install it via the GUI packaging tools or by doing
```
sudo aptitude install icedtea-java7-plugin
```

---

### Post by brento73 on 2008-04-15
I've tried installing icedtea, and several other packages which are supposed to allow java in firefox, and so far nothing has worked. I even went through a long 'how to' which involved all sorts of command line stuff, only to find out in the last couple steps that I didn't even have some of the directories it referenced. 

I think part of my problem may be that I'm running UbuntuStudio, and it seems to put some things in different locations. I'm about to set up a dual boot with the regular 64bit Ubuntu, hopefully that will work better.

---


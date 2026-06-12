---
title: "Azureus disappers for no apparent reason"
date: 2007-09-10
forum: General Help
---

### Post by khalidhamza on 2007-09-10
When I click on the Azureus icon, it loads up and once its completely loaded, it suddenly disappears. 

I had the same problem with the Totem, Vlc and almost all other players but I found out that it was because of having the desktop effects enabled. Once I disabled that it worked.    

In some discussions it was said to check that thre is space for the system tray icon or something like that, I made sure that the panels have enough room for that. 

I googled a lot to solve the problem but couldn't get it fixed - now I totally rely on your kind help. 

Your help would mean a lot.

---

### Post by prince_niceguy on 2007-09-10
Run the same from console and post the results. It should give some start to resolve the problem.

---

### Post by shaggy999 on 2007-09-10
I had a similar problem. I fixed it by disabling the "fast resume" feature of azureus.  Of course, how do you disable it if the program won't load? I just deleted the .azureus folder in my home directory and went back through the setup process. On the last setup page, de-select fast resume. There might be some config file or maybe change the setting in gconf-config, but I know what worked for me.

---

### Post by shaggy999 on 2007-09-10
BTW, the error I got when I had this was a descriptionless "core dump".

---

### Post by bmorency on 2007-09-10
do you have the latest java installed? if you do it may not be configured to use it.

try this to find out:

```
sudo update-alternatives --config java
```

i get this on my system:

```
Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1

```

make sure the right one has a star beside it.

---

### Post by AlexThomson_NZ on 2007-09-10
If I can just add my 2c, give Deluge a try- it's the best BT client on Linux by a long shot IMHO

---

### Post by Gavin Vickery on 2007-09-10
> **AlexThomson_NZ said:**
> If I can just add my 2c, give Deluge a try- it's the best BT client on Linux by a long shot IMHO

I'd have to agree. When I was still using Windows *shudders* I ran Azureus. However, I found Deluge was a lot faster and bug free on Linux. Best of all, you can easily install it through the "Synaptic Package Manager".

---

### Post by prince_niceguy on 2007-09-11
try changing the java option in the azureus shell script. This should avoid the core dumps. If not put some memory arguments to increase the memory to the java heap.

memory argument is -Xmx256m -Xms256m

---


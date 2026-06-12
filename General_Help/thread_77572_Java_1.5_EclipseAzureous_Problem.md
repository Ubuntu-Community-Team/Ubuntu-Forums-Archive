---
title: "Java 1.5 Eclipse/Azureous Problem"
date: 2005-10-17
forum: General Help
---

### Post by unexpected on 2005-10-17
I was using an older version of Java and had Azureous installed. Then, I installed the Java 1.5 SDK followed by Eclipse. When i installed Eclipse, it told me that I had to uninstall Azureous. I proceeded, but now when I try to reinstall Azureous, I get this error:

azureus:
 Depends: libswt-gtk-3.1-java but it is not going to be installed.

I looked at the "libswt" file, and it's already installed...

Does anyone know what's going on?

---

### Post by matthias_k on 2005-10-17
Where did you install Java 1.5 from? It's not an official package. Maybe you messed up dependencies by overwriting your default Java installation that came with Breezy.

It's "Azureus" by the way :)

---

### Post by unexpected on 2005-10-17
To install Java 1.5, i downloaded the binary from sun  and made it into debian pkg using the Java 1.5 commands that someone had put up here:

[http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+1.5](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+1.5)

If I overwrote the Java dependency that Azureus depends on, is there any way just to force download it and manually edit a config file?

If i download Azureus directly from sourceforge instead of via synaptic, will it look for my default java installation instead of complaining that i overrwrote the one that came with breezy?

Thanks!

~un

---

### Post by matthias_k on 2005-10-17
I don't think it will look for any dependencies. It will execute 'java', whatever version it is. I don't know if Azureus was programmed in Java 5 though. If it was, you will need to install Java 5. I'm not 100% sure, but isn't there a Java 5 package somewhere in the inofficial repositories? I think I installed it in Hoary from the backports repo.

---

### Post by unexpected on 2005-10-17
Yes, except the Breezy unofficial repos aren't up yet.

In any case, I solved the problem, so for anybody else with something similiar...

After removing Azureus completely via synaptic, i installed it from the tarball directly downloaded from sourceforge (I found excellent instructions on doing this by searching for 'Azureus' on the forums). 

Now both Eclipse and Azureus work! I don't know why Synaptic was giving me that error when i installed Azureus- it installed just fine and doesn't seem to have a problem at all.

---


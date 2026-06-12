---
title: "Unable to set openjdk 6 as default open with"
date: 2012-12-07
forum: General Help
---

### Post by Clint1337 on 2012-12-07
I recently switched to ubuntu and am very pleased so far compared to windows 7. However I just installed "Minecraft" and am attempting to make a launcher so I don't have to right click it every time. I'm able to open the program by right clicking and going open with but when I made my launcher it just wouldn’t open and I believe this is because I'm unable to set Openjdk as the open with default for minecraft.jar.
This is very annoying please help

btw this is what I typed for the command on "Main Menu" to make a launcher:
java -Xmx1024M -Xms1024M -jar /home/Zach/.minecraft/minecraft.jar

cheers,

---

### Post by Clint1337 on 2012-12-07
So i recently switched from windows 7 to ubuntu and am very pleased so far. However I'm stuck on something very important. I recently downloaded minecraft and watched a guide on how to make a quick launch icon for it through "Main Menu" however when I made the quick launch icon it did not open minecraft and I'm 99% sure it isn't opening because I'm unable to set "OpenJDK 6" to the default "Open With" program when I go to properties on minecraft.jar.

I read somewhere on google that I could use "Ubuntu tweak" but I can't figure out how to set a default "Open With" program with it, and when I try going to "Admins>File Manager> then click on applications the program just freezes. I don't know if that's the correct place to go to change a default open with program in Ubuntu tweaks but it's the only place I could think of.

PLEASE HELP

---

### Post by coffeecat on 2012-12-07
Threads merged. Please do not post the same issue in different parts of the forum.

---

### Post by CharlesA on 2012-12-07
Hit ctrl + alt +T and type this in the box:

```
java -Xmx1024M -Xms1024M -jar /home/Zach/.minecraft/minecraft.jar
```

That will tell you if there are any errors.

FWIW, the version of OpenJDK in 12.04 is Open JDK 7: ```
java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.04.1)

```

Is there a reason you are wanting to run minecraft with an older version?

---

### Post by Clint1337 on 2012-12-07
Everyone on minecraft forums says to use openjdk 6 as if you use 7 it just crashes on start login

---

### Post by Clint1337 on 2012-12-07
Unable to access jarfile /home/Zach/.minecraft/minecraft.jar

---

### Post by CharlesA on 2012-12-07
Check the path and make sure minecraft.jar is in that place.

Sounds like it isn't.

Otherwise, see here:
[http://askubuntu.com/questions/140902/which-version-of-java-should-i-use-for-minecraft](http://askubuntu.com/questions/140902/which-version-of-java-should-i-use-for-minecraft)

---

### Post by Clint1337 on 2012-12-07
wow I'm dumb, when naming the minecraft file I accidentally misspelled it.

Thanks for the support

---

### Post by CharlesA on 2012-12-07
Glad you got it sorted. :)

---


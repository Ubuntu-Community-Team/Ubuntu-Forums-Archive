---
title: "photoshop not running"
date: 2007-02-02
forum: General Help
---

### Post by Magiczero on 2007-02-02
Helloo 

I have a launcher for photoshop on my desktop & when I try running it I get this error

> Details: Failed to execute child process "/home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe" (No such file or directory) What does this mean? How do I make photoshop work on ubuntu?

Thanks

---

### Post by 23meg on 2007-02-02
Try putting the path in "double quotes".

---

### Post by MSlaveubu on 2007-02-02
> **Magiczero said:**
> Helloo 

I have a launcher for photoshop on my desktop & when I try running it I get this error

 What does this mean? How do I make photoshop work on ubuntu?

Thanks


or could you have uninstalled, moved, or deleted the program that allowed you to run photoshop?  also a possibility (did something like that myself)

---

### Post by kebes on 2007-02-02
Since photoshop is a windows program, you have to run it with "wine" (which you apparently have installed). So you need to run:

wine "/home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe"

So your launcher should not call "photoshop.exe", but "wine photoshop.exe" like in my example above.

Hope that helps.

---

### Post by Shay Stephens on 2007-02-03
Some tips that have helped me run PS7 successfully in wine:

To get save for web to work, load PS like this:
wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"

Using a path with slashes will prevent it from working, you have to use a path with backslashes, so using the simple windows style path as shown above works just fine without actually using the /home/user... stuff.

Secondly, if you are not using a wacom tablet, comment out the all mention of it in the xorg.conf file.

wine version .9.28 and .9.29 don't work for me with PS7.  I have not yet tried .9.30.  The last working version of wine I have tried is .9.27.  So use that if you can't run it otherwise.

---


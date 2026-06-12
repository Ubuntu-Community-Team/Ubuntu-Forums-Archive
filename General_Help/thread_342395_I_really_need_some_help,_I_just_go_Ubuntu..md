---
title: "I really need some help, I just go Ubuntu."
date: 2007-01-20
forum: General Help
---

### Post by Elefant_666 on 2007-01-20
Ok well i just got the disk from a friend and got rid of the windows finally, it seems to go faster and all, but there's a few problems...
1.) My screen resolution i cant figure out how to change it from 640*480 resolution =(
2.) It wont let me download java... I go to the site and download it...it says what would you like firefox to do with it...so i save to my desktop...then i try to open it...but it tries to open in a wordpad...i really need the java runtime on my computer.

If theres anyway you can help me please tell... I'm very new at this and don't know what to do.

It'd probably be best if they have a thing were you can control my computer to fix this.


Thanks for looking here and hopefully helping

Shawn

---

### Post by riven0 on 2007-01-20
1) Try doing a reconfiguration. Open the terminal: Applications >> Accessories >> Terminal and copy and paste:

> sudo dpkg-reconfigure xserver-xorg

To pick your resolutions, hit the space bar.

2) Download java through Synaptic. System >> Administration >> Synaptic Package Manger. In Synaptic, go to >> Settings >> Repositories and make sure everything under Internet is checked off. Now hit OK and Reload. Then search for **java runtime** and install through there.

---

### Post by Coop on 2007-01-20
Hello Shawn
If you're using Ubuntu 6.10 here's how to install java:

1.go to System>Administration and click Software Sources.

2.In the Ubuntu 6.10 tab,tick universe and multiverse,and click close.

3.When it asks if you want to reload,chooose yes.

4.The package lists will be reloaded.

5.Go to Applications and click Add/Remove.This will start the software installer.

6.In the search field,search for java.It will display the results.Tick Java plugin and click apply and follow the instructions and Java will be downloaded and installed.

Ahmed

---

### Post by studiesrule on 2007-01-20
if you want to install the latest JDK (6), download the executable (it should be a .bin file). If you already have that file, open up the terminal, and go to the containing folder. then type the following the the terminal:
```
 chmod +x <java package name.bin> 
```

ofcourse, replace the <...> with name of the java installer file.
Linux in general does that for security reasons.

---


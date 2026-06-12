---
title: "Opening .jar with Java"
date: 2013-01-26
forum: General Help
---

### Post by captainwithershins on 2013-01-26
I downloaded minecraft, but when I open the .jar it opens in Archive manager. So I checked Allow running as executable, but it doesn't show java in the program list. It shows it when I right click and  it works, but I can't set it as default. [http://collabshot.com/show/iC6yHL](http://collabshot.com/show/iC6yHL)

---

### Post by jackyboy633 on 2013-01-26
Hi there,

Can you perform the following command for me? It sounds like you don't have Java on your system.
```
sudo apt-get install default-jre
```

Once that package is installed, it should work by right-clicking. If not, please notify the thread.

Hope this helps :-)

Jackyboy633

---

### Post by captainwithershins on 2013-01-26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
default-jre is already the newest version.
default-jre set to manually installed.
The following packages were automatically installed and are no longer required:
  lib32asound2 lib32bz2-1.0 lib32ffi6 lib32gcc1 lib32ncurses5 lib32ncursesw5
  lib32stdc++6 lib32tinfo5 libqt4-opengl libqt4-webkit:i386
  libqtmultimediakit1 libqxt-core0 libqxt-gui0 linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.

As I said I have java, but it doesn't show up in the list.

---

### Post by jackyboy633 on 2013-01-26
Hello again.

Probably the easiest way to launch Minecraft is to do it in the terminal then. What you need to do is browse to the folder where your minecraft.jar file is located in the terminal, then run the following:
```
java -jar Minecraft.jar
```

Hope this helps,
Jackyboy633

---

### Post by jorok_tupur on 2013-01-26
After Java is installed, you probably want to make Minecraft's icon accessible from Unity's dash.

Follow the instruction on this Stack Exchange thread: [How do I create a .desktop file for a .jar file?]("http://askubuntu.com/questions/192477/how-do-i-create-a-desktop-file-for-a-jar-file/192493#192493")

---

### Post by captainwithershins on 2013-01-26
Thank you all!

---


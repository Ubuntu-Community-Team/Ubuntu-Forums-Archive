---
title: "Can't install the Java program Phyde on Ubuntu"
date: 2014-09-17
forum: General Help
---

### Post by tho4 on 2014-09-17
Hi everyone,

As I am a very beginner, please don't blame me ! 
I am trying to install Phyde, a program I use to process my DNA sequences.
Here can you find the program: [http://www.phyde.de/download.html](http://www.phyde.de/download.html)
Java is already installed, Once I double click on the folder PhyDE-1.jar, I get the message "The file '.../PhyDE-1.jar' is not marked as executable.". When I extract it and look for the executable file, I cannot find it.

Someone could help be with this issue ? 

Many Thanks
Théo

---

### Post by slickymaster on 2014-09-17
Hi tho4, welcome to the forums
> **tho4 said:**
> Hi everyone,

As I am a very beginner, please don't blame me ! 
I am trying to install Phyde, a program I use to process my DNA sequences.
Here can you find the program: [http://www.phyde.de/download.html](http://www.phyde.de/download.html)
Java is already installed, Once I double click on the folder PhyDE-1.jar, I get the message "[COLOR=#ff0000]The file '.../PhyDE-1.jar' is not marked as executable.[/COLOR]". When I extract it and look for the executable file, I cannot find it.

Someone could help be with this issue ? 

Many Thanks
Théo

The important part is in the error message: [B]The file '.../PhyDE-1.jar' is not marked as executable.
[/B]
You can either make it executable by```
sudo chmod +x /path/to/PhyDE-1.jar
```or run, in a terminal:```
java -jar /path/to/PhyDE-1.jar
```

---

### Post by tho4 on 2014-09-17
Many thanks for the help! It's solved !

---

### Post by slickymaster on 2014-09-17
You're welcome. I'm glad you got it fixed.

---

### Post by slickymaster on 2014-09-17
*Thread moved from Education & Science to the ***General Help*** sub-forum.*

---


---
title: "How do I Install JRE?"
date: 2006-08-04
forum: General Help
---

### Post by turner850 on 2006-08-04
I have read a ton of tutorials about installing java and I cannot find a working method so far.

Please share your methods of installing JRE. I need JRE plugin for Firefox

---

### Post by Ramses de Norre on 2006-08-04
```
ramses@icarus:~$ aptitude search java|grep sun
i   sun-java5-bin                   - Sun Java(TM) Runtime Environment (JRE) 5.0
i   sun-java5-demo                  - Sun Java(TM) Development Kit (JDK) 5.0 dem
p   sun-java5-doc                   - Sun JDK(TM) Documention -- integration ins
i   sun-java5-fonts                 - Lucida TrueType fonts (from the Sun JRE)
i   sun-java5-jdk                   - Sun Java(TM) Development Kit (JDK) 5.0
i   sun-java5-jre                   - Sun Java(TM) Runtime Environment (JRE) 5.0
i   sun-java5-plugin                - The Java(TM) Plug-in, Java SE 5.0
p   sun-java5-source                - Sun Java(TM) Development Kit (JDK) 5.0 sou

```
Pick whichever you need;) The plugin one is for firefox.

---

### Post by turner850 on 2006-08-04
uhhh.... What lol?

i need sun-java5-plugin

---

### Post by Ramses de Norre on 2006-08-04
Install it with aptitude =)
If you can't find it make sure you've got universe and multiverse enabled.
```
sudo aptitude update && sudo aptitude install sun-java5-plugin
```

---

### Post by bmonkey on 2006-08-04
Or get automatix :P

---

### Post by turner850 on 2006-08-04
i did what Norrre said and at the end I got

Couldn't find any package whose name or description matched "sun-java5-plugin"
The following packages have been kept back:
  gtk-gnutella
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Ramses de Norre on 2006-08-04
You'll need to add universe and multiverse as I allready said. And you might want to run a dist-upgrade too for that hold back package.

---

### Post by turner850 on 2006-08-04
Ok did what yea said, Its working now

Thank you Ramses de Norre,

Now all i have to do is wait for the download ;)

---

### Post by glatzor on 2006-08-18
You can also find Sun's Java in Applications->Install/Remove...

Just check "show unsupported" and "show commercial".

---

### Post by Dinerty on 2006-08-18
**Originally write by the **Artificial Intelligance** (Slightly updated for the new java)

If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick Linux self-extracting file. Download it to your Desktop.


```
 cd Desktop 
```

then

```
sudo apt-get install build-essential 
```

then

```
sudo apt-get install fakeroot java-package java-common 
```

then

```
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin 
```

then

```
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb 
```

then

 ```
 sudo update-alternatives --config java 
```


When asking for which version you want to choose pick;


```
 3 /usr/lib/j2sdk1.5-sun/bin/java 
```


Testing;


```
 java -version 
```



Making a Launcher for Java Control Center;


```
 sudo gedit /usr/share/applications/java.desktop 
```


fill in;


[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;


Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by cherylacbus1 on 2006-08-18
can't find java-package or make-jpkg.  I'm running Hoary 5.04

---

### Post by cherylacbus1 on 2006-08-18
Also, how do I install automatix and the others that were recommended on this thread?

---

### Post by Charkel on 2006-08-20
Thx for this ^^

---

### Post by David Corrales on 2006-08-20
I wouldn't go through the hassle of downloading and building the package. Before you had to do it, today it's in the repos.

---

### Post by alynx on 2006-08-20
Hi , im having this problem when i try to fakeroot make-jpkg **javapackage**

Thye error code is 
```

/usr/bin/fakeroot: line 150: make-jpkg: command not found


```

Can anybody please help ?

Edit : FIXED 8)

---


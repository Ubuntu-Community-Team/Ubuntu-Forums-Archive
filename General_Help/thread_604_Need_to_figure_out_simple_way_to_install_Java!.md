---
title: "Need to figure out simple way to install Java!?"
date: 2004-10-14
forum: General Help
---

### Post by ming0 on 2004-10-14
I can't get Java working--I have tried a number of suggestions.

On every other distribution I have used, it has been as easy as going to java.com and grabbing the j2re.bin file and then executing it as root...

With Ubuntu, I ```
sudo ./j2re.bin
``` It simply makes a directory with all of the files, but doesn't distribute the files or link any of the libraries. 

When I try executing a .jar file, I just get ```
bash&#58; java&#58; command not found
```

There must be an user friendly way to get Java working w/ Ubuntu?

I have tried the Ubuntu wiki suggestions, and I also tried this howto: [http://wiki.osuosl.org/display/DEV/Java+on+Debian](http://wiki.osuosl.org/display/DEV/Java+on+Debian)

but none of these work...

Please help!

--Dean

---

### Post by tsykoduk on 2004-10-14
I just grabbled the Java stuff from Synaptic - presto it worked. I needed to install a meta-package to get everything that I needed, and I canna recall what that was (away from Linux at moment) - if you need it, lemme know

---

### Post by ming0 on 2004-10-14
As far as I could tell, the stuff from synaptic wasn't the actual Sun Java RE.

The synaptic packages wouldn't run the application that lets me transfer music onto my mp3 player (rio karma), it just tells me that there are some java files missing when I try to run the music transfer program.

---

### Post by -baHam- on 2004-10-16
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

Click on linux binaries and download it.

Now in your console:

# cd /home/username/
# tar -xjvf javabinfilename.tar.bz2
# mv javabinfilename/ .java
# cd /usr/bin
# ln -s /home/username/,java/bin/java java

After doing that, run your LimeWire and install :)

---

### Post by bpmckie on 2004-10-16
I tried using your methos but when I try to install LimeWire it complains of no virtual machine. I normally put Java in /usr/local, but that didnt seem to work either. any other suggestions?

Brian

---

### Post by ming0 on 2004-10-16
OK, a few things

Very strange?? I can't run the LimeWireLinux.bin file as root or as normal user--and I can't modify the permissions of the file as root or as normal user :shock:  :shock: What am I doing wrong? below is a transcript of what happens:
```
dean@dim&#58;~/Programs/Linux Programs/Limewire $ ./LimeWireLinux.bin
bash&#58; ./LimeWireLinux.bin&#58; /bin/sh&#58; bad interpreter&#58; Permission denied
dean@dim&#58;~/Programs/Linux Programs/Limewire $ sudo ./LimeWireLinux.bin
Password&#58;
sudo&#58; unable to exec ./LimeWireLinux.bin&#58; Permission denied
dean@dim&#58;~/Programs/Linux Programs/Limewire $ chmod 777 LimeWireLinux.bin
dean@dim&#58;~/Programs/Linux Programs/Limewire $ ls -l
total 6164
-rwxr--r--    1 dean     root      6304734 Oct 16 06&#58;42 LimeWireLinux.bin
dean@dim&#58;~/Programs/Linux Programs/Limewire $ sudo chmod 777 LimeWireLinux.bin
dean@dim&#58;~/Programs/Linux Programs/Limewire $ ls -l
total 6164
-rwxr--r--    1 dean     root      6304734 Oct 16 06&#58;42 LimeWireLinux.bin

```

I got the tar.gz beta version of LimeWire, and was able to get it to run from the command line, but when I run it from the menubar like: java -jar /home/dean/LW/LimeWire.jar, I get a strange error dialogue that tells me my necessary files apper invalid, and that it is most likely due to a corrupted installation I also see a bug report, I'll post a little of it below:
```
java.util.MissingResourceException&#58; invalid logicrypto.jar
	at com.limegroup.gnutella.gui.Main.sanityCheck&#40;Main.java&#58;266&#41;
	at com.limegroup.gnutella.gui.Main.main&#40;Main.java&#58;48&#41;
```

Do you generally just run LimeWire from the command line, or were you able to get the normal binary version to work?

BTW, THANKS SO MUCH FOR HELPING ME GET JAVA WORKING! It was a stupid error on my part  :roll:  I am now able to transfer mp3's to my Karma :)

--Dean

---

### Post by kkennedy on 2004-10-19
Maybe not simple, and I haven't tried it on Ubuntu, but here is a link that may help...

[http://wiki.osuosl.org/display/DEV/Java+on+Debian](http://wiki.osuosl.org/display/DEV/Java+on+Debian)

---

### Post by cybrjackle on 2004-10-19
[quote=kkennedy]Maybe not simple, and I haven't tried it on Ubuntu, but here is a link that may help...

[http://wiki.osuosl.org/display/DEV/Java+on+Debian](http://wiki.osuosl.org/display/DEV/Java+on+Debian)[/quote]

That is the link I use on all of my ubuntu box's and the one I give to others, so I can confirm it does work ;)

I use 1.5.0

---


---
title: "Program only runs properly using sudo"
date: 2007-02-21
forum: General Help
---

### Post by onocrotalus on 2007-02-21
Hello, I installed a chess program called [Jin]("http://www.jinchess.com/"), placing the files in /usr/lib. I put a symlink to the script in /usr/bin. When I open a terminal and run jin as root, it works perfectly. When I run it as a user, the following happens in the terminal window:
```
~$ jin
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
```
Then the program window opens but the visuals are messed up and it isn't functional. Have I put the files in the wrong place? All files are chown root. I'd be grateful for any advice on how to fix this problem, as it's annoying to have to log put in my password every time I want to run Jin. 

I use Edgy. I suspect that the correct Java might not be being used when running it as user, even though I get the following version info, does this sound likely?
```
~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
~$
```
Thanks a lot in advance!

---

### Post by Kingsley on 2007-02-21
Maybe you need to copy the java folder to /usr/java.

---

### Post by onocrotalus on 2007-02-22
Thanks for the suggestion; I copied everything from /usr/lib/jvm to /usr/java, but it hasn't made any difference.

---

### Post by onocrotalus on 2007-02-23
Does anyone have any suggestions? I installed Java 5 via Synaptic, I can't see why it isn't working with correct user privileges. Maybe it's relevant that I can't install another chess program I want to try out, which I guess uses Java: after running the install.bin file for Varese, it stops with the following error: 
```
Exception in thread "main" java.lang.NoClassDefFoundError: com/zerog/lax/LAX
```

---


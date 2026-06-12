---
title: "Installing Java Media Framework"
date: 2005-09-21
forum: General Help
---

### Post by peterthebike on 2005-09-21
I have read what seems like hundreds of pages on how to install JMF.

Has anybody done on Ubuntu? How did you do it please?  :cry: 

I am using JMF 2.1.1e and have tried to install it with jdk1.5.0_04 and j2re1.4.2 (not at the same time <grn>) but none work in the [JMF - Diagnostics Applet](http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html) I keep getting the *JMF classes not found* error.

I have a Powerpoint presentation, that has sound, which I want to show using OpenOffice.

Peter

---

### Post by ant1060 on 2006-12-11
Dear Peter,
I would just like to ask if you have found a solution to the JMF problem in Ubuntu....as I am facing exactly the same problems.  I would love to hear from you.
Thanks.
Ant

---

### Post by peterthebike on 2006-12-14
Ant,

I am afraid I have regrettably gone back to M$. I cannot replace in Linux one application I have.

However, I tried and tried to install JMF but never succeeded - sorry.

---

### Post by razorbuzz on 2006-12-20
[http://isee.anywebcam.com/text/Dracosto.html](http://isee.anywebcam.com/text/Dracosto.html)  is a good source for getting JMF to work.  It worked flawlessly for me, on all three: Breezy, Dapper and now Edgy (clean installs each, thus sucessive installs of JMF).
Let me know if you need help.

---

### Post by GrumpyBob on 2006-12-21
I installed JMF on Edgy last week, as I needed to insert video in OO.o Impress.  I followed the instructions here:
[http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf](http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf)

However, note that there is an error in the second post, corrected further in that thread:

export LD_LIBRARY_PATH $JMFHOME/lib:${LD_LIBRARY_PATH}  should be

export LD_LIBRARY_PATH=$JMFHOME/lib:${LD_LIBRARY_PATH}

I had no trouble with getting videos to work in Impress after this.

Robert

---

### Post by gcordoba on 2007-11-06
Some times Linux is kind of annoying, eh?
When I try to run jmf...bin agai that results in:
.
.
JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
java.lang.Error: Can't open video card 0
java.lang.Error: Can't open video card 1
java.lang.Error: Can't open video card 2
java.lang.Error: Can't open video card 3
java.lang.Error: Can't open video card 4
java.lang.Error: Can't open video card 5
java.lang.Error: Can't open video card 6
java.lang.Error: Can't open video card 7
java.lang.Error: Can't open video card 8
java.lang.Error: Can't open video card 9
Done.

and the JMF classses are still not found.  The icons in OO are still gray...

Please, anu idea? Why is this stuff do not imlemented in synaptic?
Thanks,
Gustavo

---

### Post by scotty64 on 2007-11-14
I found two ways to get JMF running within OO 

1. Installing JMF where you like it to be and set the classpath with in OO
This does not need any work on your Java Runtime (JRE) installation:

In OO open Tools/Options and select Java.
-Click on the "Classpath" button on the right hand side and select "Add Archive".
-Now browse to the location of your jmf.jar file. In my case /usr/local/JMF-2.1.1e/lib/jmf.jar and click -"Open" to add that jar to the classpath.
-Restart OO and you will have sound in impress.

2. Install JMF within your java runtime environment and register it. This even allows playing MP3s when you install the java mp3 plugin as well:
-Download and unpack JMF and the mp3 plugin if needed [http://java.sun.com/products/java-media/jmf/mp3/download.html](http://java.sun.com/products/java-media/jmf/mp3/download.html)
-as root (sudo) copy jmf.jar and mp3plugin.jar into the lib/ext directory of your JRE
-run the following command in order to register the plugins with the java installation:
sudo java com.sun.media.codec.audio.mp3.JavaDecoder

---

### Post by gcordoba on 2007-11-15
Thanks for your reply:
I already have done the first advice. I even include the path of the directory. No success.
 I tryed your second advice resulting in:
gcordoba$ sudo java com.sun.media.codec.audio.mp3.JavaDecoder
Password:
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/media/codec/audio/mp3/JavaDecoder

It seems that java or oo. become lost. 
Looking for the installed java environments, according to oo., I have:

Sun Microsystems 1.5.0_10
Sun Microsystems 1.5.0_06
Blackdown java_linux Team 1.4.2-02
Free Software Foundation 1.4.2

I tryed with all without success. Any idea?

.

---

### Post by freezyOff on 2008-07-22
i have tried many times and read many tutorial to install this JMF. Btu none of it successfully install that JMF on my ubuntu hardy

i've done this :
chmod +x jmf-2_1_1e-linux-i586.bin
chmod +x jmf-2_1_1e-linux-i586.bin

--- after many question i've got this :

Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.6457: 1: cannot open ==: No such file
./install.sfx.6457: 1: ==: not found
./install.sfx.6457: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
Done.

any directory that should be create doesn't exist. how do i can install the class path or something else????:confused:

guys, please helpme!!!!!

---


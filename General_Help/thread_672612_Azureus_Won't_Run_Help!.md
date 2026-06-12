---
title: "Azureus Won't Run Help!"
date: 2008-01-19
forum: General Help
---

### Post by Tech_Power888 on 2008-01-19
Hi. I can't seem to get azureus to run after having installed it through synaptic.

This is the output error I get:

ryan@ryan-desktop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 328 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Now if I try "java -version" I get:

java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea Client VM (build 1.7.0-b21, mixed mode, sharing)

And when try alternative java, I get these options:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+       2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java


I have tried choosing all of them and none seem to work. Any help would be appreciated.  It was working fine but all of a sudden it isn't working at all. I haven't changed any setting s at all, I'm still running full vanilla ubuntu.

Any help would be greatly appreciated.

Ryan.

---

### Post by seamuso on 2008-01-19
did you update you xserver-xorg-core with the security update? What version are you running now?

Open synaptic and search for xserver-xorg-core .. my azureus broke last night with the update that was released yesterday .. I downgraded and everything worked great again .. 

I updated again this morning with the 8.3 version and everything has been working normally (I believe I was on 8.2 last night when I saw the problem).

---

### Post by ryanVickers on 2008-01-19
I never got it working, and even under windows it was always unstable and sould crash often.  I would recommend KTorrent or Deluge (the latest version from the website, not the one in the repositories ;))

---

### Post by Tech_Power888 on 2008-01-20
Thanks for the heads up, Ryan.I just got gutsy up and running on my second machine and Azureus seems to be working. However I may look into one of the other two for my main rig.

Ryan.

---


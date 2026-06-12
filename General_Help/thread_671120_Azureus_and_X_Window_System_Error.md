---
title: "Azureus and X Window System Error"
date: 2008-01-18
forum: General Help
---

### Post by litmos95 on 2008-01-18
After updating my system this morning, i can't get azureus run. The error message i got:
```

The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 343 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
Before updating the system, there was no problem. I just clicked OK to any updates today, don't even notice what they are, does anyone know what updates from today? 
I've tried to google, but haven't found any clue. Please help, since I really need it, as the only bt downloader which can handle chinese fonts. 

thanks in advance

My system:
Ubuntu feisty
sun java 6

---

### Post by ironclaw on 2008-01-18
Another thread on the same issue: [http://ubuntuforums.org/showthread.php?p=4159471]("http://ubuntuforums.org/showthread.php?p=4159471")

---

### Post by krebul on 2008-01-18
Same thing with me.  I did an update this morning and Azureus stopped working.  I also followed the link above and found that the last time this happened, people fixed it by downgrading xorg-core.  I tried downgrading to the previous version of xorg-core, but I'm still getting the same error:


Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [MOZILLA_FIVE_HOME may not point at an embeddable GRE] [NS_InitEmbedding /usr/lib/mozilla/ error -2147221164], InvocationTargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/mozilla for GRE
        Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: No more handles [MOZILLA_FIVE_HOME may not point at an embeddable GRE] [NS_InitEmbedding /usr/lib/firefox error -2147467259], InvocationTargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/usr/local/azureus" -Dazureus.install.path="/usr/local/azureus" -Dazureus.script="/usr/local/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 262 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

---

### Post by litmos95 on 2008-01-18
I did downgrade the xorg-core and it worked. Btw, this new xorg core does not just destroy many application, when i tried to lock screen it logged out to start screen.

---

### Post by krebul on 2008-01-18
Can you post your version of xorg-core please?

---

### Post by FRuMMaGe on 2008-01-18
Same here

---

### Post by bvucinic on 2008-01-18
same here!
downgraded xorg-core from 8.1 to 8.0

---

### Post by FRuMMaGe on 2008-01-18
> **bvucinic said:**
> same here!
downgraded xorg-core from 8.1 to 8.0

Yep. That sorted it for me.

However, it appears that it isn't working for some people.

Maybe they don't know you have to restart in order for it to take effect...

---

### Post by gaffin on 2008-01-18
I just spent two hours trying to figure out why Eclipse suddenly wouldn't start.  After installing different versions of Eclipse and different versions of the Java JDK, I miraculously stumbled on this:

[http://thread.gmane.org/gmane.linux.debian.devel.x/62705](http://thread.gmane.org/gmane.linux.debian.devel.x/62705)

which provides a workaround for the xorg bug without having to downgrade.

To save the click on the link, this is what you do:  add this:

```
         
        Section "Extensions"
                 Option "MIT-SHM" "no"
         EndSection

```

to your xorg.conf and restart xorg.  Suddenly, everything is good again.

cheers,

david

---

### Post by krebul on 2008-01-18
You, sir, are correct.  It didn't work immediately after downgrading xorg-core, but after restarting, its working fine now.

Thanks!

---

### Post by litmos95 on 2008-01-18
> **krebul said:**
> Can you post your version of xorg-core please?

I'll tell you as soon as i come back to my ubuntu, yet i'm on windows box :lolflag:. But if you go to synaptic package manager and search for xorg-core you'll find 2 items, click the xorg-core and then package->force_to. There should be a drop down list of its versions. There were only 2 versions listed on my installation, i chose the older one and restarted my system, and wala it worked!!!!

---

### Post by FRuMMaGe on 2008-01-18
> **gaffin said:**
> I just spent two hours trying to figure out why Eclipse suddenly wouldn't start.  After installing different versions of Eclipse and different versions of the Java JDK, I miraculously stumbled on this:

[http://thread.gmane.org/gmane.linux.debian.devel.x/62705](http://thread.gmane.org/gmane.linux.debian.devel.x/62705)

which provides a workaround for the xorg bug without having to downgrade.

To save the click on the link, this is what you do:  add this:

```
         
        Section "Extensions"
                 Option "MIT-SHM" "no"
         EndSection

```

to your xorg.conf and restart xorg.  Suddenly, everything is good again.

cheers,

david

However, this affects performance heavily, so be sure to change it back after a fix is found :)

---

### Post by Sir_Sid on 2008-01-18
How do you downgrade the xorg core

---

### Post by litmos95 on 2008-01-18
> **Sir_Sid said:**
> How do you downgrade the xorg core
"if you go to synaptic package manager and search for xorg-core you'll find 2 items, click the xorg-core and then package->force_to. There should be a drop down list of its versions. There were only 2 versions listed on my installation, i chose the older one and restarted my system, and wala it worked!!!!"

---

### Post by csulok on 2008-01-18
> [http://thread.gmane.org/gmane.linux.debian.devel.x/62705](http://thread.gmane.org/gmane.linux.debian.devel.x/62705)

which provides a workaround for the xorg bug without having to downgrade.

To save the click on the link, this is what you do:  add this:

```
         
        Section "Extensions"
                 Option "MIT-SHM" "no"
         EndSection

```

to your xorg.conf and restart xorg.  Suddenly, everything is good again.

cheers,

i can confirm this working.

next time please test your updates guys...

---

### Post by hihihi on 2008-01-19
he, that is funny, yesterday i saw it for the first time when startin azureus, azureus wont start, eclipse wont start, and it had to do with the latest upgrade of xorg-core cause before everything was working fine. 5 minutes ago, at the moment i found this site and i was thinking if i should cahnge xorg or downgrade, a new software-notification came in regarding xorg-core. i upgraded it, restartet the system and VOILA IT WORKS NOW FANTASTIC!! FORGET ALL THAT HAS BEEN SAID TILL NOW AND THANKS

---

### Post by litmos95 on 2008-01-19
> **hihihi said:**
> he, that is funny, yesterday i saw it for the first time when startin azureus, azureus wont start, eclipse wont start, and it had to do with the latest upgrade of xorg-core cause before everything was working fine. 5 minutes ago, at the moment i found this site and i was thinking if i should cahnge xorg or downgrade, a new software-notification came in regarding xorg-core. i upgraded it, restartet the system and VOILA IT WORKS NOW FANTASTIC!! FORGET ALL THAT HAS BEEN SAID TILL NOW AND THANKS

So maybe the developers have solved the bug and released the the update.

---

### Post by bvucinic on 2008-01-19
correct,
the bug has been resolved with xorg-core 8.3.
if you upgrade with synaptics things should work. :)

---

### Post by fotakis on 2008-06-27
This works with no sweat


[http://bearfruit.org/blog/2008/06/10/fixing-eclipse-after-the-firefox-3-rc1-update-in-ubuntu-8-04](http://bearfruit.org/blog/2008/06/10/fixing-eclipse-after-the-firefox-3-rc1-update-in-ubuntu-8-04)

---


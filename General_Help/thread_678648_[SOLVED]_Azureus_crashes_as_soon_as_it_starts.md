---
title: "[SOLVED] Azureus crashes as soon as it starts"
date: 2008-01-26
forum: General Help
---

### Post by NovaAesa on 2008-01-26
I just installed Azureus on my new 64 bit Gutsy installation. It doesn't seem to be working however, as soon as it starts it comes up with a windows that says something along the lines of 'downloading please wait' but then it disappears straight away. Here's the output from the terminal when I type in azureus.

```
aps@inspiron:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
DEBUG::Sat Jan 26 20:08:17 EST 2008  Data Missing /tmp/azupdater_1.8.3.zip
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ba3483e3e11, pid=9415, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/ps/.azureus/hs_err_pid9415.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
ps@inspiron:~$ 
```

hs_er_pid9415.log is attached in a bz2 archive. (It's referred to in the above terminal output so I figured it would be important for finding out what is wrong).

---

### Post by PmDematagoda on 2008-01-26
I believe you cannot use Azureus on IcedTea.

Install Java version 6 and update-alternative to use it as default Java.

---

### Post by NovaAesa on 2008-01-26
Thank you, I will report back when I have installed Java 6.

---

### Post by NovaAesa on 2008-01-26
Okay, so I installed java 6 with the following code:
```
sudo apt-get install sun-java6-bin
```
but what is this update-alternative thingy that I have to do? If you could give me a CLI code that could be great xD

---

### Post by taurus on 2008-01-26
It would allow you to configure which version of java to use as default.

```
sudo update-alternatives --config java
```

---

### Post by NovaAesa on 2008-01-27
Even though I've ran update-alternatives and picked java 6, it doesn't seem to be holding that option but rather reverting to the IcedTea java.

```
ps@inspiron:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
ps@inspiron:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
DEBUG::Sun Jan 27 18:56:38 EST 2008  Data Missing /tmp/azupdater_1.8.3.zip
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ba0002dae11, pid=6455, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/ps/.azureus/hs_err_pid6455.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
ps@inspiron:~$
```

Am I doing something wrong?

EDIT: Above (in the azureus output) is says something about environment AZUREUS_JAVA. Is this what I have to change? If so, how do I change it?

---

### Post by NovaAesa on 2008-01-27
bump

---

### Post by Sergiu on 2008-01-29
Hi. Try to delete the .azureus dir from home dir.

P.S. in the ubuntu repos there is an oldest verion of azureus, i will recommend to install the newer version..

---

### Post by NovaAesa on 2008-01-29
I deleted .Azureus and .azureus and it worked fine. It seems to being useing IcedTea however:

```
ps@inspiron:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
DEBUG::Wed Jan 30 13:32:47 EST 2008::org.gudy.azureus2.ui.swt.welcome.WelcomeWindow$3::runSupport::268:
    AEThread::run::69
org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: Error on connect for 'http://web.azureusplatform.com:80/az-web/releasenotes?version=2.5.0.4&locale=': 404 Not Found
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:486)
        at org.gudy.azureus2.ui.swt.welcome.WelcomeWindow$3.runSupport(WelcomeWindow.java:257)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
ps@inspiron:~$
```
But it's working, so I'm not complaining. xD

Thanks for the help guys!

---


---
title: "Need to install old java and link in firefox"
date: 2014-01-20
forum: General Help
---

### Post by sunshineacid on 2014-01-20
Hey all,

I need to install a very specific version of java: 1.6.0.20 for a Cisco application that they refuse to update that I need to run on some client machines.
Initially, I used the webupd8 method to run the java 6 installer, and it installed the latest version java 6u45, installed the browser plugins automatically, etc. I tested on the application, and it refused to run, so I attempted to install jre6u20 by downloading the bin from the oracle site, extracting in /usr/lib/jvm. I set the paths that I am aware of, restarted, and the java version verification page, and the about:plugins page in firefox keep indicating that I am running the jre6u45 plugin. 

java -version gives me: java version "1.6.0_20" so I believe I have it installed correctly at least.

I have deleted usr/lib/mozilla/plugins/libnpjp2.so several times, and created a new link to /usr/lib/jvm/jre1.6.0_20/lib/i386/libnpjp2.so rebooted both firefox and my computer, and it still tells me that I am running jre6u45.

What am I doing wrong here? Any help would be appreciated.

---

### Post by QIII on 2014-01-20
Hello!

If you can find the appropriate file on Oracle's site, you can follow the instructions [here]("https://sites.google.com/site/easylinuxtipsproject/java") to install a particular version.  Just replace the correct file name.

I would recommend, however, that you only use that version for that particular purpose and then change your alternative to a more recent version the rest of the time.  (You can have multiple versions installed and choose between them using the terminal.)

Cheers!

---

### Post by sunshineacid on 2014-01-20
Thank you for your quick reply. I have gone through those steps, with the exception of uninstalling the openjdk plugins. I didn't think it was necessary, as firefox is showing that its using oracle java 1.6 update 45. I uninstalled it just now in the case that I was mistaken, restarted firefox, and nothing seems to have changed. I feel like the issue lies with a variable that the webupd8 package changed that I am not aware of, or I am somehow pulling the wrong libnpjp2.so file, or firefox is using a different file than libnpjp2.so file all of the guides state that it does.

FWIW, this is my java section in firefox about:plugins:

Java(TM) Plug-in 1.6.0_45

    File: libnpjp2.so
    Path: /usr/lib/jvm/java-6-oracle/jre/lib/amd64/libnpjp2.so
    Version: 
    State: Enabled (STATE_VULNERABLE_UPDATE_AVAILABLE)
    The next generation Java plug-in for Mozilla browsers.

The actual file that I want it to link to is: /usr/lib/jvm/jre1.6.0_20/lib/i386/libnpjp2.so
The command I thought I should be using was: ln -s /usr/lib/jvm/jre1.6.0_20/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/libnpjp2.so

---


---
title: "Rkhunter found some infections"
date: 2014-10-09
forum: General Help
---

### Post by Robbyx on 2014-10-09
I have just run rkhunter 1.4 and it has reported the following positives. What should I do about them?

> Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-1.7.0-openjdk-i386.jinfo

Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED

Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! tty-servlets.jar:/usr/share/i2p/lib/jetty-start.jar:/usr/share/i2p/lib/jetty-util.jar:/usr/share/i2p/lib/jetty-webapp.jar:/usr/share/i2p/lib/jetty-xml.jar:/usr/share/i2p/lib/jrobin.jar:/usr/share/i2p/lib/jstl.jar:/usr/share/i2p/lib/mstreaming.jar:/usr/share/i2p/lib/org.mortbay.jetty.jar:/usr       0 /i2p/lib/jetty-servlet.jar:/usr/shtty-servlets.jar:/usr/share/i2p/lib/jetty-start.jar:/usr/share/i2p/lib/jetty-util.jar:/usr/share/i2p/lib/jetty-webapp.jar:/usr/share/i2p/lib/jetty-xml.jar:/usr/share/i2p/lib/jrobin.jar:/usr/share/i2p/lib/jstl.jar:/usr/share/i2p/lib/mstreaming.jar:/usr/share/i2p/lib/org.mortbay.jetty.jar:/usr b/jetty-start.jar:/usr/share/i2p/lib/jetty-util.jar:/usr/share/i2p/lib/jetty-webapp.jar:/usr/share/i2p/lib/jetty-xml.jar:/usr/share/i2p/lib/jrobin.jar:/usr/share/i2p/lib/jstl.jar:/usr/share/i2p/lib/mstreaming.jar:/usr/share/i2p/lib/org.mortbay.jetty.jar:/usr
! root         1499 tty7   /usr/bin/X :0 -background none -noreset -verbose -auth /var/run/gdm/auth-for-gdm-mkm1d2/database -seat seat0 -nolisten tcp vt7



---

### Post by TheFu on 2014-10-10
Is there any reason for java to be loaded on the system?  If not, I'd wipe the system and start over, this time paying more attention to security.

OTOH, could this be a false positive? [https://www.reddit.com/r/linux4noobs/comments/1kevsr/suckit_rootkit_warning_sbininit_infected/](https://www.reddit.com/r/linux4noobs/comments/1kevsr/suckit_rootkit_warning_sbininit_infected/)

---

### Post by Robbyx on 2014-10-11
I suspect it was a false +.

If I remove Java will many programs stop working?

---

### Post by TheFu on 2014-10-11
> **Robbyx said:**
> I suspect it was a false +.

If I remove Java will many programs stop working?

Many?  Guess that depends on what you consider "many."

NONE of the core OS programs are written in Java.
I don't have it loaded on 99% of my systems and actively avoid programs that require it.

When you tell the package manager to remove it, a list of packages will be shown. Look through that list to see if anything you like is there.  It isn't like you can't put it back later or it will be added back when a java-based program is installed.  The only reason I'd worry is if you have low data caps from the ISP or a slow connection.

On a desktop here with "freemind", **aptitude** says it wants to remove these:
      Remove the following packages:              
1)      ca-certificates-java                      
2)      default-jre                               
3)      default-jre-headless                      
4)      freemind                                  
5)      icedtea-7-jre-jamvm                       
6)      javahelp2                                 
7)      libatk-wrapper-java                       
8)      libatk-wrapper-java-jni                   
9)      openjdk-7-jre                             
10)     openjdk-7-jre-headless

So ... freemind is the only real program on the box using java.  I decided to remove it with aptitude, which cleans up the unneeded packages automatically. Thanks.

---

### Post by Robbyx on 2014-10-11
I followed your advice with  sudo aptitude purge freemind

Thanks

---

### Post by TheFu on 2014-10-11
Uh - was freemind on your system?  Was java removed?

---

### Post by Robbyx on 2014-10-11
> **TheFu said:**
> Uh - was freemind on your system?  Was java removed?

I installed freemind using synaptic and then removed it using aptitude and about 20 extra dependancies were removed, but looking at synaptic openjdk-7-jre is still installed!

---

### Post by Robbyx on 2014-10-13
It is not easy to remove openjdk-7-jre because synaptic agrees to remove it but to substitute another version.

Using aptitude I instructed it to remove openjdk-7-jre but instead nvidia-settings and  linux generic headings were removed.

---

### Post by TheFu on 2014-10-13
> **Robbyx said:**
> Using aptitude I instructed it to remove openjdk-7-jre but instead nvidia-settings and  linux generic headings were removed.

This makes zero sense.  Neither of those depend on java.

---

### Post by Robbyx on 2014-10-14
I agree, but that did happen, so I have done a fresh reinstall. 

In the new install the software center also wants to remove Vuze, in synaptic it will install icedtea-6 and openjdk-6. I did not see what aptitude wanted to do.

---

### Post by TheFu on 2014-10-14
I used Vuze for a few days about 10 yrs ago - it was java then.

You can ask APT (through dpkg or aptitude) which packages depend on jre. Perhaps asking would be helpful? I don't use btorrent.
```
aptitude why jre
```

Be certain you understand how to read the output. Suggested packages will be in that list too, not required packages.

---


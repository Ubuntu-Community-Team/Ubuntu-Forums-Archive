---
title: "Azureus crashing"
date: 2007-04-18
forum: General Help
---

### Post by vishnumrao on 2007-04-18
Hi all,


I had Azureus working till a few days back.  Now Azureus fails to run. Starts off and then upon bring ing up the window, it crashes.

Here is what I see when i run Azureus from the command line.

vishnumrao@vishnumrao-desktop:~$ azureus
DEBUG::Wed Apr 18 19:48:25 PDT 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Wed Apr 18 19:48:26 PDT 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Segmentation fault (core dumped)
vishnumrao@vishnumrao-desktop:~$ 

Segmentation fault! what is a segmentation fault? Can someone throw some light on the error here and a fix to it.

Thanks in advance,

Vishnu Rao.

---

### Post by iansyngin on 2007-04-20
Yes i have also noticed the same problem.
This issue is logged in the ubuntu bugs database: launchpad
They think it is due to the notice that appears when azureus sometimes starts up warning that azureus did not shut down properly.
The temporary way around the problem is to use a different java virtual machine i think.

sudo update-alternatives --config java

and choose:
gij wrapper

option 1 or 2

---

### Post by dkaplowitz on 2007-04-21
> **iansyngin said:**
> The temporary way around the problem is to use a different java virtual machine i think.
...gij wrapper
Cool, that worked for me. Thanks!

Dave

---

### Post by Red Knuckles on 2007-04-21
You can change which java you use. Run:

sudo update-alternatives --config java

and in my case I have:

There are 3 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-6-sun/jre/bin/java
2 /usr/bin/gij-wrapper-4.1
+ 3 /usr/lib/jvm/java-gcj/jre/bin/java


and choose option 3 instead of 1 and Azureus stays open. OR if you DO want to use latest version of Sun-Java you could run:

sudo aptitude purge azureus

Then Download Azureus tar ball at Azureus website:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

I downloaded to /home/me and then ran:

@localhost:~$sudo mv Azureus_2.5.0.4_linux.tar.bz2 /usr/bin
@localhost:~$cd /usr/bin
@localhost:/usr/bin$sudo tar -xjvf Azureus_2.5.0.4_linux.tar.bz2
@localhost:/usr/bin$sudo rm *.bz2

Then in K-Menu Editor [or whatever in Gnome] change whatever the old command for the Azureus entry to '/usr/bin/azureus/azureus'. You will now have to run updates from within Azureus as root, ie. 'sudo /usr/bin/azureus/azureus'. And now your Azureus will stay open and use latest version of Sun-Java!

:lolflag: 
:guitar:

---

### Post by crav on 2007-04-23
I have this same problem, I've tried changing virtual machines and i get the same problem again. Any ideas?

---

### Post by Red Knuckles on 2007-04-23
> **crav said:**
> I have this same problem, I've tried changing virtual machines and i get the same problem again. Any ideas?

Have you tried removing the version of Azureus installed from Ubuntu repos [as described in my last post] and installing Azureus with tar ball from Azureus website. That should work.

sudo aptitude purge azureus

Then Download Azureus tar ball at Azureus website:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

I downloaded to /home/me and then ran:

@localhost:~$sudo mv Azureus_2.5.0.4_linux.tar.bz2 /usr/bin
@localhost:~$cd /usr/bin
@localhost:/usr/bin$sudo tar -xjvf Azureus_2.5.0.4_linux.tar.bz2
@localhost:/usr/bin$sudo rm *.bz2

Then in K-Menu Editor [or whatever in Gnome] change whatever the old command for the Azureus entry to '/usr/bin/azureus/azureus'. You will now have to run updates from within Azureus as root, ie. 'sudo /usr/bin/azureus/azureus'. And now your Azureus will stay open and use latest version of Sun-Java!

---

### Post by crav on 2007-04-23
Red Knuckles:

This worked perfectly! Thanks so much!

(This is also the first time I've been able to install from a .tar with no problems at all)

---

### Post by Red Knuckles on 2007-04-23
> **crav said:**
> Red Knuckles:

This worked perfectly! Thanks so much!

(This is also the first time I've been able to install from a .tar with no problems at all)

Always glad to help a fellow Linux user. Many have helped me along the way.
:guitar:

---

### Post by Arup on 2007-04-23
Azureus runs like a dream on my machine, I use Java JRE 1.6 from the repositories, in fact compared to Ubuntu 6.10, this one is a dream run.

---

### Post by mwnovak on 2007-04-24
Just to follow up...

Was having the exact same problem described in the OP, then ran the suggested utility:

```
sudo update-alternatives --config java
```

Azureus started up just fine and stayed open.  Then I got the little pop-up telling me that Azureus hadn't shut down properly.  For grins and giggle, I quit Azureus, ran the Java utility again, returned/re-activated the default provider, and launched Azureus again.  It now starts and runs again just fine with the default Java provider. :)

Thanks all,

--MW

---

### Post by warmfusion on 2007-07-01
Additionally, the reason for the crash is from the sliding window effect used for the Error message about not shutting down correctly. If you can get as far as editing the options goto:
Interface>>Display and TICK the "Disable sliding animation/on top style for alert" which will hopefully solve the problems and allow you to go back to a more robust implementation of java for your applications.

Warmfusion

---


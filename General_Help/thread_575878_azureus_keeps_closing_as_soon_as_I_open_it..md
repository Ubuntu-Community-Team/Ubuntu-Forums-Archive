---
title: "azureus keeps closing as soon as I open it."
date: 2007-10-14
forum: General Help
---

### Post by onesojourner on 2007-10-14
the title pretty much says it all. I have this installed on 7.10 rc. when I open it it loads up and I get to the main window for about 2 seconds the task bar icon pops up too and then it just closes itself. all I have done is downloaded peer guardian and stuck it in the plugins directory.

---

### Post by liquidfunk on 2007-10-14
Yeah that happens with mine too.

 I switched to Ktorrent. It appears to download faster too.

---

### Post by ThrobbingBrain66 on 2007-10-14
> **onesojourner said:**
> the title pretty much says it all. I have this installed on 7.10 rc. when I open it it loads up and I get to the main window for about 2 seconds the task bar icon pops up too and then it just closes itself. all I have done is downloaded peer guardian and stuck it in the plugins directory.

You should remove Peer Guardian from the plugins folder and install it through Azureus.

If that doesn't work, use a terminal to start Azureus and post any output/errors here.

---

### Post by wormser on 2007-10-14
This [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13") fixed my Azureus issues.  If the repositories still has the old Azureus2.jar then this fix might work.

> Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by onesojourner on 2007-10-15
well I Azureus3.0.3.4.jar copied over to my java folder. its still doing the same thing. shoud I delete the old azureus2.jr or do they both need to be in there? or do I need to rename the new file to Azureus2.jv?

---

### Post by onesojourner on 2007-10-15
ok I tried just adding the Azureus3.0.3.4.jar file to the java folder with the azureus2.jar and I still had the same problem. then I tried deleting the azureus2.jar file and renaming the Azureus3.0.3.4.jar file to azureus2.jar and that didn't do anything. I have also tried deleting the safepeer plugin and that didn't do anything.

---

### Post by onesojourner on 2007-10-15
here is what I get when I run azureus from terminal

```
peter@peter-desktop:/usr/share/java$ azureus
DEBUG::Mon Oct 15 00:40:18 GMT-05:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Mon Oct 15 00:40:22 GMT-05:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
DEBUG::Mon Oct 15 00:40:34 GMT-05:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl::select::528:
  VirtualChannelSelector: No progress for op 1: listener = class com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$2, count = 10, socket: open = true, connected = true
    VirtualChannelSelector::select::272,NonBlockingReadWriteService$1::runSupport::79,AEThread::run::69
Aborted (core dumped)
peter@peter-desktop:/usr/share/java$ 

```

---

### Post by onesojourner on 2007-10-15
I tried a complete removal and reinstalling. It is still doing the same thing.

---

### Post by wormser on 2007-10-15
It looks like they are now on version 3.  This solution will not work unless you can find the last Azureus2.jar released.  You could just try renaming the new one to Azureus2.jar.  It probably will not work but it would be interesting to try.

---

### Post by hevymetldude on 2007-10-15
try this

```
sudo update-alternatives --config java
```

should bring this
```
  Selection    Alternative 
----------------------------------------------- 
 +        1    /usr/lib/jvm/java-gcj/jre/bin/java 
*         2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 
          3    /usr/bin/gij-wrapper-4.1
```

then choose the wrapper option 
and start azureus again...it should work...
though it seems to run slower...

close azureus with the file/quit menu.
DO NOT ever close Azureus over the windowmanager...it seems to just crash azureus.

---

### Post by chunchengch on 2007-10-15
If you have SCIM installed, try this to make Azureus 3.0.3.4 work, it works for me on Ubuntu 7.10:

1. I assume you extract/install Azureus tar file under /home

$ gedit /azureus/azureus

2. copy this line "export GTK_IM_MODULE=xim" (no quotes) to the beginning of the file azureus, and then save it.

3. now you should be able to run Azureus

---

### Post by maikie on 2007-10-24
> **hevymetldude said:**
> try this

```
sudo update-alternatives --config java
```

should bring this
```
  Selection    Alternative 
----------------------------------------------- 
 +        1    /usr/lib/jvm/java-gcj/jre/bin/java 
*         2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 
          3    /usr/bin/gij-wrapper-4.1
```

then choose the wrapper option 
and start azureus again...it should work...
though it seems to run slower...

close azureus with the file/quit menu.
DO NOT ever close Azureus over the windowmanager...it seems to just crash azureus.

Thank you

Worked amazingly

---

### Post by GreenMeanie on 2007-10-24
I switched to Deluge for the same reason.

---

### Post by jenhsun on 2007-10-25
> **GreenMeanie said:**
> I switched to Deluge for the same reason.

me too. But not this reason.
I switch because the performance and the look with GNOME.

---

### Post by teeheenah on 2008-07-19
I'm not sure if this will help anyone else but I had the same problem.  Az would run for about 5 minutes at a time before closing without warning.  What fixed it for me was to update my java.  I was running on v6 update 5 and updated to v6 update 7.  Running like a dream now.

T-

---

### Post by onesojourner on 2008-07-22
Just a heads up, I have switched to utorrent since I created this thread and I am having much better luck.

---


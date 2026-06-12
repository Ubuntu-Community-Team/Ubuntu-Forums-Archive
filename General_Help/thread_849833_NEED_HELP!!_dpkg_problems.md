---
title: "NEED HELP!! dpkg problems"
date: 2008-07-04
forum: General Help
---

### Post by Nasty_Ben on 2008-07-04
First of all, I am a quite new with Ubuntu so excuse my ignorance.  I have searched for a solution but none have helped my problem.  When I go to the installer or try to do an upgrade I get the error:

 "E: dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem". 

  I've tried running that command with sudo and all that happens is my pc freezes for awhile then the problem persists.  I also tried the sudo apt-get -f install but I get a long freeze then the same error message.  Any help would be greatly appreciated.

EDIT:  I know the problem is Java too.  The error returned a message saying something about an incomplete Java installation but it can't fix itself.

---

### Post by VMC on 2008-07-04
Have you tried cleanup command:

```
sudo apt-get clean
sudo apt-get autoremove

```
Also, try removing rebooting and reinstalling have.

---

### Post by Nasty_Ben on 2008-07-04
I get the same error message for any apt-get command.

---

### Post by Nasty_Ben on 2008-07-04
Come On One Some One Must Be Able To Help!!!

---

### Post by tamoneya on 2008-07-04
can you post the complete output of the error talking about incomplete java installation.  You can either copy out of terminal with ctrl-shift-c or redirect the output to a text file like so:```
sudo apt-get update >myfile.txt
```


Please dont bump for 24 hours

---

### Post by Nasty_Ben on 2008-07-04
here is the error:

ben@Ben-Ubuntu:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/COLOR]
ben@Ben-Ubuntu:~$ 

and running that command does nothing.

---

### Post by tamoneya on 2008-07-04
I was looking for the error pertaining to java that you mentioned in your first post.

---

### Post by napzilla on 2008-07-04
I'm not an expert, so corrections or confirmation by someone more knowledgeable would be welcome!

I had similar problems at one point and this helped:

First, try removing the broken package with dpkg and reinstalling it (if you need it). You mentioned that the problem was a broken Java install, so the following command should help you find out which package is broken:
```
dpkg -l | grep 'java'[\CODE]
This will return all the packages dpkg knows of that have 'java' in their names. To identify the faulty package, check the status (that's the first column, the one with two letters). 'ii' indicates that the package is installed and configured properly. 'rc' indicates that only the package has been removed and only the configuration files remain. The broken package will have a different status. Once you identify it, you can try to remove it with dpkg using the following command (as root--sudo--of course!).
[CODE]dpkg -r <packagename>
```

If that doesn't work, then you can try removing the package name from dpkg's list the hard way. First, back up the status file:
```
cp /var/lib/dpkg/status ~/dpkg-status.bak
```
Then open the status file with a text editor as root--e.g.:
```
sudo vi /var/lib/dpkg/status
```
and find the broken package. Once you find it, remove all the lines of text associated with that package and save the file.

Once you've removed the broken package, update your package list
```
apt-get update
```

I learned this technique from another posting by someone who was having troubles with openssh-server ([http://kubuntuforums.net/forums/index.php?topic=13297.msg53029#msg53029](http://kubuntuforums.net/forums/index.php?topic=13297.msg53029#msg53029)).

Assuming you actually want the package, you can now try to install it again with apt. If you're trying to install the proprietary version of the Java Development Kit, you might still have to download the source files from Sun's website ([http://java.sun.com](http://java.sun.com)). I don't know for certain, though.

Good luck!

---

### Post by Nasty_Ben on 2008-07-04
OK here it is:

ben@Ben-Ubuntu:~$ sudo dpkg --configure -a
Setting up java-common (0.28ubuntu3) ...
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : AttValue: ' expected
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : attributes construct error
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : Couldn't find end of Start Tag sect line 316
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : Premature end of data in tag sect line 290
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : Premature end of data in tag sect line 6
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^
/var/lib/scrollkeeper/ru/scrollkeeper_cl.xml:316: parser error : Premature end of data in tag ScrollKeeperContentsList line 2
      <sect categorycode="ApplicationsUtilitiesTex
                                                  ^

---

### Post by tamoneya on 2008-07-04
try what napzilla has mentioned.  That method should work pretty well.  If however that doesnt work for you post the contents of /var/lib/scrollkeeper/ru/scrollkeeper_cl.xml.  It may be best to attach the file instead of posting inline since it will be fairly wrong.  If I am not mistaken it seems as if this file just got a little messed up and it may be a simple fix.

---

### Post by Nasty_Ben on 2008-07-04
I found the corrupt entry and it says:

Package: java-common
Status: install ok half-configured
Priority: optional
Section: misc
Installed-Size: 364
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 0.28ubuntu3
Suggests: equivs
Conffiles:
 /etc/jvm e2f2c42a5f693b0a115bc1025f058e08

how can i configure the other half?

---

### Post by tamoneya on 2008-07-04
remove it first with ```
sudo dpkg -r java-common
``` then run: ```
sudo dpkg --configure -a
``` Then do an update and upgrade

---

### Post by Nasty_Ben on 2008-07-04
it says illegal opperation for the -r

removing the bad part of the status file did nothing btw

---

### Post by VMC on 2008-07-04
The one time I really messed up installing some package, and nothing seemed to work. I rebooted and typing:

```
sudo dpkg --configure -a
```

Then worked. Just a thought.

---

### Post by Nasty_Ben on 2008-07-04
i just got into the aptitude thing and all i have to do is figure out how to uninstall java.

---

### Post by tamoneya on 2008-07-04
> **Nasty_Ben said:**
> it says illegal opperation for the -r

removing the bad part of the status file did nothing btw

Can we get the exact output.  Are you certain you didnt make any typos.  should look identical to this: ```
sudo dpkg --configure -a
```

---

### Post by Nasty_Ben on 2008-07-04
no typos, the error is the exact same as earlier posted

I'm onto something here, i typed sudo aptitude and i am currently figuring it out

---

### Post by l0fls on 2008-07-05
have you tried doing exactly what it suggests type into terminal
> dpkg --configure -a

---

### Post by Nasty_Ben on 2008-07-05
of course, and i still get the error

---

### Post by Nasty_Ben on 2008-07-05
OK its over with the aptitude thing allows removal so java-common has been obliterated.  Sometime down the road I'll reinstall it but I've had enough for tonight.  Thanks for helpin tamoneya, I've learned a lot.

---


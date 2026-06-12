---
title: "Eclipse+PDT"
date: 2007-11-22
forum: General Help
---

### Post by raxz on 2007-11-22
Not getting any response from the programming thread so I hope I can get some answers here: :)

Hi all,

I want to install PDT on my Eclipse 3.2 and I am running on Gutsy.

I tried following [http://www.thierryb.net/pdtwiki/inde...Installing_PDT](http://www.thierryb.net/pdtwiki/inde...Installing_PDT)

I used the "automated" approach but I get this error:

"PDT Feature (1.0.1.v20071001-79-78E7QYGHEPGGP) requires feature "org.eclipse.wst (2.0.0)", or compatible"

I checking my Eclipse Project SDK I found this configuration:


Included feature "Eclipse Platform" version "3.2.2.r322_v20070119-CXMbUe9K_WF26uA" contains problems.

Included feature "Eclipse Platform Plug-in Developer Resources" version "3.2.2.r322_v20070119-CXMbUe9K_WF26uA" contains problems.

Included feature "Eclipse Java Development Tools" version "3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" contains problems.

Included feature "Eclipse JDT Plug-in Developer Resources" version "3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" contains problems.

Included feature "Eclipse Plug-in Development Environment" version "3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG" contains problems.


Is there a particular SDK that Eclipse does not like?

help?

----edit---

after some searching in the forums I found a similar problem: [http://ubuntuforums.org/showthread.php?t=385895&highlight=eclipse+PDT](http://ubuntuforums.org/showthread.php?t=385895&highlight=eclipse+PDT)

unfortunately the issue was not resolved....any help?

---

### Post by nnico on 2007-11-24
Hi,

I have the same problem, did you solve it ? 

Nico

---

### Post by coldNsunny on 2007-11-25
Hi,
I am not sure if this will be much help but I downloaded the all-in-one version of Eclipse PDT (eclipse 3.3) and  extracted it to /opt/ fixed up my java_home file to point to java-6-sun-1.6.0.00 and altered the JAVA_HOME setting in ~/.eclipse/eclipserc as suggested in the java_home file and everything is working well - except I have to start a new thread for a debugging problem.  Sorry I couldn't be more help.
Scott.

---

### Post by calvinkim on 2007-11-26
> **raxz said:**
> http://www.thierryb.net/pdtwiki/inde...Installing_PDT[/url]

 
You need Eclipse 3.3 or a Europa Bundle for PDT 1.0.
Visit [http://wiki.eclipse.org/PDT/FAQ](http://wiki.eclipse.org/PDT/FAQ) and 
[http://www.eclipse.org/pdt/install.php](http://www.eclipse.org/pdt/install.php) for more info.

---

### Post by raxz on 2007-11-28
> **coldNsunny said:**
> Hi,
I am not sure if this will be much help but I downloaded the all-in-one version of Eclipse PDT (eclipse 3.3) and  extracted it to /opt/ fixed up my java_home file to point to java-6-sun-1.6.0.00 and altered the JAVA_HOME setting in ~/.eclipse/eclipserc as suggested in the java_home file and everything is working well - except I have to start a new thread for a debugging problem.  Sorry I couldn't be more help.
Scott.

Could you please elaborate more on these steps?

How do I do each one?:confused:

---

### Post by kk_furtiva on 2008-01-08
Ubuntu has Eclipse 3.2 in its repositories but the latest PDT (1.0) works only with Eclipse 3.3 so in order to get PDT to work you have to download and install Eclipse 3.3 (from Eclipse's web page) or downgrade PDT version and install PDT 0.7 which works with Eclipse 3.2. To do this just add the "New remote site" for PDT in the "Find and install" screen and uncheck the "Show latest version of feature only" in the Search Result screen where you select the features to install. Then you will be able to select version 0.7 and install it.

Cheers,
Leandro

---

### Post by masher_oz on 2008-01-26
I've downloaded eclipse 3.3 from their website, I've untarred (currently in tmp as I'm just playing with it) it works, and I can code in it and stuff...

How would I go about installing it so that it is recognised from the command line?

I get told that "The program 'eclipse' is currently not installed" evn if I'm in the directory with the eclipse executable...

---

### Post by ayoli on 2008-01-26
I use eclipse pdt complete (with all needed plugins) pack from zend ([here]("http://downloads.zend.com/pdt/all-in-one/pdt-1.0.2.R20080103_debugger-5.2.12.v20071210-all-in-one-linux-gtk.tar.gz")).
Before I've installed sun-java6-* packages:
```
sudo apt-get install sun-java6-bin sun-java6-jdk sun-java6-jre
```
then I made a short script in my /usr/local/bin like this :
```
sudo gedit /usr/local/bin/eclipse
```
I've put those lines :
```
#!/bin/sh

# eclipse dir
ECLIPSE_DIR="/path/to/wherever/you/extracted/eclipse"

# start eclipse
$ECLIPSE_DIR/eclipse
```
then you can add a launcher to your dock/panel/menu or launching it with run dialog (ALT F2) or from the CLI.

---

### Post by mhf on 2008-01-27
Hi raxz

> I used the "automated" approach but I get this error:

"PDT Feature (1.0.1.v20071001-79-78E7QYGHEPGGP) requires feature "org.eclipse.wst (2.0.0)", or compatible"

I checking my Eclipse Project SDK I found this configuration:

In case you have'nt sloved it then here how I tamed the beast. It took me many frustrating hours before I solved it. Actually it is very easy.

Do what you normally do for updates i.e 

Help > Software Updates > Find and Install... > 
  (*) Search for new features > Next > 
  [x] Europa Discovery Site > 

PTD runs on the top of WST therefore you have to install WST first
- Expand WEB and JEE development and choose WST
You will get and error of the same nature you godt before don't mind 
**- Just click on select required (the error will disapear)**
-Click finish

**Now go back and repeate the same procedure for PTD (when get the error just click on select required)**

This will solve you problem.
fayez

---

### Post by jimmyxx on 2008-04-10
> **mhf said:**
> In case you have'nt sloved it then here how I tamed the beast. It took me many frustrating hours before I solved it. Actually it is very easy.


Thanks, that worked for me :)

---


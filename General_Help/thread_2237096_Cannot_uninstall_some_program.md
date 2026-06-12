---
title: "Cannot uninstall some program"
date: 2014-07-30
forum: General Help
---

### Post by lobosuelto on 2014-07-30
Hey guys, so I downloaded some software which I think runs in Java, not sure, not a tech or anything like it ... Its called SEO Power Suite ([http://www.link-assistant.com/](http://www.link-assistant.com/)) and it doesn't show in Software Center nor Synaptic, and the only way it can be run is by typing the names of the 4 programs that come in the Suite in the terminal (Rank Tracker, Website Auditor, Spyglass and LinkAssistant). Please help!!!

command line when I open one of the 4 programs:

~$ seospyglass 
About: Initializing Application...
About: Environment:
    OS name: Linux (version 3.13.0-32-generic)
    OS arch: amd64
    Java version: 1.8.0_11
    JVM bitness: 64
About: SEO SpyGlass 5.14.1 starting...
About: Loading Application Settings...
Jul 30, 2014 6:10:24 PM com.agilemind.commons.gui.locale.DefaultButtonLocalizator reloadLanguage
WARNING: Nor text nor icon defined for com.agilemind.commons.gui.locale.keysets.BundleButtonStringKeySet@5c08c46a
Jul 30, 2014 6:10:24 PM com.agilemind.commons.gui.locale.DefaultButtonLocalizator reloadLanguage
WARNING: Nor text nor icon defined for com.agilemind.commons.gui.locale.keysets.BundleButtonStringKeySet@61ce23ac
About: Checking for the latest version...
About: Adjusting Application Window...


The files of the programs are in /Home/ in folders that are named after the program (eg .seospyglass)

---

### Post by QIII on 2014-07-30
Hello!

How did you install these?

---

### Post by lobosuelto on 2014-07-30
It was a tar.gz archive so I think so

I think I navigated to the containing folder with the cmnd line as root and then ran "./" on a "install.sh" file that contains this when opened with gedit:

#!/bin/bash

if [ $UID != "0" ] ; then
    echo -e "You need to be ${red}ROOT${coloroff} to run this script, sorry..."
    echo -e "Press ${blue}ENTER${coloroff} to exit the installer."
    read
    exit 1
fi

cd distr/commons/bin/ 

java -jar macinstall.jar seopowersuite

---

### Post by Erik1984 on 2014-07-30
What if you run

```
which seospyglass
```

?

That should give you the location of the executable (likely /usr/bin) but other files of the program are likely not in that folder.

You can also unpack that install file (macinstall.jar, a jar is just an archive like a zip) to look at the source files inside. There should be a .java file inside containing the directories where the script copies the files to.

On the other hand, you shouldn't worry too much about this. These programs you 'installed' only take up space on the disk, they won't slow down your system (unless they have some auto starting service in the background).

---

### Post by lobosuelto on 2014-07-30
$ which seospyglass 
/usr/local/bin/seospyglass

"You can also unpack that install file (macinstall.jar, a jar is just an  archive like a zip) to look at the source files inside. There should be a  .java file inside containing the directories where the script copies  the files to." please elaborate, sorry, complete newbie here.

So I navigated to /usr/local/bin/ and found that it contains the 4 programs names:

[http://es.tinypic.com/view.php?pic=20pcv9u&s=8#.U9lputYcfQo](http://es.tinypic.com/view.php?pic=20pcv9u&s=8#.U9lputYcfQo)

And, [**[COLOR=#000000]Erik1984[/COLOR]**]("http://ubuntuforums.org/member.php?u=1332877"),  this is whats inside the macinstall.jar. If you think its not gonna damage anything the way it is then I'll forget. If not how do I proceed? 

[http://postimg.org/image/egax13i83/](http://postimg.org/image/egax13i83/)

[IMG]http://postimg.org/image/egax13i83/[/IMG]

And this is inside macoinstaller.properties:

```
#frame.icon=${_iconName}
#frame.title=${_titleName}

linkassistant.fullname=LinkAssistant
linkassistant.description.text=Link building and partner management tool
linkassistant.isbundle=0
linkassistant.showondialog=1
linkassistant.installwithbundle=seopowersuite
linkassistant.url=http://www.link-assistant.com/linkassistant/
linkassistant.welcome.icon=commons/installer/LA_welcome.png
linkassistant.frame.icon=application/application.png
linkassistant.frame.title=${linkassistant.fullname} v${_installerVersion} Installation

ranktracker.fullname=Rank Tracker
ranktracker.description.text=Keyword research tool and search engines rankings checker
ranktracker.isbundle=0
ranktracker.showondialog=1
ranktracker.installwithbundle=seopowersuite
ranktracker.url=http://www.link-assistant.com/rank-tracker/
ranktracker.welcome.icon=commons/installer/RT_welcome.png
ranktracker.frame.icon=keypos/keypos32.png
ranktracker.frame.title=${ranktracker.fullname} v${_installerVersion} Installation

seospyglass.fullname=SEO SpyGlass
seospyglass.description.text=Backlink analyzer and competition research tool
seospyglass.isbundle=0
seospyglass.showondialog=1
seospyglass.installwithbundle=seopowersuite
seospyglass.url=http://www.link-assistant.com/seo-spyglass/
seospyglass.welcome.icon=commons/installer/SG_welcome.png
seospyglass.frame.icon=spyglass/spyglass32.png
seospyglass.frame.title=${seospyglass.fullname} v${_installerVersion} Installation

websiteauditor.fullname=WebSite Auditor
websiteauditor.description.text=Website content optimization tool
websiteauditor.isbundle=0
websiteauditor.showondialog=1
websiteauditor.installwithbundle=seopowersuite
websiteauditor.url=http://www.link-assistant.com/website-auditor/
websiteauditor.welcome.icon=commons/installer/WA_welcome.png
websiteauditor.frame.icon=websiteauditor/websiteauditor32.png
websiteauditor.frame.title=${websiteauditor.fullname} v${_installerVersion} Installation

buzzbundle.fullname=BuzzBundle
buzzbundle.description.text=Social media management tool
buzzbundle.isbundle=0
buzzbundle.showondialog=1
buzzbundle.installwithbundle=seopowersuite
buzzbundle.url=http://www.link-assistant.com/buzzbundle/
buzzbundle.welcome.icon=commons/installer/BB_welcome.png
buzzbundle.frame.icon=buzzbundle/buzzbundle32.png
buzzbundle.frame.title=${buzzbundle.fullname} v${_installerVersion} Installation

seopowersuite.fullname=SEO PowerSuite
seopowersuite.description.text=
seopowersuite.isbundle=1
seopowersuite.showondialog=0
seopowersuite.contains=linkassistant ranktracker seospyglass websiteauditor buzzbundle
seopowersuite.url=http://www.link-assistant.com/
seopowersuite.welcome.icon=commons/installer/SPS_welcome.png
seopowersuite.frame.icon=commons/installer/sps_application.png
seopowersuite.frame.title=${seopowersuite.fullname} Installation

wizardheader.start.header.text=Welcome to the ${_name} Setup Wizard
wizardheader.start.info.text=You are going to install ${_name}.\n\nPlease close all applications developed by Link-Assistant.Com before continuing: Rank Tracker, WebSite Auditor, SEO SpyGlass, LinkAssistant, and BuzzBundle. This will make it possible to update relevant system files without having to reboot your computer.

wizardheader.license.header=Step ${step}: End User License Agreement
wizardheader.license.info=Please review license terms before installing ${_applicationName}.
wizardheader.license.icon=commons/installer/${_name}_header.png

wizardheader.chooseapps.header=Step ${step}: Select Tools to Install
wizardheader.chooseapps.info=${_applicationName} is part of SEO PowerSuite - the complete suite of SEO software.
wizardheader.chooseapps.icon=commons/installer/${_name}_header.png
wizardheader.chooseapps.seopowersuite.header=Step ${step}: Select Tools to Install
wizardheader.chooseapps.seopowersuite.info=SEO PowerSuite is a software package made up of 4 applications.
wizardheader.chooseapps.seopowersuite.icon=commons/installer/${_name}_header.png
wizardheader.chooseapps.buzzbundle.header=Step ${step}: Select Tools to Install
wizardheader.chooseapps.buzzbundle.info=You can install other applications developed by Link-Assistant.Com\ntogether with ${_applicationName} if you like.
wizardheader.chooseapps.buzzbundle.icon=commons/installer/${_name}_header.png
chooseapps.info.label.text=You can also install other parts of the SEO toolkit and the BuzzBundle tool.
chooseapps.seopowersuite.info.label.text=Choose the apps to install. You can include BuzzBundle (another tool by Link-Assistant.Com) into the installation.
chooseapps.buzzbundle.info.label=You can also install other applications developed by Link-Assistant.Com.

wizardheader.progress.header=Step ${step}: Installing
wizardheader.progress.info=Please stand by while the software is being installed.
wizardheader.progress.icon=commons/installer/${_name}_header.png
wizardheader.progress.operationFailed.title=Installation cannot be completed
wizardheader.progress.operationFailed.text=It doesn't seem possible to install the software to the specified folder. Possible reasons:\n\n- Not enough free disk space.\n- Insufficient user permissions.\n- Presence of unsupported symbols in the name of the installation folder.\n\nPlease try one more time or contact support for assistance.

wizardheader.finish.header=Step ${step}: Completing Installation
wizardheader.finish.info=The installation is complete. Thanks for choosing ${_applicationName}.
wizardheader.finish.icon=commons/installer/${_name}_header.png

frame.installer.title=${_applicationName} Installation

dialog.finish.checkBox.text=Open the folder to get started
dialog.finish.infoLabelMac.text=Now you can find the software in Applications / Link-AssistantCom.
dialog.finish.infoLabelMac.buzzbundle.text=Now you can find the software in Applications / Link-AssistantCom.
dialog.finish.infoLabelLinux.text=To run the software, type the name of the corresponding tool in terminal (for Rank Tracker it will be 'ranktracker', for SEO SpyGlass 'seospyglass', for LinkAssistant 'linkassistant', for Website Auditor 'websiteauditor').
dialog.finish.infoLabelLinux.buzzbundle.text=To start BuzzBundle, type its name into your terminal emulator (lower-case symbols, no quotation marks): 'buzzbundle'.\n\nIf you've installed any of the SEO PowerSuite tools together with BuzzBundle, you can start them in the same way: 'ranktracker', 'websiteauditor', 'seospyglass' or 'linkassistant'.
dialog.progress.starting.text=Starting installation...
dialog.progress.installingapp.text=Installing ${_application}

applicationurl.url=${_applicationUrl}
applicationurl.text=${_applicationName} site
applicationurl.tooltip=Visit ${_applicationName} site for news and support

norights.message.title=No Root Privilege To Install
norights.message.text=You need root privileges to install this software.

runningApplications.message.title=You need to close some applications
runningApplications.message.text=To install the software correctly, you need to quit the following applications: ${_runApps}.

agree.button.text=Accept

license.text=END USER LICENSE AGREEMENT\n\
\n\
SEO PowerSuite, hereafter referred to as 'Software'. Link-Assistant.Com, hereafter referred to as 'Author'.\n\
\n\
1. This is a single-user copy of the Software and all modules must be used only on one computer. You may not copy the program and accompanying materials except for backup and archival purposes.\n\
\n\
2. For unregistered versions of the Software you are hereby granted a non-exclusive license to use the Software free of charge. \n\
\n\
3. You may distribute copies of the software provided it remains in its original distribution form and all files and notices remain intact.\n\
\n\
4. For registered versions of the Software you are hereby granted a non-exclusive, non-transferable license to use the Software. You may not sell, distribute or share any part of a registered copy. \n\
\n\
5. You may not rent, lease, or otherwise transfer rights to the Software. You may not make available either intentionally or otherwise your registration details to other persons.\n\
\n\
6. You may not modify, reverse engineer, disassemble or create derivative works based on the Software.\n\
\n\
7. This software is copyrighted, and all rights therein are reserved for the Author. Purchase of this product does not transfer any right, title, or interest in the software except as specifically set forth in this agreement. You are hereby notified that the software product is protected by applicable laws, and you may be held responsible by the Author for any infringement of such rights or violations to this agreement.\n\
\n\
8. This license is effective until terminated. You may terminate it at any time by destroying the program and all copies of it. It will also terminate if you fail to comply with any term or condition on this agreement. You agree upon termination to destroy the program together with all copies of the program.\n\
\n\
9. A paid license covers a free subscription to the Software Search algo updates within 6 months since the date of purchase. After this period expires, the Software Search algo updates is provided on a paid basis only.\n\
\n\
DISCLAIMER\n\
\n\
Some search engines have conditions for use, including references to running automated ranking tools, such as this one, without authorization from the Search Engine. For further information refer to search engines' documentation.\n\
\n\
The Author cannot and does not guarantee that any functions contained in the Software will meet your requirements, or that its operations will be error free.  The entire risk as to the Software performance or quality, or both, is solely with the user and not the Author.\n\
\n\
The Author's Current Return Policy is available at: [http://www.link-assistant.com/return-policy.html\n\](http://www.link-assistant.com/return-policy.html\n\)
\n\
By using the Software you agree to the terms and conditions of the Return Policy.\n\
\n\
The Author makes no warranty, either implied or expressed, including without limitation any warranty with respect to this Software documented here, its quality, performance, or fitness for a particular purpose. In no event shall the Author be liable to you for damages, whether direct or indirect, incidental, special, or consequential arising out of the use of or any defect in the Software, even if the Author has been advised of the possibility of such damages, or for any claim by any other party. \n\
\n\
All other warranties of any kind, either express or implied, including but not limited to the implied warranties of merchantability and fitness for a particular purpose, are expressly excluded.\n\
\n\
IMPORTANT NOTE: You have purchased one single-user copy of Software, which means you can ONLY run it on ONE computer AT A TIME. Please DO NOT run this software with the same Registration Key concurrently on multiple computers, or your key might be blocked.\n\
\n\
By using the Software you agree to be bound by the terms and conditions of this license.

buzzbundle.license.text=END USER LICENSE AGREEMENT\n\
\n\
BuzzBundle, hereafter referred to as 'Software'. Link-Assistant.Com, hereafter referred to as 'Author'.\n\
\n\
1. This is a single-user copy of the Software and must be used only on one computer. You may not copy the program and accompanying materials except for backup and archival purposes.\n\
\n\
2. For unregistered versions of the Software you are hereby granted a non-exclusive license to use the Software free of charge.\n\
\n\
3. You may distribute copies of the software provided it remains in its original distribution form and all files and notices remain intact.\n\
\n\
4. For registered versions of the Software you are hereby granted a non-exclusive, non-transferable license to use the Software. You may not sell, distribute or share any part of a registered copy.\n\
\n\
5. You may not rent, lease, or otherwise transfer rights to the Software. You may not make available either intentionally or otherwise your registration details to other persons.\n\
\n\
6. You may not modify, reverse engineer, disassemble or create derivative works based on the Software.\n\
\n\
7. This software is copyrighted, and all rights therein are reserved for the Author. Purchase of this product does not transfer any right, title, or interest in the software except as specifically set forth in this agreement. You are hereby notified that the software product is protected by applicable laws, and you may be held responsible by the Author for any infringement of such rights or violations to this agreement.\n\
\n\
8. This license is effective until terminated. You may terminate it at any time by destroying the program and all copies of it. It will also terminate if you fail to comply with any term or condition on this agreement. You agree upon termination to destroy the program together with all copies of the program.\n\
\n\
9. This license covers a free subscription to the Software Maintenance Updates within 6 months since the date of purchase. After this period expires, the Software Maintenance Updates are provided on a paid basis only.\n\
\n\
DISCLAIMER\n\
\n\
Some web services have conditions for use, including references to running scripts, such as this one, without authorization. For further information refer to their documentation.\n\
\n\
The Author cannot and does not guarantee that any functions contained in the Software will meet your requirements, or that its operations will be error free. The entire risk as to the Software performance or quality, or both, is solely with the user and not the Author.\n\
\n\
The Author's Current Return Policy is available at: [http://www.link-assistant.com/return-policy.html\n\](http://www.link-assistant.com/return-policy.html\n\)
\n\
By using the Software you agree to the terms and conditions of the Return Policy.\n\
\n\
The Author makes no warranty, either implied or expressed, including without limitation any warranty with respect to this Software documented here, its quality, performance, or fitness for a particular purpose. In no event shall the Author be liable to you for damages, whether direct or indirect, incidental, special, or consequential arising out of the use of or any defect in the Software, even if the Author has been advised of the possibility of such damages, or for any claim by any other party.\n\
\n\
All other warranties of any kind, either express or implied, including but not limited to the implied warranties of merchantability and fitness for a particular purpose, are expressly excluded.\n\
\n\
IMPORTANT NOTE: You have purchased one single-user copy of Software, which means you can ONLY run it on ONE computer AT A TIME. Please DO NOT run this software with the same Registration Key concurrently on multiple computers, or your key might be blocked.\n\
\n\
By using the Software you agree to be bound by the terms and conditions of this license.
```

---

### Post by Erik1984 on 2014-07-30
Did you run that instaler? Judging by the contents of the .jar file it's some graphical install wizard. Sadly I don't see any source files (Downloaded the tar.gz package myself) so I can't check where that installer copies the files to. But like I said before it's only disk space, it doesn't hurt your system that these programs are installed.

---

### Post by QIII on 2014-07-30
If it does bother you that it is there, then look in the installation directory and see if there is something like "uninstall.sh"

Also look at the targets of those symlinks (the icons with the arrows) by right clicking on them.  If those all point to your /home, then we can tell you how to delete the symlinks and just clean up your /home.

Given the way it was installed, you *won't *find it in the Software Center or Synaptic.

---

### Post by lobosuelto on 2014-07-30
OK I'll see if I can find it. And if I can't then I'll leave the god admn thing there as long as the only thing it takes is space

No uninstall in usr/local/bin ... I just wanna be sure that this is no freacking spyware or something

---

### Post by Erik1984 on 2014-07-30
You could see if you have the following directory:

```
/opt/link-assistantcom
```

on your system (that's the full path, /opt is on the same level as /usr).

I suspect that is where most of the installed files go.

---

### Post by lobosuelto on 2014-07-30
The symlics show:

#!/bin/bash

java -Duser.dir=/opt/link-assistantcom/seospyglass/resources/ \
     -Xms64m \
     -Xmx768m \
     -jar /opt/link-assistantcom/seospyglass/bin/seospyglass.jar

And thats it

---

### Post by lobosuelto on 2014-07-30
Yeah! Here they are: 

[http://postimg.org/image/ngo7bzyth/](http://postimg.org/image/ngo7bzyth/)

Now? (thaks)

---

### Post by lobosuelto on 2014-07-30
Should I just remove them?

---

### Post by lobosuelto on 2014-07-31
Anyone? :(

---

### Post by Erik1984 on 2014-07-31
You could do that if you like the HDD space back :P No but seriously if you don't need those programs anymore it's safe to remove those folders. /opt is for self installed software (outside the repositories). To be clear: I'm not saying to delete /opt itself only the folders inside it. It seems like all those folders in there (in your screenshot) belong to the linkassistant program.

---


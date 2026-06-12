---
title: "Removing unnecessary programs, or at least disabling them"
date: 2014-03-03
forum: General Help
---

### Post by bjngchn on 2014-03-03
I never use kmail and never plan to use it.  Can I safely remove it? I tried to remove it with sudo apt-get remove; and computer became unusable... What are alternatives to uninstalling to stop those programs? Like renaming or removing associated files, or chmodding them? How can I know which program uses, edits, reads which files?  When I click d to delete a file, I see a search function. Maybe it is dash program, which is called spyware by people on internet. I would certainly block this program if I knew how this could be done. ...... Another related thing is firefox. In about:config there are references to external sites like facebook, yahoo, google, , What is the point of this. Also there is reference to ubuntu. While editing those stuff not only firefox , but whole computer became unusable. I don't want any connection between unrelated programs, share data, send anything outside, either as crash report or anything else. ..These are not about me, these are general questions....Akonadi, nepomuk running many processes all the time. maybe they are just things that make computer work hard, get hot and noisy; and this also eat battery life. kwallet running al the time.

---

### Post by Tristan_Williams on 2014-03-03
Are you running Kubuntu or Ubuntu?

---

### Post by bjngchn on 2014-03-03
Kubuntu; but firefox config mentions ubuntu without k. Maybe there is an installation id of *ubuntu, and it is asociated to firefox through "preferences".  Btw some items in about:config are not changeable.   Unchangeable preferences. Still much  much better than  closedsource OSs.

---

### Post by 1clue on 2014-03-03
I haven't used KDE or Kubuntu for years, but yes you can remove end-user apps from your install.  I do that sort of thing all the time.  I don't know exactly how it all ties together, maybe the menu item won't go away but I'm guessing it probably will because new menu items appear when you install something.

You need to be careful, you need to look at the list of things that will ALSO be uninstalled.  If you remove a library or service which a lot of other things depend on, you could have a painful time fixing it all.  But something like kmail, you'll only lose kmail and maybe some sort of kmail-specific widgets or themes.

If you want to be complete about it, you can specify to completely remove it including configuration files.

If you do something like this and then change your mind, all you need to do is reinstall it.

---

### Post by monkeybrain20122 on 2014-03-03
Well in your other thread you talked about removing some kde application cleaned out half your system. So you should have learned to be careful. Yes, in general you can remove unused software but always pay attention to what else is removed along with it. For this you should use phonon instead of just "sudo apt-get remove xxx" and press "yes" because at least it prompts you several times before going ahead. 

With kde you have to be particularly careful because kde's design is not modular, so there are innocent looking things that are actually a part of KDE so they cannot be removed without breaking kde. For these you'd better leave them alone as they don't usually take up a lot of space.

---

### Post by buzzingrobot on 2014-03-03
A number of applications in the Ubuntu repos are compiled with Unity dependencies, as we ought to expect.  Those dependencies will be required if that app is running on Unity, KDE, Gnome, etc.

When removing packages, use apt-get or Synaptic and carefully consider the list of packages that will be removed in response to your command.  For large packages like KMail, which, in turn, is part of the large Kontact group, deleting it will likely result in the deletion of many packages essential to KDE's operation.

Unless you are running dramtically short of disk space, there no harm in letting unused packages sit on the drive.

---

### Post by oldos2er on 2014-03-03
I've removed kmail from Kubuntu in the past, I don't recall it harming anything, or removing anything other than the kmail package itself. I also disable the akonadi server because I don't use kontact or any similar software (see [http://userbase.kde.org/Akonadi#Disabling_the_Akonadi_subsystem](http://userbase.kde.org/Akonadi#Disabling_the_Akonadi_subsystem)). Nepomuk can be be disabled in System Settings.

---

### Post by buzzingrobot on 2014-03-04
Dunno if it was Kubuntu or elsewhere, but I've seen attempts to remove KMail try to remove the rest of KDE's PIM programs, MySQL, etc. Depends, I'm sure, in how the dependencies are set up.

Installing a group like kde-full or kubuntu-desktop does seem to have the counterintuitive effect of creating dependency links with previously installed packages, so trying to remove the newly installed KDE pacakges needs to done with care, if it all.

I've never really understood the impulse to delete unused packages when disk space is not an issue. Often seems more trouble that it's worth.

---

### Post by 1clue on 2014-03-04
So add mysql back if you need it.

The way the package manager works, you install the app you want and the package manager installs the dependencies if they're not already there.  It marks the main thing you installed as "wanted" and the rest is just there because something depends on it.

If Kmail needs mysql and nothing else does, then when you remove kmail there are some circumstances where mysql would go away too, but not if you explicitly install it.

---

### Post by speartip on 2014-03-04
On a clean install of kubuntu, the 1st thing I do is:
```
sudo apt-get remove --purge kontact kmail ktorrent rekonq
```
It doesn't compromise the rest of the system at all.

---

### Post by bjngchn on 2014-03-04
speartip, what exactly  does this command do?   I guess it removes kontact, kmail, ktorrent, rekonq without affecting other programs. If so can we also add more to the list, like akonadi, kopete, dash ,  kwallet, safely?

---

### Post by oldos2er on 2014-03-04
I wouldn't try to to remove dash (the default system shell) since that would most likely break your system: ```
sudo apt-get remove -s dash
[sudo] password for annk:        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bash bash-completion dash pipelight pipelight-multi
[COLOR=#ff0000]WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing![/COLOR]
  bash dash (due to bash)
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv pipelight [0.2.5~ubuntu13.10.1]
Remv pipelight-multi [0.2.5~ubuntu13.10.1]
Remv bash-completion [1:2.1-2ubuntu2]
Remv bash [4.3-1ubuntu2]
Remv dash [0.5.7-4ubuntu1]
```

---

### Post by buzzingrobot on 2014-03-04
> **bjngchn said:**
> speartip, what exactly  does this command do?   I guess it removes kontact, kmail, ktorrent, rekonq without affecting other programs. If so can we also add more to the list, like akonadi, kopete, dash ,  kwallet, safely?

This -- "sudo apt-get remove --purge kontact kmail ktorrent rekonq" removes those packages and their configuration files, which you may or may not have edited.

Leaving out the "--purge" removes the packages while leaving the configuration files intact.

Whether or not a package can be removed without triggering the removal of other packages depends on the chain of dependencies that have been created. Tools like apt-get and Synaptic will let you take a look at *all* the packages to be removed as a result of your command.  You should alway examine and pay attention to that list.

---

### Post by monkeybrain20122 on 2014-03-04
> **bjngchn said:**
> speartip, what exactly  does this command do?   I guess it removes kontact, kmail, ktorrent, rekonq without affecting other programs. If so can we also add more to the list, like akonadi, kopete, dash ,  kwallet, safely?

If you don't know what that command does, do yourself a favour and use the gui package manager that comes with kubuntu. It is called phonon and you can find it in the menu (probably called software add/remove or something like that) It is very good and intuitive to use. There are very few occasions that you actually have to deal with the command lines in *buntu.

Edited: sorry it should be muon rather than phonon (which is a sound thing)

---

### Post by speartip on 2014-03-05
> **bjngchn said:**
> speartip, what exactly  does this command do?   I guess it removes kontact, kmail, ktorrent, rekonq without affecting other programs. If so can we also add more to the list, like akonadi, kopete, dash ,  kwallet, safely?
You do need to be very careful what you remove. I suspect akonadi & kwallet are an integral part of the kde desktop.
All you can do is try removing things 1 by 1 in a terminal as in the command I gave above. Before accepting the command it will list what else will be removed, if it is a program that is bound up with kde it will tell you it needs to remove a lot of stuff, and so I would hit "N" & abort the command.
 Quite often though the program you want to remove is the only thing that is removed so you're fine.

---

### Post by 1clue on 2014-03-05
I use the command line for just about everything, but you should be able to remove it using synaptic as well.  The standard install is just a guess, there's nothing keeping you from doing your own thing.

---

### Post by monkeybrain20122 on 2014-03-05
> **1clue said:**
> I use the command line for just about everything, but you should be able to remove it using synaptic as well.  The standard install is just a guess, there's nothing keeping you from doing your own thing.

kubuntu comes with muon which is as good as synaptic so there is no need to install synaptic-kde.

---

### Post by 1clue on 2014-03-05
Whatever.  I was saying that you should be able to remove "standard" packages which were included in the base distro using a GUI package manager.  There's nothing holy about the selection of end-user tools.

---

### Post by bjngchn on 2014-03-13
Reinstalled Kubuntu 13.10. After speartips's command:             sudo apt-get remove --purge kontact kmail ktorrent rekonq  ;  I can't login normally (graphically) anymore.  Also there is an error after typing encryption pw: The disk drive for /dev/mapper/kubuntu--vg-swap_1 is not ready yet or not present. Continue to wait, Press S to skip mounting, or M for manual  recovery. And in either case, nothing happens, but computer gets noisy and hot (btw it is a new computer). I guess kmail can't be removed without screwing the whole installation.

---

### Post by monkeybrain20122 on 2014-03-13
Why don't you just keep those programs if removing them give you troubles? It is not like they take up a lot of space like Windows program would. I would just leave them alone.

---

### Post by nothingspecial on 2014-03-13
The thing with Kubuntu, Ubuntu and most other major distros is that they use a range of packages that give you a complete desktop environment (DE) including a browser, text editor  , email client, Facebook thing etc
Consider installing minimal Ubuntu and then adding what you want because removing core stuff from a DE can mess it up.

---

### Post by hebrewofyhwh on 2014-03-13
I wouldn't feel confident at this stage to remove any programs, speaking for myself.

---

### Post by 1clue on 2014-03-13
You should be able to get it all back by typing **apt-get install kubuntu-desktop**.  But in any case I'd remove one thing at a time to make sure you don't break something.  I do this  sort of thing all the time, but I don't use kubuntu so I can't help with the details.

---

### Post by 1clue on 2014-03-13
Frankly I always start with server or minimal and add on what I want.

---

### Post by speartip on 2014-03-14
@bjngchn..

The command ```
sudo apt-get remove --purge rekonq kmail ktorrent kontact
``` removes 19 files, NONE of which are system files.
I have just done it again on a fresh install of 13.10, & everything is fine, including login. I have been doing this since 9.10, without ever having an issue.
Something else must have borked your system.

As has been mentioned you can always drop down to a terminal, CTRL + ALT + F2, & just reinstall, what you purged. But I doubt this is your problem.
It would be interesting if you could let us know though.

---

### Post by bjngchn on 2014-03-14
Many new questions arise. Is kubuntu-desktop a very big pack? (I don't want anything very heavy, which takes up space, which will never be used, which can't be disabled, which runs out of control and consumes battery and makes noise/heat, and worse do some spying. ) .................Second question: Is Ubuntu as easy to use as Kubuntu, for a naive user? Is it even lighter than Lubuntu? (Btw lubuntu iso file is as big as kubuntu iso file). Can we start with Ubuntu , and reach kubuntu just by adding more stuff? ................Third question is there a difference between CTRL+ALT+F1 and CTRL+ALT+F2 ? Previously, when I removed kmail (and then whole thing was screwed), reinstalling kmail didn't fix things. This is a great command, if it works. it didn't work this time. Others say, use package managers. Same thing may happen with package managers also, who knows.

---

### Post by monkeybrain20122 on 2014-03-14
Why is it that you so want to remove stuffs? They don't take up too much space, they are not like typical Windows software. As said before, KDE is not modular by design and it is more difficult to remove stuffs than other DES.

---

### Post by buzzingrobot on 2014-03-14
> **bjngchn said:**
> Many new questions arise. Is kubuntu-desktop a very big pack? (I don't want anything very heavy, which takes up space, which will never be used, which can't be disabled, which runs out of control and consumes battery and makes noise/heat, and worse do some spying. )

Installing the kubuntu-desktop on Ubuntu Unity installs what it says:  the Kubuntu KDE desktop on a machine that already has Ubuntu Unity on it.  

It is safe to say KDE does not have a reputation as a 'light" desktop environment. But, that means different things to different people because there is no accepted definition of "light'.

You  can also install "kde-full" on Ubuntu, which installs the entire KDE suite, and that include dozens of programs. Whether you use them or not, of course, depends on you.

No reason exists to *disable* programs that do not execute unless you want to free up some disk space. In fact, it is impossible. A program cannot be *disabled* unless it is first *enabled*, i.e., launched and executed.  Certain services and startup applications are executed at startup and they can, of course, be disabled -- kept from executing at system startup -- *if* you know what you are doing and *if* you know which are not essential to the operation of your system. 

Nothing can run "out of control" unless it is launched, typically by you, the user.  If something runs "out of control" (whatever that means:  Can't be halted?  Consumes ever-increasing amounts of memory?) the solution is to avoid launching it again and to report a bug.

Kubuntu does not include the optional function to forward local searches to online entities, like Amazon, that are in Ubuntu. Nor does it include any of the scopes and lenses Unity offers for searching.  Kubuntu does include the optional KDE functions to index your local data and store that index in a searchable local database. This provides the full-coverage desktop search that many people want.

Battery usage and heat management in Linux, in general, are often not as good as in Windows due to the reluctance of vendors to release their source code and otherwise cooperate.



>  Is Ubuntu as easy to use as Kubuntu, for a naive user? 

Depends on the user.  Ubuntu relies heavily on a search mechanism and a dock. KDE relies on a complex menu and panels. Nothing is easy -- or can be easy -- if the user has not idea what to do.


> Is it even lighter than Lubuntu? (Btw lubuntu iso file is as big as kubuntu iso file). 

Lubuntu has a reputation for being lighter.  That seems to mean that the Lubuntu system, once loaded and with no applications loaded, requires somewhat less RAM than Ubuntu.  Of course, an OS is pretty useless unless you load applications, and the memory use of those applications will be essentially constant whether they run on Lubuntu, Ubuntu, Kubuntu, etc.

> Can we start with Ubuntu , and reach kubun system is easy -- or can be easy -- if the user has not idea what to do.

It's easy to do, if you take the time to research how to do it.  It's done the same way any other package is installed, except that packages like kubuntu-desktop and kde-full are pseudo packages that represent the hundreds of KDE packages that would otherwise need to be installed individually.

Nothing is easy to do if you have no idea how to do it.

> ...is there a difference between CTRL+ALT+F1 and CTRL+ALT+F2 ? Previously, when I removed kmail (and then whle thing was screwed), reinstalling kmail didn't fix things. This is a great command, if it works. it didn't work this time. Others say, use package managers. Same thing may happen with package managers also, who knows.

One opens a full-screen terminal session.  The other opens another full-screen terminal session.  Ditto CTRL+ALT+F3, etc.

Executing CTRL+ALT+F1, etc., would *not* do anything unless you executed a command in one of them.  

Large programs like KMail are not single files, but comprise dozens or even hundreds of files that are installed, including many support files required by the program (the "dependencies").  It is not uncommon to find that removing a large complex package like KMail will also remove many of its dependencies that will not be re-installed simply by re-installing KMail.

Bottom line:  Programs that are not executed do nothing except take up a bit of space on your drives. Removing them is often more trouble that it is worth:  Much to lose and nothing at all to gain.

---

### Post by bjngchn on 2014-03-14
Still one may want to remove programs for various reasons: old computer, needing more space. Another reason: I would prefer to disable, not only turn off, say, bluetooth. If I don't disable it, maybe it will run outside user control  and need to be disabled everytime. if bluetooth runs all the time, it creates radiation. Maybe it is not running officially, but it is ready to work and still emitting radiation. ..... There is something called online presence. If this makes sense, some info need to be sent to a fixed location all the time... How can I know, if running program A, requires running program B also  (and there is an excuse for it). .... Main answer I needed was, whether kubuntu-desktop was big. I will try this one. ..kde-full was the big one which I would avoid (something in GB range).

---

### Post by buzzingrobot on 2014-03-14
> **bjngchn said:**
> Still one may want to remove programs for various reasons: old computer, needing more space. Another reason: I would prefer to disable, not only turn off, say, bluetooth. If I don't disable it, maybe it will run outside user control  and need to be disabled everytime. if bluetooth runs all the time, it creates radiation. Maybe it is not running officially, but it is ready to work and still emitting radiation. ..... There is something called online presence. If this makes sense, some info need to be sent to a fixed location all the time... How can I know, if running program A, requires running program B also  (and there is an excuse for it). .... Main answer I needed was, whether kubuntu-desktop was big. I will try this one. ..kde-full was the big one which I would avoid (something in GB range).

There is no bluetooth application.  There is a bluetooth service that can be disabled.  Investigate Upstart  -- used by 
Ubuntu to launch and control system services -- to see how to disable services.  Bluetooth is also hardware in your machine.  If your machine allows it, you can turn off that hardware.

Synaptic and apt-get list a package's dependencies before you commit to installing them. Software Center does not.

---

### Post by bjngchn on 2014-03-15
No fix with any command, so installed k13.10 again.  When I type speartip's command: sudo apt-get remove --purge rekonq kmail ktorrent kontact  I get a very long list (not just 19 files), and I still want to remove all this junk: ................................  ```
$ sudo apt-get remove --purge rekonq kmail ktorrent kontact 
Reading package lists...Done
 Building dependency tree  Reading state information...Done
 The following extra packages will be installed:  
 kate-data katepart kde-runtime-data kdelibs-bin kdelibs5-data   kdepimlibs-kio-plugins kdoctools libakonadi-calendar4 libakonadi-contact4   libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4   libakonadi-socialutils4 libgpgme++2 libkabc4 libkalarmcal2   libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4   libkcmutils4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5   libkdgantt2-0 libkdnssd4 libkemoticons4 libkfile4 libkholidays4 libkhtml5   libkidletime4 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkleo4   libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4   libknewstuff3-4 libknotifyconfig4 libkntlm4 libkontactinterface4 libkparts4   libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4   libkpty4 libkresources4 libkrosscore4 libkrossui4 libksieve4   libktexteditor4 libktnef4 libkunitconversion4 libkxmlrpcclient4   libmailtransport4 libmicroblog4 libnepomuk4 libnepomukquery4a   libnepomukutils4 libplasma3 libplasmaclock4abi4 libqgpgme1   libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core   libreoffice-draw libreoffice-impress libreoffice-math libreoffice-writer   libsolid4 libsyndication4 libthreadweaver4 plasma-dataengines-addons   policykit-1-gnome python-apport python-keyring python-launchpadlib   python-lazr.restfulclient python-lazr.uri python-oauth   python-problem-report python-simplejson python-wadllib python3-apport   python3-distupgrade python3-uno ubuntu-release-upgrader-core   usb-creator-common xterm Suggested packages:   hspell libreoffice-base libreoffice-style-crystal   libreoffice-style-hicontrast libreoffice-style-human   libreoffice-style-tango libreoffice-gcj libreoffice-java-common default-jre   gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre sun-java6-jre   java5-runtime jre gir1.2-gnomekeyring-1.0 python-gdata python-keyczar   python-testresources python3-launchpadlib xfonts-cyrillic Recommended packages:   python-secretstorage libjs-jquery 
The following packages will be REMOVED:  
 akregator* amarok* amarok-utils* apport-kde* apturl-kde* ark* audiocd-kio*   bluedevil* colord-kde* dolphin* dragonplayer* gstreamer0.10-qapt* gwenview*   jockey-kde* k3b* k3b-i18n* kaccessible* kaddressbook* kamoso* kate* kcalc*   kde-baseapps-bin* kde-config-pimactivity* kde-config-telepathy-accounts*   kde-config-touchpad* kde-runtime* kde-style-oxygen* kde-telepathy*   kde-telepathy-auth-handler* kde-telepathy-contact-list*   kde-telepathy-desktop-applets* kde-telepathy-filetransfer-handler*   kde-telepathy-integration-module* kde-telepathy-minimal*   kde-telepathy-send-file* kde-telepathy-text-ui* kde-window-manager*   kde-window-manager-common* kde-workspace* kde-workspace-bin*   kdelibs5-plugins* kdemultimedia-kio-plugins* kdepasswd* kdepim-kresources*   kdepim-runtime* kdesudo* kexi* khelpcenter4* kinfocenter* kio-audiocd*   klipper* kmag* kmail* kmenuedit* kmix* kmousetool* knotes* konsole*   kontact* korganizer* kpat* kppp* krdc* krita* kscreen* ksnapshot*   ksysguard* ksystemlog* ktorrent* kubuntu-debug-installer* kubuntu-desktop*   kubuntu-firefox-installer* kubuntu-notification-helper* kwalletmanager*   language-pack-kde-en* libcalendarsupport4* libeventviews4*   libincidenceeditorsng4* libk3b6* libkateinterfaces4* libkde3support4*   libkdepim4* libkdepimdbusinterfaces4* libkfbapi1* libkgapi2-2* libkolab0*   libksieveui4* libktpcommoninternalsprivate5* libmailcommon4*   libmailimporter4* libmessagecomposer4* libmessagecore4* libmessagelist4*   libmessageviewer4* libmuonprivate1* libpimactivity4* libpimcommon4*   libqapt2-runtime* libreoffice-kde* libtemplateparser4* lightdm-kde-greeter*   muon* muon-discover* muon-notifier* muon-updater* okular* partitionmanager*   plasma-dataengines-workspace* plasma-desktop* plasma-netbook* plasma-nm*   plasma-scriptengine-python* plasma-widget-facebook* plasma-widget-homerun*   plasma-widgets-addons* plasma-widgets-workspace* polkit-kde-1*   print-manager* python-kde4* python3-pykde4* qapt-batch* qapt-deb-installer*   quassel* rekonq* skanlite* software-properties-kde* systemsettings*   ubuntu-release-upgrader-qt* usb-creator-kde* The following NEW packages will be installed:   policykit-1-gnome python-apport python-keyring python-launchpadlib   python-lazr.restfulclient python-lazr.uri python-oauth   python-problem-report python-simplejson python-wadllib xterm The following packages will be upgraded:   kate-data katepart kde-runtime-data kdelibs-bin kdelibs5-data   kdepimlibs-kio-plugins kdoctools libakonadi-calendar4 libakonadi-contact4   libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4   libakonadi-socialutils4 libgpgme++2 libkabc4 libkalarmcal2   libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4   libkcmutils4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5   libkdgantt2-0 libkdnssd4 libkemoticons4 libkfile4 libkholidays4 libkhtml5   libkidletime4 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkleo4   libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4   libknewstuff3-4 libknotifyconfig4 libkntlm4 libkontactinterface4 libkparts4   libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4   libkpty4 libkresources4 libkrosscore4 libkrossui4 libksieve4   libktexteditor4 libktnef4 libkunitconversion4 libkxmlrpcclient4   libmailtransport4 libmicroblog4 libnepomuk4 libnepomukquery4a   libnepomukutils4 libplasma3 libplasmaclock4abi4 libqgpgme1   libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core   libreoffice-draw libreoffice-impress libreoffice-math libreoffice-writer   libsolid4 libsyndication4 libthreadweaver4 plasma-dataengines-addons   python3-apport python3-distupgrade python3-uno ubuntu-release-upgrader-core   usb-creator-common 
90 upgraded, 11 newly installed, 129 to remove and 217 not upgraded. Need to get 101 MB of archives. After this operation, 318 MB disk space will be freed. Do you want to continue [Y/n]? n    Abort.
```

---

### Post by buzzingrobot on 2014-03-15
> **bjngchn said:**
> No fix with any command, so installed k13.10 again.  When I type speartip's command: sudo apt-get remove --purge rekonq kmail ktorrent kontact  I get a very long list (not just 19 files), and I still want to remove all this junk: 

It isn't "junk".  It's all the packages that are dependencies of rekonq, kmail, ktorrent, kontact, and all of the dependencies of those dependent packages, and on and on until the dependency chain ends.  

You are asking the system to remove packages, three of which are very large collections with a considerable number of dependencies. Therefore, it is doing what it is supposed to do: remove those packages and their dependencies.

---

### Post by speartip on 2014-03-15
As Buzzingrobot says, is seems that nearly the whole KDE Desktop is being removed in your case, & would render your system useless.
Very strange that after a clean install on your system it wants to remove so much stuff. Yet on a clean install on my system I have no such problem.
I have no idea what may be causing the difference. Maybe someone else can chime in.

---

### Post by bjngchn on 2014-03-15
Ok, then how do I remove kmail, telepathy, akkregator, kontact, bluedevil, etc, without removing dependencies? Speartip's command is not just just remove command, it contains something else, which I don't understand. Bluedevil-helper was running although I never requested anything related to it...Even if I can't remove them, I should be able to disable them... So basically I want to get rid of application part, without touching library part. I guess library part is what is shared between essential and junk programs.

---

### Post by buzzingrobot on 2014-03-15
If this was after an install of kubuntu-desktop, then I have to say I've seen similar behavior after using similar very large pseudo-package installs of KDE.  

The "--purge" is an option to remove the configuration files -- files possibly altered by a user.

if you want such precise control, it is probably only attainable by installing a minimal system and then adding only what you want, piece by piece.  Even there, however, many dependencies will be brought in.  E.g., Kontact is a large suite of programs, libraries, etc.  If you install one application in that suite, you will very likely get all of Kontact.

Finer control is probably possible by building the packages you need.

If the system detects hardware in your machine, including Bluetooth chips, it will do its best to install and configure the software needed to support it.  This is universally seen as a welcome convenience.

---

### Post by speartip on 2014-03-15
You could just try removing the programs one at a time, & see if it is any specific program that is attempting to remove the whole KDE Desktop. Other than suggest that I can't really help as I do not see the same problem as you have, on my system.

---

### Post by buzzingrobot on 2014-03-15
I suspect the list of packages shown represents the contents of kubuntu-desktop.  A meta-package like that contains no actual packages, but is created to require -- be dependent on -- a collection of packages.  Those packages will be marked as automatically installed. Trying to remove a component of kubuntu-desktop will prompt the removal of all the packages that comprise that metapackage because, in this instance, the metapackage depends on the component.

---

### Post by daniroma on 2014-05-14
Just remove them from menu list. Will do no harm if they remain on hdd.

---

### Post by WogBoy on 2014-05-14
When I first tried Kubuntu I played around with getting rid of stuff that " I would never use" all it did was to make my PC crash and stuff not work. 
As I now say " If it aitnt broke, Dont fix it"

---


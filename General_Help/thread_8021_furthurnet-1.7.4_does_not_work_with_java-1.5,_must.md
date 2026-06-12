---
title: "furthurnet-1.7.4 does not work with java-1.5, must install 1.4.2"
date: 2004-12-13
forum: General Help
---

### Post by howiemoe on 2004-12-13
The problems furthurnet was having was with sharing files.  It had problems verifying md5 checksums.  The files were downloaded, but it would hang up at 97% and even go back and redownload parts of the concert files
  It looked visably messed up.  The colors did not work right and it did not looked as polished as in the past.  But java 1.4.2_06, works great for it.  I have it alongside java 1.5. It doesn't seem to create any conflicts having them both
 
 If you happen to be using or wish to use Furthurnet.org's furthurnet version 1.7.4 and have been having problems with it, then you will want to get a hold of the older version of java. In hoary, Java 1.5 makes furthur go on the fritz.  In warty I had to reinstall java as well, so here is a possible fix for both warty and hoary users:

   I installed it from the sun site, because the java.com site automagically detects 1.5 and won't allow downloads, but sun.com does. Just go to [COLOR=Sienna]http://java.sun.com/j2se/1.4.2/download.html and follow the 'Download J2se' link.[/COLOR]

   After you have installed it per instructions on the site, you than have to edit the file[COLOR=Blue] /usr/local/bin/furthur[/COLOR].  Here is a copy of mine with the path where I installed the old java:

[COLOR=Teal]#!/bin/sh
/usr/java/j2re1.4.2_06/bin/java -Dfurthur.syscfgdir=/usr/local/share/furthur -jar /usr/local/bin/Furthur.jar[/COLOR]     

Open furthurnet per yer usual method and enjoy the great music.  
jeff   
 :-({|=

---

### Post by tlepes on 2005-05-22
Looks like the Furthur Network folks have addressed this with an upgrade to Furthur.   Just in case some reading here were not aware, Furthur 1.7.5 is released and seems to work fine.  I have not noticed any problems, and am using...

```
$ java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)
```

Here is more info from the website ([www.furthurnet.org)](www.furthurnet.org)), with emphasis added:

> 04-16-2005: Furthur v. 1.7.5 Released!
After a lot of hard work and some dumb luck, the FurthurNet Development Team is pleased to announce Furthur v. 1.7.5.

Special thanks go to our crack coding team, Jonco, Acidrain, Vdoma, Skryking and the usual cast of mental patients, chat admins, and beta testers.

Major Issues Addressed Since Version 1.7.4

- Added an installation wizard to help first time users

- Added font and color selection and other enhancements to chat, and fixed several display bugs

**- Fixed several bugs that prevented filesets from completing/sharing when the user upgrades to JRE 1.5**

- Changed the way that Furthur reports band-name only search results -- it will now report all active shares that match the search, even if the user hosting the files has no open slots (i.e., the download will not start immediately)

- Improved the connection/disconnection code so that users won't appear as "ghosts," or be added incorrectly to the "peak uploaders" column as often

- Fixed a bug that prevented Furthur from automatically reconnecting to the network if the users' Internet connection went dead

- Revamped the help dialogs and error messages, added tooltips, and generally make the user interface more helpful

- Re-arranged the preferences panel and added code to automatically find flac and metaflac, or to prompt the user to download the flac binaries, and added a check to prevent selecting FlacFrontend by mistake

- Added column headings and other labels for using the client's features

- Fixed the installer for Solaris users

- Moved OS X menus to the client instead of on the system menu bar due to bugs with Apple's JRE that will hopefully be corrected by the next release

So, you want to know where to get it?
[http://www.furthurnet.org/downloadarea](http://www.furthurnet.org/downloadarea)


---

### Post by revgrndave on 2005-11-17
i can not even get furthur up on my system.
i executed a partition, no problem. everything is hunkey dorey even. BUT i do not know where to put java, or furthur, and am sofa king lost... :confused:

UPDATE
i have everything installed yet can not get it to load up...

---


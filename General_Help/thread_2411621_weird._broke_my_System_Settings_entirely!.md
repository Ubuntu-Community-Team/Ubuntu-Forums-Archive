---
title: "weird. broke my System Settings entirely!"
date: 2019-02-01
forum: General Help
---

### Post by shyspook on 2019-02-01
Hey friends
Something Horrible happened! An hour ago I used Bleach program and deleted something essential. Now I cannot use System Settings - there are actually no System Settings. I even cannot switch the general language from Lithuanian to English to give you the screenshots. I tried to run " unity-control-center" command and then " sudo apt-get -f install" - to no avail. Reads errors

---

### Post by deadflowr on 2019-02-01
Ubuntu version, please. 
Also is it unity or gnome for the desktop?

What are the Read Errors?
Can you post a sample?

---

### Post by shyspook on 2019-02-01
Thanks. Whatever I put in terminal it reads: Unsatisfied dependencies. Try performing 'apt-get -f install' without the specified packages
when I type  'apt-get -f install, it tells:  klaida, apdorojant paket&#261; python2.7-minimal (--configure): vidinis procesas installed post-installation script nutr&#363;ko gražindamas reikšm&#281; 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
And my translation: error processing python2.7-minimal (--configure):
  internal process installed post-installation script no longer gets back mode 1

Ubuntu version 14.04

Sorry, I am i panic. In 5 minutes i shall concentrate somehow

Well, if I type "sudo apt-get update" it starts but in the end it tells:
 ```
W: GPG error: [http://archive.trisquel.info](http://archive.trisquel.info) toutatis-updates InRelease: These signatures could not be verified because there is no public key: NO_PUBKEY B4EFB9F38D8AEBF1
```

then I run: sudo apt-get install synaptic
It gives:
```
 Reading package lists ... CompletedConstructing an addictive tree
Reading status information ... Completed
You may want to run 'apt-get -f install' to fix errors:
These packages have no dependencies installed:
  python: It belongs to: python-minimal (= 2.7.5-5ubuntu3) but it will not be installed
E: Unsatisfied dependencies. Try performing 'apt-get -f install' without the specified packages (or specify a solution)
```

then I try: apt-get -f install

And it gives:

 ```
Linking and byte-compiling packages for runtime python2.7 ...
python or pycompile not found in public_modules.rtinstall hook.
dpkg: Error processing python2.7-minimal (--configure):
  internal process installed post-installation script interrupted to return value 1
Errors occurred while processing:
  python2.7-minimal
E: Sub-process / usr / bin / dpkg returned an error code (1)
```

Thanks for editions, I must add that all those sentences may contain orthographic and lexical errors, since it is  my bad translation from Lithuanian ( I can't switch settings to English due to all above mentioned disasters) Sorry!

---

### Post by deadflowr on 2019-02-01
See if this helps fix the language issue first as that will help push it along:
[https://help.ubuntu.com/community/Locale]("https://help.ubuntu.com/community/Locale")

Also is this really trisquel?

---

### Post by shyspook on 2019-02-01
I have not a slightest idea about "trisquel" and what it has to do with me. I think it is a sort of glitch here
I can use also Russian and English  - they still are in the system, but now this System can speak with me only in Lithuanian, I don't know how to help that

May be there is a way to "go back in time" with the system? In windows it was easy, but here it is suggested to add some new packets to restore to the previous state



It seems I fix the problem with the "trisquel"
the problem with Python stays:
 Apdorojant &#303;vyko klaid&#371;: (processing has been done with errors) python2.7-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Impavidus on 2019-02-02
You're not the first to break your system using bleechbit. I never used it myself, but there are many advanced users who do. Also, there's no way to go back in time, unless you made a full system backup. I don't backup my system, only my documents.

The damage seems to be quite extensive. I think python2.7-minimal is vital to Ubuntu 14.04, as important parts of the system rely on it. The latest versions of Ubuntu have largely moved to python 3. Furthermore, Ubuntu 14.04 only has 2 months of support left. Within 2 months, you should upgrade to or freshly install a more recent release. So my suggestion is more radical: just make a backup of your documents and do a fresh install of Ubuntu 18.04 LTS now. It will fix all problems and allow you to skip 16.04, getting you directly on the latest LTS release.

---

### Post by shyspook on 2019-02-02
thanks, has reason

---


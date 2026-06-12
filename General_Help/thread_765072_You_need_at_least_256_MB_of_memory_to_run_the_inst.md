---
title: "You need at least 256 MB of memory to run the installation program!"
date: 2008-04-24
forum: General Help
---

### Post by Christian Johansson on 2008-04-24
I downloaded the Wubi installer by clicking on "Try Wubi Now" on the bottom of the page [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) . When I then ran the installer, I got the following error (translated from Swedish):

"You need at least 256 MB of memory to run the installation program!"

I find that strange because my computer has 256 MB of RAM.

---

### Post by ago on 2008-04-24
Sometimes the memory reported is actually less than what it says on the tin

anyway: [https://wiki.ubuntu.com/WubiGuide#head-3b62d195ae4508cbc9cda21f715c530637901377](https://wiki.ubuntu.com/WubiGuide#head-3b62d195ae4508cbc9cda21f715c530637901377)

---

### Post by CvRudo on 2008-04-24
Hi, i'm new user and i tried to install ubuntu from wubi, but i have the same message, and i looked the page and says "Yes start Wubi with the argument "--skipmemorycheck". The installer may not work in such conditions." How can i do that?? i dont understand "the argument" or how can i start that, and my other question is if i use wubi with less than 256 ram, the install will be ok or  will i have problems?? i have 224 ram because i have a internal video card.
Grettings

P.D: Sorry for my english :)

---

### Post by CvRudo on 2008-04-24
Sorry but i forgot something, if i can¡t install from wubi, Is another options to install ubuntu like wubi does it? or without cd??

---

### Post by ago on 2008-04-24
Open a dos box, go into the folder that contains wubi.exe and run:

wubi.exe --skipmemorycheck

---

### Post by Christian Johansson on 2008-04-25
> **ago said:**
> Open a dos box, go into the folder that contains wubi.exe and run:

wubi.exe --skipmemorycheck

I did that and then it worked for me to install Xubuntu using Wubi :) . I have only tested my Wubi installation of Xubuntu for a few minutes but so far I've noticed three things:

* In the log-in box, "Swedish (Finland)" is an alternative but not "Swedish (Sweden)", which is what I would like to select.

* The clock is one hour too fast. This problem remains after having started Windows (just changed it back one hour in Windows).

* Now and then, the computer makes a "beep" sound (not through the loudspeaker but the computer itself). That would indicate that something is wrong I think.

Since the questions above are not really Wubi specific questions I think, I should probably ask them in another forum.

---

### Post by Christian Johansson on 2008-04-25
Hmmm, I wonder if bullet 1 and 2 that I wrote might be related. In Finland they are actually one hour ahead of us. Maybe it was incorrectly detected that I'm i Finland instead of in Sweden during the installation of Xubuntu.

---

### Post by ago on 2008-04-25
please post the wubi log in your windows user temp folder (%temp%)

---

### Post by dmyre on 2008-04-26
> **ago said:**
> please post the wubi log in your windows user temp folder (%temp%)

============ Installer ============
PLUGINSDIR=C:\DOCUME~1\Daniel\LOCALS~1\Temp\nsr8.tmp
detect_all
Parsing cmdline "C:\Documents and Settings\Daniel\Local Settings\Temporary Internet Files\Content.IE5\CA8IE1FW\Wubi-8.04[1].exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=255 MB
Not enough memory, quitting
You need at least 256MB of memory to run the installer!

As you can See! This test is just below the minimum limit...

---

### Post by Christian Johansson on 2008-04-26
I looked in my wubi log as well and it does actually believe that I'm in Finland instead of in Sweden. In the log file I can find:

GMT=2
Country=EG
Locale=sv_FI.UTF-8

It should be the following I think:

GMT=1
Country=EG
Locale=sv_SE.UTF-8

---

### Post by ago on 2008-04-26
dmyre open a dos box go to the wubi directory and run

wubi.exe --skipmemorycheck

Christian Johansson, obviously the issue is that your country was detected as EG (Egypt). Can you check your windows settings? That is read from registry.

---

### Post by Christian Johansson on 2008-04-26
Aha, EG means Egypt. I incorrectly believed it meant the European Union (the old acronym for that in Swedish was EG).

---

### Post by ago on 2008-04-26
If you have egypt in windows then the wubi behaviour is correct

---

### Post by Christian Johansson on 2008-04-27
> **ago said:**
> If you have egypt in windows then the wubi behaviour is correct

I certainly shouldn't have Egypt as country in Windows. I should have Sweden. I'm not sure exactly where to check the country.

---

### Post by ago on 2008-04-27
The relevant registry key is: HKCU\Control Panel\International 
Use regedit to look for it

---

### Post by Christian Johansson on 2008-04-27
Just looked in the registry. The country is set to Sweden there (sCountry = Sverige, iCountry = 46) so I don't think Wubi should have detected it as Egypt.

(However, this is not a big problem for me since I have manually in Xubuntu after the installation changed time zone and default language so that they are correct.)

---

### Post by ago on 2008-04-27
I see, I was expecting "Sweden"... The fallback uses the GMT which happens to be Egypt.

---

### Post by ago on 2008-04-27
[https://bugs.launchpad.net/wubi/+bug/223250](https://bugs.launchpad.net/wubi/+bug/223250)

---

### Post by Christian Johansson on 2008-04-28
Ok, thank you for filing a bug report.

---

### Post by ago on 2008-04-28
I have transformed the 256 MB error into a warning and fixed the country issue.
Please test [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev503.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev503.exe)

---

### Post by Christian Johansson on 2008-04-29
Thank you. I have already installed Xubuntu with Wubi at the moment but if I'm going to do a new installation, I will try the newest Wubi beta version where these issues are fixed :) .

---

### Post by TheDeboMan on 2008-05-10
> **ago said:**
> Open a dos box, go into the folder that contains wubi.exe and run:

wubi.exe --skipmemorycheck


Hmm, can someone tell me how to do this? I'm sort of confused on how to do that.

I'm actually trying to install Xubuntu, which says it only needs 192 mb ram to run the installer, but I keep getting the "You need at least 256 MB of memory to run the installation program!" message. Any help would be great, and if you could keep it simple that'd be great as this is my first time installing Linux.

---

### Post by Midwest-Linux on 2008-05-10
> **TheDeboMan said:**
> Hmm, can someone tell me how to do this? I'm sort of confused on how to do that.

I'm actually trying to install Xubuntu, which says it only needs 192 mb ram to run the installer, but I keep getting the "You need at least 256 MB of memory to run the installation program!" message. Any help would be great, and if you could keep it simple that'd be great as this is my first time installing Linux.

 I would bypass Wubi altogether. Go with the ALTERNATE Xubuntu and install yourself on your computer, but if you are uncomfortable with partitioning or installing directly. Then I would guess getting more RAM would be another option.

[http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso)

[http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso.torrent](http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso.torrent)

---


---
title: "opera flash"
date: 2008-04-04
forum: General Help
---

### Post by philmetz on 2008-04-04
basically its not working.
I installed flashplugin-nonfree
then went to the folder and theres no files there??
so i can copy flashplayer.so to the opera plugin folder,

Any ideas?

---

### Post by twright on 2008-04-04
if you go to adobe's website and download the plugin in .tar.gz format the plugin is in there and you can put it in the opera plugins folder

---

### Post by philmetz on 2008-04-04
since opera is in my root how to i copy it there?

---

### Post by SEMW on 2008-04-04
The fact that it's not in the opera plugins folder is irrelevent: Opera by default checks several folders, including Firefox's plugin folder, for plugins; anything in any of those folders will work.  And the package installs it into Firefox's plugins folder.  You can check this by going to [opera<colon>plugins]("opera:plugins"), you'll see the plugin there.

The reason that it still doesn't work (shows a grey box for all flash applets) is that apparently flashplugin-nonfree 9.0.115 doesn't work with Opera 9.24 or 9.25!

The easiest solution is to download the previous version of flash from [http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1"); the only problem being that the package you get from there contains pretty much all the versions of flash 9 for all operating systems and takes about 2 hours to download.  Wait about 45 minutes when mine will have finished downloading (I started just over an hour ago) and I'll post the relevent one here as an attachment. (Edit: [Too big for the forums; uploaded here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz"). Oh well.)

Alternatively you can use Opera 9.5 beta, which does support Flash 9.0.115.  But of course that is a beta version, so use at your own risk and all that.

---

### Post by TeoBigusGeekus on 2008-04-04
I use Opera 9.5 for 4 months now without any particular problems. Some crashes once in a while, but it is still better than the major bloatware called Firefox...

---

### Post by philmetz on 2008-04-04
this is my info for opera:

```

Version information
Version
9.50 Beta 1
Build
1643
Platform
Linux
System
i686, 2.6.22-14-generic
Qt library
3.3.7
Java
Java Runtime Environment installed
Browser identification

Opera/9.50 (X11; Linux i686; U; en)
Paths
Preferences
/home/philip/.opera/opera6.ini
Saved session
/home/philip/.opera/sessions/autopera.win
Bookmarks
/home/philip/.opera/opera6.adr
Opera directory
/home/philip/.opera/
Cache
/home/philip/.opera/cache4/
Help documents
/home/philip/.opera/opcache/
Mail directory
/home/philip/.opera/mail/
Plug-in path
/usr/lib/opera/plugins
/usr/lib/flashplugin-nonfree
/usr/lib/mozilla/plugins
User CSS directory
/home/philip/.opera/styles/user/

```

See i got 9.5 beta but still its all blank

---

### Post by TeoBigusGeekus on 2008-04-04
Go to this page
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")
and download the .tar.gz file.
Extract its contents somewhere, say on your Desktop.
It will be a folder containing 2 files.
Open the file flashplayer-installer with gedit and press the button Replace.
Add Mozilla in the Search for field, Opera in the Replace with field and press Replace all. 
Save the script and execute it.
Good luck!

---

### Post by philmetz on 2008-04-04
How do i execute the script?

---

### Post by TeoBigusGeekus on 2008-04-04
Double click it and select Run in Terminal.

---

### Post by philmetz on 2008-04-04
Ok i did that and nothing,
it opened in terminal
said close all browsers and press enter then it closed

then i opened opera, tried youtube and still grey?

---

### Post by TeoBigusGeekus on 2008-04-04
Were Opera and all other browsers closed when you run the script?

---

### Post by philmetz on 2008-04-04
yes

---

### Post by SEMW on 2008-04-04
If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

---

### Post by twright on 2008-04-04
you can browse the filesystem as root in order to put the plugin in the folder by typing gksu nautilus into terminal > **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

---

### Post by Tomatz on 2008-04-04
> **TeoBigusGeekus said:**
> I use Opera 9.5 for 4 months now without any particular problems. Some crashes once in a while, but it is still better than the major bloatware called Firefox...

Easy!

---

### Post by philmetz on 2008-04-05
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

Yes! thanks that worked!

---

### Post by robotron2084 on 2008-04-05
It looks as though Flash 9,0,45,0 works fine in Opera on Hardy Heron, but the new 9,0,115,0 player does not, at the time of this writing. Thanks for the help SEMW!

---

### Post by barmaley on 2008-04-06
Thanks SEMW
It works

---

### Post by TenPlus1 on 2008-04-06
I'm using the latest Opera 9.50 beta form their site and flash works fine for me...

goto:
Preferences -> Advances -> Content screen,

Click:
Plugin Options -> Change Path -> Add

add this line:
/usr/lib/flashplugin-nonfree

then refresh plugins and flash will appear, OK all the windows and check out this site to make sure it works ok:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by CDL-WarChilde on 2008-04-06
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

Using Opera 9.27, this worked for me, thanks!!! :guitar:

---

### Post by Blastomorpha on 2008-04-14
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

Wow, in this way I don't even need to install any flash related package!
Very appreciate it! =D>

---

### Post by rahimveron on 2008-04-18
Thanks a lot SEWN. You have explained it nicely and above all damn it works:D with Opers 9.27 and that selecting that particular plugin from Advance=>Download section in Opera was cool. Nobody suggested that step. Now i wont be worried about upgrading Opera to newer stable version. Have been using 9.26 for a long time for his flash problem. Thanks a million once again.

---

### Post by everah on 2008-05-07
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

OH. HELLS. YEAH. This totally worked. Thanks.

---

### Post by mssg131187 on 2008-05-12
> **TenPlus1 said:**
> I'm using the latest Opera 9.50 beta form their site and flash works fine for me...

goto:
Preferences -> Advances -> Content screen,

Click:
Plugin Options -> Change Path -> Add

add this line:
/usr/lib/flashplugin-nonfree

then refresh plugins and flash will appear, OK all the windows and check out this site to make sure it works ok:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Thanks, worked for me...

---

### Post by PhatKat on 2008-05-16
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.

Hi there! I am running Opera 9.27 and am a newbie at linux :P I d/l version 9.0.48 to my home folder but the last step : untargazzing to a specific directory - i do not know how to do or the commands in Terminal? Can you explain it in simpler terms? Thanks in advance :popcorn:

---

### Post by PunkLV on 2008-05-18
This thread should be stickied or at least added to Documentation or something alike, for easy access! I've spent 4+ hours straight googling and messing with .so file and paths, even got Opera to detect flash, but making flash content static or just black, not gray, like in case theres no plugin... 

Damn I'm happy right now...

---

### Post by PhatKat on 2008-05-24
Hmm d/l 9.5b and got this error meggase beofre Opera crashes at startup:
"Before you can use your mail and newsfeed, OPera needs to update your mail database to a new format. Would you like to do this now?"
If i click yes or no Opera hangs while if i delay in pressing anything, Opera crashes ...help!!!

---

### Post by oavicena on 2008-07-14
> **SEMW said:**
> If version 9.0.115 (the current version) gives you a grey square in Opera, try version 9.0.48.  I've uploaded it [here]("http://home.btconnect.com/geoffwoolf/files/libflashplayer.so.tar.gz") since it's too big for the forums, and the [official Adobe package]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1") contains every version for all OSes and takes aaages to download.  Just untargz that file into /usr/lib/opera/plugins, restart Opera, and go to Tools -> Preferences -> Advanced -> Downloads -> select Flash -> Edit -> and select the one from /usr/lib/opera/plugins.
It worked for me. Opera 9.27, the one installed using apt and default source.list on hardy heron. Thanks SEMW.

---


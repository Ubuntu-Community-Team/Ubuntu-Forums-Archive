---
title: "cron-o-meter software crash in Ubuntu 14.10"
date: 2015-01-08
forum: General Help
---

### Post by petermartin2 on 2015-01-08
I have a software installed for tracking calories and training and it worked well at first but since a while I can't open it getting this error message:

[IMG]http://s8.postimg.org/ykpbqwbth/errorcron.jpg[/IMG]
Anyone know what I could do to get it running again?

---

### Post by petermartin2 on 2015-01-08
java.lang.IndexOutOfBoundsException: Index 0, Size: 0

java.util.ArrayList.get(ArrayList.java:411)
ca.spaz.cron.summary.NutrientTable$NutrientTableModel.getNutrientInfo(Unknown Source)
ca.spaz.cron.summary.NutrientTable$NutriendTableModel.getValueAt (Unknown Source)

Is there any file I could change or edit to fix it? The application won't even start up after this error message it's really annoying. Very useful app so I will miss it if no one has an idea how to fix it. Anyone know of a similar program for Ubuntu for counting calories and exercise?

---

### Post by petermartin2 on 2015-01-08
I've tried reinstalling it and following a guide about installing the apple OS version instead but I keep getting this message when running the script:

```
w@w:~$ sh cron-o-meter.sh
Error: Could not find or load main class r:docs.jar
```

Pretty much any up to date ideas about installing a stable version of cron-o-meter in Ubuntu would be great, last thread I can find is from 2010.

Also ideas about how to completely uninstall it would be valuable. The software was working pretty good in the beginning so if I could completely remove it maybe I will have better time running it in the future?

---

### Post by ian-weisser on 2015-01-08
The error looks like some lookup table within cronometer is corrupted or has some internal bug.
I agree that uninstalling and reinstalling might replace a corrupted table, and it's probably worth a try.

Did you install the version from the Ubuntu repositories (Software Center)? Or someplace else?
If you installed from Software Center, go back and uninstall it there. Software Center is generally the safest place to install stable software from.
If you installed using some other instructions from out in the wild, wild web, go back there and look for uninstall instructions. A link to those instructions would help us help you....

---

### Post by petermartin2 on 2015-01-08
> **ian-weisser said:**
> The error looks like some lookup table within cronometer is corrupted or has some internal bug.
I agree that uninstalling and reinstalling might replace a corrupted table, and it's probably worth a try.

Did you install the version from the Ubuntu repositories (Software Center)? Or someplace else?
If you installed from Software Center, go back and uninstall it there. Software Center is generally the safest place to install stable software from.
If you installed using some other instructions from out in the wild, wild web, go back there and look for uninstall instructions. A link to those instructions would help us help you....

The only version of the application I've managed to install is from Software Center. After it bugged I also tried to install the macos version but had no success. When trying to delete all the files with the name cron-o-meter there is one file that I can not delete for some reason. Not with sudo in terminal or anything

The first few times I started the app it worked fine. Then maybe the 4th time I opened it (I think after a restart of the computer) it stopped working

---

### Post by ian-weisser on 2015-01-08
> **petermartin2 said:**
> The only version of the application I've managed to install is from Software Center.

Please do file a bug report. I'm sure the developer would like to know about the problem.
You are welcome to file on the Ubuntu bug tracker, but do be aware that some volunteer will manually need to locate and forward the bug the cronometer.com. You might get a faster resolution submitting directly to cronometer.com.

 
> **petermartin2 said:**
> I also tried to install the macos version but had no success.

Yeah, we all try that once.


> **petermartin2 said:**
> When trying to delete all the files with the name cron-o-meter there is one file that I can not delete for some reason. Not with sudo in terminal or anything

(Ears perk up) Say, what?

Here's the list of files supplied by the cronometer package:
```
/usr/bin/cronometer
/usr/share/applications/cronometer.desktop
/usr/share/cronometer/crdb_005.jar
/usr/share/cronometer/docs.jar
/usr/share/cronometer/usda_sr24.jar
/usr/share/doc/cronometer/changelog.Debian.gz
/usr/share/doc/cronometer/copyright
/usr/share/java/cronometer.jar
/usr/share/lintian/overrides/cronometer
/usr/share/man/man1/cronometer.1.gz
/usr/share/pixmaps/cronometer.png
```

Which one fails to delete?
How, exactly are you trying to delete it? (please be detailed)
What, exactly happens? Error message?

---

### Post by petermartin2 on 2015-01-09
> **ian-weisser said:**
> Please do file a bug report. I'm sure the developer would like to know about the problem.
You are welcome to file on the Ubuntu bug tracker, but do be aware that some volunteer will manually need to locate and forward the bug the cronometer.com. You might get a faster resolution submitting directly to cronometer.com.

 


Yeah, we all try that once.




(Ears perk up) Say, what?

Here's the list of files supplied by the cronometer package:
```
/usr/bin/cronometer
/usr/share/applications/cronometer.desktop
/usr/share/cronometer/crdb_005.jar
/usr/share/cronometer/docs.jar
/usr/share/cronometer/usda_sr24.jar
/usr/share/doc/cronometer/changelog.Debian.gz
/usr/share/doc/cronometer/copyright
/usr/share/java/cronometer.jar
/usr/share/lintian/overrides/cronometer
/usr/share/man/man1/cronometer.1.gz
/usr/share/pixmaps/cronometer.png
```

Which one fails to delete?
How, exactly are you trying to delete it? (please be detailed)
What, exactly happens? Error message?

Ok I found [http://blog.cronometer.com/](http://blog.cronometer.com/) so I thought this is how I could file a bug report however I have no success with registering a blog.com account because their anti-spam verification picture is not showing in any of my browsers although they are all up to date. CAPTCHA is working fine for me on other pages.[LEFT][COLOR=#444444][FONT=proxima-nova][/FONT][/COLOR]
[/LEFT]
 Is there anywhere else I could file a bug report for CRON-o-Meter? I've installed a terminal-run app called nut-nutrition but it's not really what I need.

The file I can't delete is located in /usr/share/app-install/desktop and called simply CRON-o-Meter. I can't delete it from terminal either

[IMG]http://s3.postimg.org/ahocd85pt/cantdel.jpg[/IMG]
```
w@w:/usr/share/app-install/desktop$ rm CRON-o-Meter
rm: cannot remove &#8216;CRON-o-Meter&#8217;: No such file or directory
w@w:/usr/share/app-install/desktop$ rm CRON-o-Meter.txt
rm: cannot remove &#8216;CRON-o-Meter.txt&#8217;: No such file or directory
w@w:/usr/share/app-install/desktop$ rm CRON-o-Meter.desktop
rm: cannot remove &#8216;CRON-o-Meter.desktop&#8217;: No such file or directory
```

---

### Post by petermartin2 on 2015-01-09
I've also tried to make sure from Terminal that the files you mention seem to be deleted but still no success on solving the problem when reinstalling CRON-o-Meter

```
w@w:/$ rm usr/bin/cronometer
rm: cannot remove ‘usr/bin/cronometer’: No such file or directory
w@w:/$ rm usr/share/applications/cronometer.desktop
rm: cannot remove ‘usr/share/applications/cronometer.desktop’: No such file or directory
w@w:/$ rm usr/share/cronometer/crdb_005.jar
rm: cannot remove ‘usr/share/cronometer/crdb_005.jar’: No such file or directory
w@w:/$ rm usr/share/cronometer/docs.jar
rm: cannot remove ‘usr/share/cronometer/docs.jar’: No such file or directory
w@w:/$ rm usr/share/cronometer/usda_sr24.jar
rm: cannot remove ‘usr/share/cronometer/usda_sr24.jar’: No such file or directory
w@w:/$ rm usr/share/doc/cronometer/changelog.Debian.gz
rm: cannot remove ‘usr/share/doc/cronometer/changelog.Debian.gz’: No such file or directory
w@w:/$ rm usr/share/doc/cronometer/copyright
rm: cannot remove ‘usr/share/doc/cronometer/copyright’: No such file or directory
w@w:/$ rm usr/share/java/cronometer.jar
rm: cannot remove ‘usr/share/java/cronometer.jar’: No such file or directory
w@w:/$ rm usr/share/lintian/overrides/cronometer
rm: cannot remove ‘usr/share/lintian/overrides/cronometer’: No such file or directory
w@w:/$ rm usr/share/man/man1/cronometer.1.gz
rm: cannot remove ‘usr/share/man/man1/cronometer.1.gz’: No such file or directory
w@w:/$ rm usr/share/pixmaps/cronometer.png
rm: cannot remove ‘usr/share/pixmaps/cronometer.png’: No such file or directory
```

---

### Post by petermartin2 on 2015-01-09
I had added two days of exercise and diet to it and set some goals before it crashed that's the only thing I had time to do with it before it stopped working

---

### Post by Holger_Gehrke on 2015-01-09
I don't think a bug report will do all that much good since the desktop  version is more or less abandoned. The website [http://cronometer.com](http://cronometer.com)  does not have any link (that I could find) to the download page (that is  still there) and if you do find it, it urges you to use the mobile or  webapp version.

The download on Sourceforge  ([http://sourceforge.net/projects/cronometer/](http://sourceforge.net/projects/cronometer/)) hasn't been updated in 1.5  years and the source-tarball you get there is ... problematic ... to  say the least ( wouldn't compile without several changes to the  build.xml file and recoding one of the source-files from ms-ansi to  utf-8).

The error messages you get look to me like your personal  data (your own food and recipe data probably) got corrupted. These are -  as far as I can tell - saved in a hidden directory in your  home directory '~/.cronometer' .

---

### Post by ian-weisser on 2015-01-09
> **petermartin2 said:**
> Is there anywhere else I could file a bug report for CRON-o-Meter? I've installed a terminal-run app called nut-nutrition but it's not really what I need.

Sure, lots of places...but none of them will do anything about it - it's not their software.
Rather like sending a complaint about your electric service to your grocer instead. Sure, the grocer will listen.... 


> **petermartin2 said:**
> The file I can't delete is located in /usr/share/app-install/desktop and called simply CRON-o-Meter. I can't delete it from terminal either

You probably cannot delete it because it's NOT called simply CRON-o-meter. The desktop search, trying to be helpful, has misled.
Let's take a look at some files in that directory.
Mine has almost 13,000 files in it, so let's limit it to the first six.
```
$ ls -l /usr/share/app-install/desktop/ | head -n6
total 12852
-rw-r--r-- 1 root root   295 Oct 13 09:39 0ad:0ad.desktop
-rw-r--r-- 1 root root   349 Oct 13 09:40 0install-core:0install.desktop
-rw-r--r-- 1 root root   302 Oct 13 09:40 3dchess:3dchess.desktop
-rw-r--r-- 1 root root   283 Oct 13 09:39 3depict:3depict.desktop
-rw-r--r-- 1 root root   305 Oct 13 09:39 4digits:4digits.desktop
```

See how the file name for 3dchess isn't simply '3dchess'? It's actually '3dchess:3dchess.desktop'

If I wanted to see the contents (note the escape or quotes for the ':'): 
```
less /usr/share/app-install/desktop/3dchess\:3dchess.desktop
less "/usr/share/app-install/desktop/3dchess:3dchess.desktop"
```

And if I wanted to delete it manually (note the sudo. File is owned by root):
```
 sudo rm /usr/share/app-install/desktop/3dchess\:3dchess.desktop
```


But manually deleting stuff has consequences, too:
Turns out, I have a cronometer file, too...but it's NOT provided by cronometer (which I don't have installed).
```
$ dpkg -S /usr/share/app-install/desktop/cronometer\:cronometer.desktop 
app-install-data: /usr/share/app-install/desktop/cronometer:cronometer.desktop

```
It's provided by an entirely different package, app-install-data. The file is supposed to be there.


> **petermartin2 said:**
> I've also tried to make sure from Terminal that the files you mention seem to be deleted but still no success on solving the problem when reinstalling CRON-o-Meter

I recommend against testing for deletion that way.
A mistake could break your system quite horribly.

Also, there is a vital system service coincidentally named 'cron'. Do not delete it by mistake. Deleting 'cron' or any of it's required files will thoroughly break your system.

---

### Post by petermartin2 on 2015-01-09
> **Holger_Gehrke said:**
> I don't think a bug report will do all that much good since the desktop  version is more or less abandoned. The website [http://cronometer.com](http://cronometer.com)  does not have any link (that I could find) to the download page (that is  still there) and if you do find it, it urges you to use the mobile or  webapp version.

The download on Sourceforge  ([http://sourceforge.net/projects/cronometer/](http://sourceforge.net/projects/cronometer/)) hasn't been updated in 1.5  years and the source-tarball you get there is ... problematic ... to  say the least ( wouldn't compile without several changes to the  build.xml file and recoding one of the source-files from ms-ansi to  utf-8).

The error messages you get look to me like your personal  data (your own food and recipe data probably) got corrupted. These are -  as far as I can tell - saved in a hidden directory in your  home directory '~/.cronometer' .

This actually seemed to work to delete the files in .cronometer now it is working again also after restart! thanks for this.

---

### Post by petermartin2 on 2015-01-09
Ok yes I have been careful with the "cron" since they seemed to contain files that had nothing to do with cronometer thanks for this warning. I hope someone will make a new similar app for ubuntu! I have looked a little at it in desperation in quickly but the only thing I managed to do so far was add a calendar! CRON-o-Meter is great when it's working to bad it's no longer being updated, hope it will work anyway...

---


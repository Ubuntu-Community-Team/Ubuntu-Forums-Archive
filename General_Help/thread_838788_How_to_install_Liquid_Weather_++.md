---
title: "How to install Liquid Weather ++  ???"
date: 2008-06-23
forum: General Help
---

### Post by popatopalous on 2008-06-23
I know you go here:

[http://liquidweather.net/downloads.php](http://liquidweather.net/downloads.php)

and currently down load the file:

lwp-15.0.skz

But my question is what to do with the file? I've never heard of an .skz file. What do I do with it???   :confused:

---

### Post by linuxwizard on 2008-06-23
You do have Super Karamba installed? Their maybe other ways to install but this has always worked for me. Save the skz download to your desktop > go to home folder > click on view > show hidden files click on > look for folder .superkaramba click on > now right click on download copy > paste into .superkaramba >  now click on lwp-15.0.skz > it will install and Liquid Weather will be displayed on desktop >

---

### Post by popatopalous on 2008-06-23
Thanks for the reply.

The file or folder file:///home/ben/Desktop/.superkaramba does not exist.

---

### Post by linuxwizard on 2008-06-23
Do have Super Karamba installed ? Must be installed to create that folder.

---

### Post by popatopalous on 2008-06-23
> **linuxwizard said:**
> Do have Super Karamba installed ? Must be installed to create that folder.

Yes superkaramba is installed. I'm a KDE user and super karamba was installed by default. I am running superkaramba from cli [and it does not prompt to create the file which is probably an error] and then launching liquid weather from there resulting currently in this output:

```
$ superkaramba
/home/ben/Desktop/lwp-15.0.skz/liquid_weather.py:3656: SyntaxWarning: import * only allowed at module level
sys.path.insert(0, '/home/ben/Desktop/lwp-15.0.skz')
Reading config
Reading from Config ...
fontSizeMatrix:
[20, 12, 10, 12, 10]
No such application: 'kxdocker'
Downloading weather in initWidget
http://wwwa.accuweather.com/forecast-current-conditions.asp?partner=accuweather&myadc=0&traveler=0&zipcode=80301&metric=1
parsing Accuweather
US_code
http://wwwa.accuweather.com/forecast.asp?partner=accuweather&myadc=0&traveler=0&zipcode=80301&metric=1
``` 


I also can't get liquid weather to work in Debian or Mandriva currently although the errors are different.

---

### Post by linuxwizard on 2008-06-23
I have never seen Super Karamba installed by default. See if you have this > go to home folder > click on view > show hidden files click on > look for folder .kde > share > apps > superkaramba > themes click on > you should be able to copy & paste lwp-15.0.skz into the themes folder.

---

### Post by popatopalous on 2008-06-23
> **linuxwizard said:**
> I have never seen Super Karamba installed by default. See if you have this > go to home folder > click on view > show hidden files click on > look for folder .kde > share > apps > superkaramba > themes click on > you should be able to copy & paste lwp-15.0.skz into the themes folder.

Regardless of whether it was installed by default it was installed the day I installed Ubuntu [NOT Kubuntu, my preference as I thought it would lead to easier resolution of problems such as this] when I went through the list and installed KDE packages I wanted/needed. I have not yet installed kupuntu-desktop. The point being that super karamba was installed long before I learned of Liquid Weather. I am further confused as to your question as I couldn't even open Liquid Weather if super karamba wasn't installed.

Now to answer your question it is easier for me to use cli:

```
$ cd /home/ben/.kde/share/apps
ben@ben-desktop:~/.kde/share/apps$ ls
amarok   drkonqi  kabc      kconf_update  kdesktop  kfile  kicker   konqsidebartng  kopete   nsplugins
d3lphin  k3b      kaffeine  kcookiejar    kdisplay  kfm    klipper  konqueror       kwallet  RecentDocuments
digikam  kab      kate      kdeprint      keep      khtml  kmail    konsole         noatun   remoteview

```

package super karamba was installed with aptitude.

```
$ superkaramba -v
Qt: 3.3.8b
KDE: 3.5.9
SuperKaramba: 0.42
```

Now for the good part. I think I have it working. I think what did that was 'rm -rf ~/.superkaramba'. I think. This appears to me to be a rather buggy app and well like I said. I think that's what worked.

Hey man, thanks for your replies and help. Greatly appreciated.  
:lolflag: :popcorn:

Now if only the same would work in Debian... And it didn't... 
:lolflag::lolflag:

---


---
title: "Java Applet Issues"
date: 2008-01-06
forum: General Help
---

### Post by rkillcrazy on 2008-01-06
I have 7.10 set up and everything runs smooth as silk!  However, if I use a web page that has a java applet in it, FF& Epiphany get laggy!  For instance, I have a web gallery that uses a java applet and I use LogMeIn to admin many Windows PCs.  Any time I visit these sites, the browser gets laggy.  If I hit these sites on a Windows PC or in a VirtualBox PC (installed on this Ubuntu PC), the sites work fine and are snappy!  What am I doing wrong?

01-06-08
0005 EST

---

### Post by rkillcrazy on 2008-01-11
bump...

Nobody has any ideas?

---

### Post by SyL on 2008-01-13
Hi,

Do you have any output if you run firefox from a terminal?

Are you running a 64 bits box?

Could you post your java version: ```
java -version
```

Can you see a javaplugin.so if you do:

```
ls [COLOR="Orange"]/path/to/mozilla/firefox[/COLOR]/plugins
```

---

### Post by rkillcrazy on 2008-01-13
> **SyL said:**
> Hi,

Do you have any output if you run firefox from a terminal?

Are you running a 64 bits box?

Could you post your java version: ```
java -version
```

Can you see a javaplugin.so if you do:

```
ls [COLOR="Orange"]/path/to/mozilla/firefox[/COLOR]/plugins
```

Java version:
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

I couldn't find where it told me if I'm running 64-bit or 32-bit.  And I don't recall what I loaded it with.

I couldn't find the plugins directory for FF so I opened FF and brought up the "about:plugins" page.  I'll rough it out below as the page was rather long.
Shockwave Flash
GCJ Web Browser Plugin (using IcedTea) 1.4
VLC Multimedia Plugin
Totem Web Browser Plugin 2.20.0
Windows Media Player Plug-in 10 (compatible; Totem)
DivX® Web Player
QuickTime Plug-in 7.2.0


If you want me to do some more commands or look elsewhere, let me know...

01-13-08
2230 EST

---

### Post by SyL on 2008-01-14
1.4.2-02 is quite old!
you should upgrade your JRE:
```
sudo apt-get install sun-java6-plugin
```

you can find the plugin directory under, something like:
/home/yourUser/.mozilla


When i was asking about 64bits, it's about your machine: i.e. do you have a 64bits CPU?

---

### Post by rkillcrazy on 2008-01-15
> **SyL said:**
> 1.4.2-02 is quite old!
you should upgrade your JRE:
```
sudo apt-get install sun-java6-plugin
```

you can find the plugin directory under, something like:
/home/yourUser/.mozilla


When i was asking about 64bits, it's about your machine: i.e. do you have a 64bits CPU?

I know I have that installed.  I saw it in Synaptic.  Is it not being used by FF for some reason?

Yes, it's a dual-core 64-bit AMD 6000+ ~3.0 GHz.  However, I don't know if it's a 64bit OS or not.

---

### Post by SyL on 2008-01-15
> **rkillcrazy said:**
> I know I have that installed.  I saw it in Synaptic.  Is it not being used by FF for some reason?

Yes, it's a dual-core 64-bit AMD 6000+ ~3.0 GHz.  However, I don't know if it's a 64bit OS or not.


1/ try:
```

sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun

```


2/ did you try to see if there is any output when you launch Firefox from a terminal??


3/ what is the address for your website?


4/ having a 64bits CPU and not using it ... would be a pity

---

### Post by rkillcrazy on 2008-01-15
> **SyL said:**
> 1/ try:
```

sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun

```


2/ did you try to see if there is any output when you launch Firefox from a terminal??


3/ what is the address for your website?


4/ having a 64bits CPU and not using it ... would be a pity

Site:
[http://www.wceastclassof1997.net/rob/gallery/]("http://www.wceastclassof1997.net/rob/gallery/")

Running "firefox" from the terminal just opens it.  There don't seem to be any errors when it opens.

I found some things that may help with the plugins for FF...
I went to my home folder, I hit **CTRL+H** to unhide things, found a **.mozilla** folder and started digging.  I found **/home/rob/.mozilla/pluginreg.dat** which seems to open in a simple text editor.  That same file is also at **/home/rob/.mozilla/firefox/pluginreg.dat**

01-15-08
1728 EST

---

### Post by SyL on 2008-01-17
> **rkillcrazy said:**
> 
Running "firefox" from the terminal just opens it.  There don't seem to be any errors when it opens.

I found some things that may help with the plugins for FF...
I went to my home folder, I hit **CTRL+H** to unhide things, found a **.mozilla** folder and started digging.  I found **/home/rob/.mozilla/pluginreg.dat** which seems to open in a simple text editor.  That same file is also at **/home/rob/.mozilla/firefox/pluginreg.dat**


regarding the error message, i was asking if you get any when you reach your site, not when you open firefox.

try to find a file with a name similar to javaplugin.so under the .mozilla directory

---

### Post by rkillcrazy on 2008-01-17
> **SyL said:**
> regarding the error message, i was asking if you get any when you reach your site, not when you open firefox.

try to find a file with a name similar to javaplugin.so under the .mozilla directory

Well, in that case, no errors from FF.  Furthermore, I was unable to find any file by that name or similar to it under the .mozilla directory.

---

### Post by SyL on 2008-01-24
I actually experiment the same issue when i access your website from my Ubuntu at home. 

This might mean that this is not a configuration issue.
Maybe a bug of the FF plugin?
Or something in your applet which access some libs not working properly.
maybe review your code on this way, looking at your import and the libs used and ask google on this way.


I cannot help you further, sorry.


just one more hint: did you try to access your website with another browser?

---

### Post by rkillcrazy on 2008-01-25
> **SyL said:**
> I actually experiment the same issue when i access your website from my Ubuntu at home. 

This might mean that this is not a configuration issue.
Maybe a bug of the FF plugin?
Or something in your applet which access some libs not working properly.
maybe review your code on this way, looking at your import and the libs used and ask google on this way.


I cannot help you further, sorry.


just one more hint: did you try to access your website with another browser?

No worries... I thank you just the same!

I know it works in FF & IE on Windows PCs.  It was only Ubuntu where I saw the issue.  I'll keep looking...

01-25-08
0829 EST

---

### Post by rkillcrazy on 2008-02-02
I think I may have just figured it out.  I still had this issue until this morning - when I installed the restricted drivers for my nvidia card.  I was playing around with the desktop effects and obviously needed the restricted drivers to be installed.  This was a side effect.  Can anyone else confirm this?  Meaning, those without restricted drivers test the site and then install said drivers and have the site work fine?

02-02-08
1121 EST

---


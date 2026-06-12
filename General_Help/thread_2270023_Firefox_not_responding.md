---
title: "Firefox not responding"
date: 2015-03-19
forum: General Help
---

### Post by andfree on 2015-03-19
I have installed Lubuntu 14.04 LTS on a Toshiba Satellite L10-194.

When I visit some webpages, firefox freezes. Then I click "x" to close firefox and I get the message:
 
```
The window "Mozilla Firefox" does not seem to be responding. Do you want to force it to exit by sending the terminate signal?
```

I think it has to do with flash plugin, but I don't know what to do.

---

### Post by pmi2 on 2015-03-19
> **andfree said:**
> I think it has to do with flash plugin, but I don't know what to do.I wonder if you can test if it is really Flash causing the problem?

In Firefox, Menu, Add-ons, Plugins, change Shockwave Flash to "Ask to Activate" status.  Then visit some of the same pages and see if the problem persists.

---

### Post by andfree on 2015-03-19
> **pmi2 said:**
> In Firefox, Menu, Add-ons, Plugins, change Shockwave Flash to "Ask to Activate" status.

There is no such a plugin.

---

### Post by SeijiSensei on 2015-03-19
Well then, it can't be the fault of the Flash plugin.

Give us the URL of a page you cannot view properly so we can see what might be wrong.

---

### Post by andfree on 2015-03-19
> **SeijiSensei said:**
> Give us the URL of a page you cannot view properly so we can see what might be wrong.

[http://www.agame.com/game/nick-bounty](http://www.agame.com/game/nick-bounty)
[http://www.agame.com/game/royal-pain](http://www.agame.com/game/royal-pain)
[http://www.linuxquestions.org/questions/linux-newbie-8/i%27ve-got-a-black-line-in-my-firefox-address-bar-4175505839/](http://www.linuxquestions.org/questions/linux-newbie-8/i%27ve-got-a-black-line-in-my-firefox-address-bar-4175505839/)

---

### Post by stephen_ward on 2015-03-20
Best bet is try to re load your firefox again. Check for the updates if you need any updates on activate java on firefox

---

### Post by andfree on 2015-03-20
> **stephen_ward said:**
> Best bet is try to re load your firefox again. Check for the updates if you need any updates on activate java on firefox

I remove and re-installed firefox. This didn't solve the problem.

I didn't find any java activated at all. I installed QuickJava 2.0.6 from add-ons, but it didn't help and I removed it again. Then I installed Icedtea java plugin from Software Center but it didn't help and removed it again. Now I have installed OpenJDK Java 7 Runtime, but the problem remains.

I don't have installed neither adobe flash plugin. I installed it, it didn't solve the problem and I removed it again.

---

### Post by kerry_s on 2015-03-20
check in synaptic package manager, on the left click on status, you probably got all kinds of bits & pieces from installs

all i do is install "ubuntu-restricted-extras" all those sites work for me just fine in firefox on lubuntu 14 lts

---

### Post by buzzingrobot on 2015-03-20
Here, both sites load in Firefox normally with Flash and the Icetea plugin both disabled.  The game site wants you to install the Flash plugin, but loads per usual.  (Meaning, the site loads fine without Flash, but you need Flash for the videos to work.)

LinuxQuestions is a forum site with no obvious requirement for any plugin.

If you have other plugins or extensions installed, disable all of them and try again.  if the sites work, re-enable each plugin/extension one at a time to see if one is causing the problem.

---

### Post by andfree on 2015-03-20
> **kerry_s said:**
> check in synaptic package manager, on the left  click on status, you probably got all kinds of bits & pieces from  installs

all i do is install "ubuntu-restricted-extras" all those sites work for me just fine in firefox on lubuntu 14 lts

"Ubuntu-restricted-extras" were not installed. I installed it and the affected packages from synaptic package manager, but it didn't help.

> **buzzingrobot said:**
> If you have other plugins or extensions installed, disable all of them and try again.

I disabled plugins & extensions from firefox Add-ons, but it didn't help. 

Then I did a search for "plugin" at the quick filter of Synaptic Package Manager and I started remove one-by-one all these: 

```
Adobe Flash Player plugin installer
Fluendo mp3 decoder GStreamer 0.10 plugin
Fluendo mp3 decoder GStreamer 1.0 plugin
libav plugin for GStreamer
Loadable modules for extending Sylpheed features
LXDE GTK+ theme switcher (plugin)
GStreamer faad plugin from the "bad" set
GStreamer videoparsers plugin from the "bad" set
ICE library (GStreamer 0.10 plugin)
lxpanel indicator applet
GStreamer plugins from the "base" set
efficient, featureful word processor with collaboration
GStreamer plugins from the "base" set
GStreamer plugins from the "ugly" set
GStreamer plugins from the "ugly" set
GStreamer libraries from the "base" set
GStreamer plugin for PulseAudio
GStreamer plugins from the "bad" set (Multiverse Variant)
Core GStreamer libraries and elements
Qt 4 MySQL database driver
libraries for the Soprano RDF framework
```

Then I tried to remove this:

```
Cyrus SASL - pluggable authentication modules (DB)
```

and got the message:

```
Could not apply changes!
Fix broken packages first.
```

Daemon for the Soprano RDF framework seems to be broken. I can't remove nothing else before fix it.

And the problem remains.

---

### Post by buzzingrobot on 2015-03-20
> **andfree said:**
> 
I disabled plugins & extensions from firefox Add-ons, but it didn't help. 

You've eliminated one possible cause, assuming you restarted Firefox.

> Then I did a search for "plugin" at the quick filter of Synaptic Package Manager and I started remove one-by-one all these: 

```
Adobe Flash Player plugin installer
Fluendo mp3 decoder GStreamer 0.10 plugin
Fluendo mp3 decoder GStreamer 1.0 plugin
libav plugin for GStreamer
Loadable modules for extending Sylpheed features
LXDE GTK+ theme switcher (plugin)
GStreamer faad plugin from the "bad" set
GStreamer videoparsers plugin from the "bad" set
ICE library (GStreamer 0.10 plugin)
lxpanel indicator applet
GStreamer plugins from the "base" set
efficient, featureful word processor with collaboration
GStreamer plugins from the "base" set
GStreamer plugins from the "ugly" set
GStreamer plugins from the "ugly" set
GStreamer libraries from the "base" set
GStreamer plugin for PulseAudio
GStreamer plugins from the "bad" set (Multiverse Variant)
Core GStreamer libraries and elements
Qt 4 MySQL database driver
libraries for the Soprano RDF framework
```

Then I tried to remove this:

```
Cyrus SASL - pluggable authentication modules (DB)
```

and got the message:

```
Could not apply changes!
Fix broken packages first.
```

Daemon for the Soprano RDF framework seems to be broken. I can't remove nothing else before fix it.




Not all plugins installed ono your system are Firefox plugins.  All Firefox plugins will be displayed in the Add-ons page.

You need the Adobe Flash plugin to view Flash video in Firefox, as at that game site. You know it is not causing the problem because the problem remained after you disabled it.

All GStreamer packages are multimedia codecs and should not have been removed. Without them you very likely will not be able to get sound out of any multimedia application.
 
(Installing the "ubuntu-restricted-extras" package will reinstall Flash and the codecs.)

None of the other packages removed have anything to do with Firefox.

The message about broken packages should be addressed. I'd suggest opening another thread for that.

For the Firefox issue, what, exactly, happens when you point it at those two sites?  What, if anything, displays?  Blank page?  Broken page? What's in the address bar? Are there any error or warning messages?  If you open a terminal and try to ping (for example, *"ping [www.linuxquestions.org]("http://www.linuxquestions.org")*") the URL's, what do you see?  You should see a continuing display that looks like this:```
 PING www.linuxquestions.org (75.126.162.205) 56(84) bytes of data.
64 bytes from www.linuxquestions.org (75.126.162.205): icmp_seq=1 ttl=52 time=50.0 ms
```  If you don't see that, it could indicate your system is not resolving the URL for the sites into the IP address needed to locate it.

---

### Post by andfree on 2015-03-20
> **buzzingrobot said:**
> (Installing the "ubuntu-restricted-extras" package will reinstall Flash and the codecs.)

"Ubuntu-restricted-extras" package still appears as installed, although Flash and most of GStreamer packages have been removed.

> **buzzingrobot said:**
> For the Firefox issue, what, exactly, happens when you point it at those two sites?  What, if anything, displays?  Blank page?  Broken page? What's in the address bar? Are there any error or warning messages?

The webpages are displayed normally, but soon they freeze and I can't scroll them up & down. Sometimes they freeze too fast and stay blank, but not very often. The webpage addresses appear normally in the address bar. And on the firefox tab the spinning thing freezes. I close the firefox window by clicking at "x" and I get the message:

```
The window "Mozilla Firefox" does not seem to be responding. Do you want to force it to exit by sending the terminate signal?
```

 > **buzzingrobot said:**
> If you open a terminal and try to ping (for example, *"ping [www.linuxquestions.org]("http://www.linuxquestions.org")*") the URL's, what do you see?  You should see a continuing display that looks like this:```
 PING www.linuxquestions.org (75.126.162.205) 56(84) bytes of data.
64 bytes from www.linuxquestions.org (75.126.162.205): icmp_seq=1 ttl=52 time=50.0 ms
```

I see continuing displays like this ( for [www.linuxquestions.org]("http://www.linuxquestions.org") ):

```
PING www.linuxquestions.org (75.126.162.205) 56(84) bytes of data.
64 bytes from www.linuxquestions.org (75.126.162.205): icmp_seq=1 ttl=51 time=187 ms
```

& this ( for [www.agame.com]("http://www.agame.com") ):

```
PING gs1.wac.v1cdn.net (93.184.220.39) 56(84) bytes of data.
64 bytes from 93.184.220.39: icmp_seq=1 ttl=57 time=74.3 ms
```

---

### Post by buzzingrobot on 2015-03-20
Ubuntu-restricted-extras is a 'package' that installs other packages. One contains Flash, one contains the codecs, one contains Microsoft fonts, etc.  If you uninstall it and then re-install it, I believe you'll be OK.

Your name resolution is working.  The pages load, but then crash. I'm at a loss to explain why those two sites generate a crash, especially linuxquestions.org, which is a plain bread-and-butter forum site.  Keeping the System Monitor open to watch how much memory Firefox consumes (look for it in the Processes tab) as you navigate to those pages will tell you if there's a sudden large memory spike. 

My only advice at this point is to resolve the broken packages issues, then be sure the system is correctly updated.

---

### Post by andfree on 2015-03-20
> **buzzingrobot said:**
> Ubuntu-restricted-extras is a 'package' that installs other packages. One contains Flash, one contains the codecs, one contains Microsoft fonts, etc.  If you uninstall it and then re-install it, I believe you'll be OK.

It was uninstalled, I installed it, then I removed all the packages I wrote at #11 and it still appears as installed.

> **buzzingrobot said:**
> Keeping the System Monitor open to watch how much memory Firefox consumes (look for it in the Processes tab) as you navigate to those pages will tell you if there's a sudden large memory spike.

About 159-168 MB. At this page ( [http://ubuntuforums.org](http://ubuntuforums.org) ) & at this moment, Task Manager shows 159-161 MB. There' s not seems to be a sudden large memory spike for those pages.

> **buzzingrobot said:**
> My only advice at this point is to resolve the broken packages issues

The broken packages issues seems to have been auto-resolved. I don't find any broken packages at Synaptic Manager but, just to be on the safe side, I reinstalled (without any problem) Daemon for the Soprano RDF framework which had the issue.

> **buzzingrobot said:**
> then be sure the system is correctly updated.

I ran:

```
sudo apt-get update
```

I don't find Update Manager at System Tools anymore, perhaps because of the packages I have removed.

---

### Post by buzzingrobot on 2015-03-20
Unless you specifically remove Ubuntu-restricted-extras, the package manager will consider it installed.

---

### Post by andfree on 2015-03-21
I did a fresh installation of lubuntu-14.04-alternate-i386.iso and I updated the system. The problem remains. Sometimes appears at the google search pages, too.

---

### Post by Yellow Pasque on 2015-03-21
Just to be clear, you did remove/overwrite your old user data (especially your Mozilla/Firefox) profile when you reinstalled, correct?

Try running in safe mode:
```
firefox -safe-mode
```

If it's still crashing in safe-mode, then this seems like the next logical step to get a more detailed error message: [https://wiki.ubuntu.com/MozillaTeam/Bugs#Crashes](https://wiki.ubuntu.com/MozillaTeam/Bugs#Crashes)

---

### Post by andfree on 2015-03-21
> **Temüjin said:**
> Just to be clear, you did remove/overwrite your old user data (especially your Mozilla/Firefox) profile when you reinstalled, correct?

I think the answer is "yes". I did a complete OS re-installation using the entire disk. I didn't keep any data, user profile or whatever.

> **Temüjin said:**
> Try running in safe mode:
```
firefox -safe-mode
```

If it's still crashing in safe-mode, then this seems like the next logical step to get a more detailed error message: [https://wiki.ubuntu.com/MozillaTeam/Bugs#Crashes](https://wiki.ubuntu.com/MozillaTeam/Bugs#Crashes)

The problem remains. This is the terminal display:

```
~$ firefox -safe-mode

(process:2768): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xaba44aa0)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xaba44a30)" of type `GString'
Terminated
```

I did a bug report:
[URL="https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1434848"]
https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1434848[/URL]

---


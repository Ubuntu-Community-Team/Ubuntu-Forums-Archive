---
title: "Which alternative to flash player"
date: 2015-02-06
forum: General Help
---

### Post by Cyber72 on 2015-02-06
Firefox is warning me that I shouldn't use Flash Player. The updater gives me the following alternatives
YUM for linux
.tar,gz
.rpm
APT for ubuntu 10.4+

or should I install pepper flash?
It needs to work withh youtube and BBC radio

Thanks

---

### Post by kerry_s on 2015-02-06
none.
you should install flash through the software center
or
using the terminal: sudo apt-get install flashplugin-installer

---

### Post by carl4926 on 2015-02-06
Are you actually telling us that you use Ubuntu 10.04?

In any case, what you list makes little sense, except that they are packaging methods and nothing to do with Flash Player.

There are 2 LTS versions available to you 12.04 and 14.04
14.04 would be my suggestion
Flash Player works just fine, but many do use Chromium with the pepper flash plugin as an option

---

### Post by monkeybrain20122 on 2015-02-06
If you have installed it already just do a regular upgrade.

---

### Post by kerry_s on 2015-02-07
> **carl4926 said:**
> Are you actually telling us that you use Ubuntu 10.04?

In any case, what you list makes little sense, except that they are packaging methods and nothing to do with Flash Player.

There are 2 LTS versions available to you 12.04 and 14.04
14.04 would be my suggestion
Flash Player works just fine, but many do use Chromium with the pepper flash plugin as an option

no, those are the options your given if you go to the adobe site to download flash.

---

### Post by Bucky Ball on 2015-02-07
> **kerry_s said:**
> none.
you should install flash through the software center
or
using the terminal: sudo apt-get install flashplugin-installer

^^^
This. 

No need to download and install manually. You want flashplugin-installer from SCentre or use the command kerry_s provided in a terminal. ;)

---

### Post by lisati on 2015-02-07
> **Bucky Ball said:**
> ^^^
This. 

No need to download and install manually. You want flashplugin-installer from SCentre or use the command kerry_s provided in a terminal. ;)

Exactly. 

I recently had my system whinge about a vulnerable version of flashplayer being installed, and the solution was to remove the currently installed version, and install flashplugin-installer. No problems since, and no need to mess around trying to figure out what to download from the adobe site.

---

### Post by mooreted on 2015-02-07
One thing to remember about Linux: It is not Windows. You almost never go online and look for something to download. Pretty much everything you need is in the repositories. Downloading random crap from the Internet is what gets people in trouble.

---

### Post by carl4926 on 2015-02-07
> **Cyber72 said:**
> Firefox is warning me that I shouldn't use Flash Player. The updater gives me the following alternatives
YUM for linux
.tar,gz
.rpm
APT for ubuntu 10.4+

or should I install pepper flash?
It needs to work withh youtube and BBC radio

Thanks

OK It's just that the OP said Firefox is warning me that I shouldn't use Flash Player -
I don't ever recall having that. Which sort of had me thinking he might be running an outdated OS.

I concur with ever other comment here about using the software sources that are part of Ubuntu.
If Adobe site really quotes v 10.04, it just shows how lame it is.

And FYI: I wasn't aware bbc radio required flash player. How silly would that be?

---

### Post by Yellow Pasque on 2015-02-07
> If Adobe site really quotes v 10.04, it just shows how lame it is.

If you look carefully, it says 10.4**+** (meaning 10.04 or later).

---

### Post by SeijiSensei on 2015-02-07
> **carl4926 said:**
> OK It's just that the OP said Firefox is warning me that I shouldn't use Flash Player -
I don't ever recall having that.

Probably he got the message all of us have been seeing frequently [for the past few weeks]("http://ubuntuforums.org/showthread.php?t=2264304"), that the plugin has a security vulnerability and requires an update.  The warning screen includes a link to the Adobe site, so it's not surprising that people will follow that and try to download the package from there.

---

### Post by Bucky Ball on 2015-02-07
> **SeijiSensei said:**
> Probably he got the message all of us have been seeing frequently [for the past few weeks]("http://ubuntuforums.org/showthread.php?t=2264304"), that the plugin has a security vulnerability and requires an update.  The warning screen includes a link to the Adobe site, so it's not surprising that people will follow that and try to download the package from there.

+1. Agreed.

---

### Post by yancek on 2015-02-07
The error is specific to firefox as they have added an option which will give you that warning it you don't have the latest plugin.  About a week ago it was .438, I updated four days ago to .440 and if you go to the Adobe site now, it is 11.2.202.442.  If you see the warning, there is an option to Activate in the window, click that and you get a popup to Allow Now or Allow and Remember.  The memory is pretty short as I selected it one time and a minute later went to another site and got the same warning.   I got the warnings on the following systems plus a few others:

> Ubuntu 14.04; firefox 31.0; flash-plugin 11.2.202.400
Ubuntu 12.04; firefox 29.0; flash-plugin 11.2.202.285

All worked with no warnings with the following:

> Mint 17; firefox 28.0; flash-plugin 11.2.202.378
Zorin 9; firefox 30; flash-plugin 11.2.202.394]

The older versions of firefox don't have this option.  Can't remember the name but you should be able to disable it in the location bar with about:config

---

### Post by yancek on 2015-02-07
The warning is specific to firefox as they have added an option which will give you that warning it you don't have the latest plugin.  About a week ago it was .438, I updated four days ago to .440 and if you go to the Adobe site now, it is 11.2.202.442.  If you see the warning, there is an option to Activate in the window, click that and you get a popup to Allow Now or Allow and Remember.  The memory is pretty short as I selected it one time and a minute later went to another site and got the same warning.   I got the warnings on the following systems plus a few others:

> Ubuntu 14.04; firefox 31.0; flash-plugin 11.2.202.400
Ubuntu 12.04; firefox 29.0; flash-plugin 11.2.202.285

All worked with no warnings with the following:

> Mint 17; firefox 28.0; flash-plugin 11.2.202.378
Zorin 9; firefox 30; flash-plugin 11.2.202.394]

The older versions of firefox don't have this option.  Can't remember the name but you should be able to disable it in the location bar with about:config

---

### Post by SeijiSensei on 2015-02-07
The "Activate" message is not related to the version updates.  It's a setting in Tools > Add-ons > Plug-ins.  If you choose "Ask to Activate" as I have, you'll be asked whether to enable Flash on every site that uses it.  You can tell Firefox to remember your choice for that site or ask separately each time.

---

### Post by PaulInBHC on 2015-02-07
I was getting the warning two days ago and yesterday there was an auto update that included the flash update.

---

### Post by Impavidus on 2015-02-07
> **Cyber72 said:**
> 
or should I install pepper flash?
It needs to work withh youtube and BBC radio


> **carl4926 said:**
> 
And FYI: I wasn't aware bbc radio required flash player. How silly would that be?
And neither does youtube, so if that's all, you can live without flash.

Pepper flash doesn't work with firefox, but works with chromium and google chrome. Sometimes I need it. I prefer more modern solutions though, as they tend to work better.

---

### Post by craig10x on 2015-02-07
Chrome comes with pepperflash (the one you get from their website) so that's an easy way to always have the latest and up to date flash on ubuntu...

---

### Post by monkeybrain20122 on 2015-02-07
> **craig10x said:**
> Chrome comes with pepperflash (the one you get from their website) so that's an easy way to always have the latest and up to date flash on ubuntu...

If you remember to upgrade Chrome. I know people who never run updates even when the update manager popup is staring at them, and then they complain that things don't work anymore. :p

---

### Post by Yellow Pasque on 2015-02-07
> **Impavidus said:**
> Pepper flash doesn't work with firefox

There are hacks around that, like FreshPlayerPlugin or Pipelight.

---


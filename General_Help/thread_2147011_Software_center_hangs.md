---
title: "Software center hangs"
date: 2013-05-20
forum: General Help
---

### Post by per engberg on 2013-05-20
After an unsuccessful installation of a unsupported program (remote server for spotify) my software center no longer works. I've updated from 12.04 to 12.10 and then to 13.04, with no change.
This is what i get when trying to start USC:

per@msi-u135:~$ software-center
2013-05-20 19:31:59,166 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-20 19:32:05,093 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-20 19:32:05,100 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-05-20 19:32:05,138 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-05-20 19:32:05,137 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-05-20 19:32:05,803 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

apt-get update reports the following (unhelpful) tip:

.......
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-da_DK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-da
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) raring-updates/universe Translation-da
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) raring/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_raring_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by linuxonbute on 2013-05-20
Have you tried
```


sudo apt-get purge software-center

sudo apt-get install software-center


```

---

### Post by andrew.46 on 2013-05-20
Or perhaps take a step sideways:

```

sudo apt-get install synaptic

```

---

### Post by per engberg on 2013-05-22
Thanks for the tip. Unfortunately this didn't help. Seems like it's time for a fresh install (or start using Synaptic, but I hate to be forced to change by inability to correct an error).

---

### Post by andrew.46 on 2013-05-22
> **per engberg said:**
>  (or start using Synaptic, but I hate to be forced to change by inability to correct an error).

I can see where you are coming from but Synaptic is not such a bad choice, I use it in preference to the Software Centre.

---

### Post by HiImTye on 2013-05-22
give
```
sudo apt-get update; sudo apt-get dist-upgrade -y
``` a try

personally I prefer aptitude to any of the GUI updaters, and knowing dpkg and apt is helpful in case you get any problems down the road

---

### Post by akf-mike-nw2 on 2014-04-09
> **per engberg said:**
> After an unsuccessful installation of a unsupported program (remote server for spotify) my software center no longer works. I've updated from 12.04 to 12.10 and then to 13.04, with no change.
This is what i get when trying to start USC:

per@msi-u135:~$ software-center
2013-05-20 19:31:59,166 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-20 19:32:05,093 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-20 19:32:05,100 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-05-20 19:32:05,138 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-05-20 19:32:05,137 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-05-20 19:32:05,803 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

apt-get update reports the following (unhelpful) tip:

.......
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-da_DK
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-da
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) raring-updates/universe Translation-da
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) raring/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_raring_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

[SIZE=3]**I had an issue where my Software center was freezing and ran across this posting.  I can help first with the last part you mention then will detail the fix I used to get it unfrozen.**[/SIZE]
-----
The last part you list is actually very helpful it appears as though the repos listed do not have a raring entry [sources list tries to auto fill the distro part if not supplied or during a distro upgrade and if the repo does not exist it can not be found.  All you would want to do is open your sources.list file with mousepad gedit nano whatever text editor you prefer and either remove or comment out the lines listed in the error message.  

So from terminal issue
```
gksu mousepad [COLOR=#333333][FONT=UbuntuMono]/etc/apt/sources.list[/FONT][/COLOR]
```
[you can use gksudo gksu works the same and is shorter :-) and instead of mousepad use gedit, nano, whatever you prefer I use xUbuntu and mousepad is default so is what I use].

Now just find the lines listing the repos with issues and either put a # in front of them or delete them
This is how I suggest you do it so you have them for reference if needed later
#Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") raring-security/universe Translation-da_DK
#Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") raring-security/universe Translation-da
#Ign [http://dk.archive.ubuntu.com]("http://dk.archive.ubuntu.com/") raring-updates/universe Translation-da
Reading package lists... Done
and only one of the following
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) raring/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_raring_partner_binary-i386_Packages)

Now just save the file and issue:
```
sudo apt-get update
```
and it should hopefully run through.  Even if not try the next mentioned thing...

For me I would get the Software Center loaded but on install it would just freeze and eventually the this app is taking too long do you wish to terminate it error pops.  Finally today I had time to sit down and I tried **[be sure you CLOSE SOFTWARE CENTER BEFORE THE FOLLOWING]**

```
sudo dpkg-reconfigure software-center
```

it came back stating 2 files in usr/share/app-install/desktop could not be read and would not be included in software center.  HUH, so I went ahead and cd'd over to it and removed both the files [sonic-visualizer and same with layer.desktop] like so:

```
sudo rm -R sonic-visualiser:x-sonicvisualiser.desktop
```[didn't slow down to see if directories or files; if dir -R means recursive and deletes directories out so was easier to just use -R so it wouldn't matter]
  
I then issued the exact same dpkg command again and let it run and this time it came back with no errors listed.  NOW, it seems software center is happier and error free.  

Hope this helps!

---


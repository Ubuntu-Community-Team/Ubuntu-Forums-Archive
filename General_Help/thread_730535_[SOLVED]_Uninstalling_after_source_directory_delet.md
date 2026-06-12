---
title: "[SOLVED] Uninstalling after source directory deleted???"
date: 2008-03-21
forum: General Help
---

### Post by brundlelinux on 2008-03-21
Okay, I know this is THE ultimate bonehead newbie mistake.

I installed an app (Cairo-dock, to be exact) from source.  It worked fine, except I didn't have any of the plugins.  I then found a deb file of the plugins, but since I installed from source, Gdebi didn't recognize that the dependencies were filled.  Well, maybe they weren't, actually.  In any event, what I wanted to do was uninstall Cairo-dock and then reinstall it from the deb file.  I figured that having two instances of it installed, one from deb and one from source would create a nightmarish conflict somewhere.

Like a bonehead, after I initially installed it from source, I trashed the source code folder I had extracted to my desktop.  Then, to compound matters, I used the old Windows mindset of just deleting the folders it installed to and thinking I would then just clean the registry.

Yeah... I'm an idiot.

I've searched the forums and google for help.  In the process, I've learned to ALWAYS use checkinstall from now on when compiling from source, which I knew nothing about before this.  I guess I'm learning the hard way.

So, here's what I actually did.  I deleted the hidden folder in my home directory called .cairo-dock.  I then deleted /usr/local/share/cairo-dock.  Yes, I actually logged out and logged in as root to do that.  I've got just enough ubuntu knowledge to be a danger to myself.  :)

So, I'm now at a point where attempting to install the deb files results in Gdebi telling me that the current version is the same I'm trying to install, and therefore nothing happening.  Synaptic actually list cairo-dock, but tells me the the apps don't actually exist, but are pointed to by other installed dependencies.

So.... uh.... how does one fix this issue without a complete OS reinstall?

---

### Post by zvacet on 2008-03-21
```
sudo apt-get --purge remove **package_name**
```

or 

```
sudo dpkg --remove --force-remove-reinstreq** package_name**
```

** package_name= name of package you want to remove**

---

### Post by justleen on 2008-03-21
do source packages show up in apt Zvacet? thougt they didnt..

what i'd do: ```
locate <program> 
```
find all files from that program. use the name you type to launch it (the executable name)then delete those files.
```
 for files in `locate program`; do rm -rf $files; done 
```
(DO check the output of locate BEFORE deleting!!! )

or, find the files/folders, and delete those
```

cd /
sudo find . -name "program*"

```
```

cd /
sudo find . -name "program*"  -exec rm -rf {} \;

```
again: CHECK the output of the first find!!


rm -rf ruines lives, so make so you only feed it those files you're sure of!

---

### Post by brundlelinux on 2008-03-23
To be honest, I didn't try either of these methods.  I actually just followed the exact same procedure I did for the original install, this time using Checkinstall, and effectively overwrote everything I may have botched the first go round.  I then used Synaptic to remove the app, and everything is perfect.  I'm marking as solved.  Thanks for all the great info guys!  I swear, I've learned my lesson.

---


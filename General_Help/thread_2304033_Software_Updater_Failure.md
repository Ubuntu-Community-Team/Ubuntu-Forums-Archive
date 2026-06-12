---
title: "Software Updater Failure"
date: 2015-11-23
forum: General Help
---

### Post by box02-0 on 2015-11-23
Hi.

I am running:

Ubuntu 14.04 LTS 
   Unity 7.2.6
   using nemo 1.8.4 for file display/organization
   nemo-fileroller 2.6.1 I don't know what this does?? Seems to be needed for Cinnamon desktop which I'm not using.



The Software Updater is failing with the following message: "The installation or removal of a software package failed."

Details of Updates:
Files:
        File manager and graphical shell for Unity (data files)
        File Roller integration for Nemo
        Files
        Translation files for the Cinnamon desktop


I am not sure why this failed. So I tried using Synaptic Package Manger, to upgrade nemo & nemo-fileroller to 2.8 and got the following message:

[I]E: /var/cache/apt/archives/cinnamon-translations_2.8.0-20151023040309-trusty_all.deb: trying to overwrite '/usr/share/locale/ms/LC_MESSAGES/nemo.mo', which is also in package nemo-data 1.8.4-1.1
[/I]

How can I get the Software Updater to work?


Thanks for your help,

M...

---

### Post by matt_symes on 2015-11-23
Hi

> So I tried using Synaptic Package Manger, to upgrade nemo & nemo-fileroller to 2.8 

Did you use the standard repositories or a PPA to upgrade nemo and nemo-fileroller ?

You can force an overwrite using dpkg but you'll want to make sure this is not going to cause you problems so check before you run the command below.

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/cinnamon-translations_2.8.0-20151023040309-trusty_all.deb
```

Kind regards

---

### Post by box02-0 on 2015-11-24
Hi.

I used Ubu Software Centre to initially bring in Nemo 1.8. I then use the standard repositories to upgrade. 


*"....you'll want to make sure this is not going to cause you problems so check before you run the command below."*

How do I make sure this is not going to cause any problems - what do I check for before running the command you suggested?

Thanks for your quick response.

M....

---

### Post by matt_symes on 2015-11-24
Hi

> **box02-0 said:**
> 
Ubuntu 14.04 LTS
Unity 7.2.6
using nemo 1.8.4 for file display/organization
nemo-fileroller 2.6.1 I don't know what this does?? Seems to be needed for Cinnamon desktop which I'm not using.


From your first post, nemo-fileroller is a recommended, not a dependent, package for nemo for archive manipulation. Here's its description.

> Description-en: File Roller integration for Nemo
 Nemo File Roller is an Nemo extension which allows you to create and extract
 archives in Nemo. This extension adds "Extract Here" (for archive files) and
 "Compress..." items to the right-click menu.

It's a plugin for nemo.

> I used Ubu Software Centre to initially bring in Nemo 1.8. I then use the standard repositories to upgrade. 

Did you pull it in from this PPA ?

[https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly)

If so you may not have needed it to fix the original issue. This is a nightly build of cinnamon packages. That's pretty cutting edge and has the potential to break your system at some point. It could very well make a distribution upgrade to 16.04 a real pain.

> How do I make sure this is not going to cause any problems - what do I check for before running the command you suggested?


Looks like the original nemo-data package contains mostly *.mo files and these are translation (language) files so it most likely will not cause you a direct. The rest are icons, bitmaps, svg. The only one that may be a problem is /usr/share/GConf/gsettings/nemo.convert as i don't know what that does. I am assuming there are the same files in the PPA's package of nemo-data so it depends on what the PPA's package contains.

I would run the dpkg command from post #2 as you can always roll back (ppa-purge) if you have problems.

After that run

```
sudo apt-get -f install
```

Kind regards

---


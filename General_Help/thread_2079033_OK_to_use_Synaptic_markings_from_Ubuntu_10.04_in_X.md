---
title: "OK to use Synaptic markings from Ubuntu 10.04 in Xubuntu 12.04 install?  Problems?"
date: 2012-11-01
forum: General Help
---

### Post by mikodo on 2012-11-01
Hi,

I hope this is alright to do. 

I posted a question a few days ago about backing backing up Synaptic Markings and the bringing them forward in a new install, over at askubuntu.com, because I had read about doing it in one of their threads, that came up from doing a google search. My first ever question there. I received no responses.  :(

Can I link [this post]("http://askubuntu.com/questions/208244/ill-there-be-problems-using-synaptic-in-ubuntu-10-04-to-save-markings-to-backup") from there to here, to ask the same question?

Edit:

I am wondering things like:

1. I may be bringing forward older packages, to my new install, that I might not necessarily want the older version of.

2. I am looking forward to a clean install of Xubuntu 12.04, to clean things up for me, and give me a fresh Xubuntu experience, and I am wondering if this might, "muddy the waters", so to speak.

3. Some of the apps and their dependencies, may not want to play nice with Xubuntu 12.04.

Stuff like that ...

I'm off to bed. I can't keep my eyes open anymore.  ;-)

Thanks.

---

### Post by ibjsb4 on 2012-11-01
I have not done a U to X markings, but the repositories I think are the same.  Would seem to me that you risk bloating your new install.
 
I have used markings in the pass and found that discrepancies will be rejected.  Not doing any real damage, but leaves you with some clean-up afterwards.  Some people use scripts that just reinstalls app's and configurations.  I don't have any links handy for scripts, but you could take a look here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by dannyboy79 on 2012-11-01
i think using synaptic markings only works when applying it to the same version, like if you had another machine you wanted the same packages installed on, you could use that.

however, if you want a list of all currently installed packages (but it doesn't list the "version") you could use a command like this
```
dpkg –get-selections > installed-packages.txt
```
that will output the dpkg –get-selections command into a text file called installed-packages.txt which will be stored in the current directory you ran the command from.

then at least you know what you all have installed and can search for and install those packages in the new 12.04 system. I think people have created custom scripts that do this but I would be leary about running it and would feel more comfortable just searching synaptic per individual program to reinstall it.

ANother note, your Update Manager should be able to upgrade you from 10.04 to 12.04 however your results may vary.

Good luck

---

### Post by mikodo on 2012-11-01
@ ibjsb4 and dannyboy79!

I'll stay away from using Synaptic markings then, for forwarding apps to a new version/flavor.

I'm looking into searching for "backup installed packages" and "dpkg --help" for an alternative for doing this.

Thanks.

---

### Post by mikodo on 2012-11-01
Alright.

This is what I tried and am going to use by backing up, before installing a new drive and installing Xubuntu 12.04. 

```
cd ~/Documents
``````
dpkg --get-selections > installed-packages.txt

```It will be a bit of work in the new install, installing the apps, but as pointed out earlier, I will have the option to only install the *newer apps and dependencies*, I want.

Thanks.

---


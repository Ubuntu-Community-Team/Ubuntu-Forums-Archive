---
title: "downgrade libc6"
date: 2008-05-26
forum: General Help
---

### Post by conartist6 on 2008-05-26
Ok. So this is all my house. But I'm learning by doing with Ubuntu and it was only going to be so long until I made a mistake, which I did. I was trying to install the newest test release of Audacious (shouldn't be that hard should it?) from source, and sifting through the dependencies (I forget if it was on packages.ubuntu.org or packages.debian.org... That was probably my first mistake). Anyway, I finally tried installing libmcs-dev and it told me that I needed a newer version of libc6. So I downloaded a deb of libc6 and installed it. It broke. I got errors from apt about packages having broken dependancies. So I started synaptic, and asked it to fix broken dependancies (it found libc6-dev and libc6-i386 to be broken). It removed a shatload of packages in order to get to those, and then failed while trying to reinstall them because it expected and older version of libc6. So now I'm stuck. I guess I need to either downgrade libc6 and fix everything that synaptic broke, or I need to install newer versions of libc6-dev and libc6-i386 than synaptic wants me to. WHAT DO I DO? I would sincerely like not to have to reinstall my OS, but if thats what it is then so be it, but i'd like to hear my options for tinkering first. I have nothing to lost. Thanks in advance for your help.

---

### Post by Anduu on 2008-05-27
If you modified your /etc/apt/sources.list at all remove any third party repositories.

Open a terminal and enter ```
sudo apt-get -f install
```It may be able to sort things out for you.

If not please post any output it gives.

---

### Post by zvacet on 2008-05-27
```
sudo aptitude forbid-version packagename
```
[B]
packagename = new version  of libc6[/B]

---

### Post by conartist6 on 2008-05-27
Here is a copy of the specific error I am getting from Synaptic while trying to mark libc6-dev for installation:
libc6-dev:
  Depends:libc6 (=2.6.1-1ubunu10) but 2.7-5ubuntu2 is to be installed

So there's the version discrepancy. Anyway, apt-get -f is normal, as right now I have no broken dependencies (just missing libc6-dev and everything else that used to depend on it). What would forbid-version do? It sounds like that would just prevent me from downloading that new version automatically should I know beforehand that it was broken. I suppose its possible that that would force synaptic to try to downgrade, but I have a deep suspicion that apt will be useless here because, as with Synaptic, it will want to remove every package from the system in order to get to libc6. That makes me think I need to do this manually (from a live CD?) and just write the package over and either let the system work the new version out for itself or also change whatever records it keeps of what packages are installed. Is this correct? Anybody? Help!!?

---

### Post by ibuclaw on 2008-05-27
Sounds like you need a good pinning of packages before you try anything else.

Open up a terminal and type these commands in:
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
Then open up one of the preferences files in gedit
```
sudo gedit /etc/apt/preferences
```

And paste this in:
```

Package: *
Pin: release a=hardy
Pin-Priority: 1001

```
Save the file and close.

Then run
```
sudo apt-get upgrade -f
```

Once your system has downgraded. Reopen your preferences file.
```
sudo gedit /etc/apt/preferences
```
And remove what you put in.

[EDIT]
Or, if your like me and prefer security over everything else, paste this over the previous pin above:
```

Package: *
Pin: release a=hardy-security
Pin-Priority: 1001

Package: *
Pin: release a=hardy-updates
Pin-Priority: 900

Package: *
Pin: release a=hardy
Pin-Priority: 800

```
And re-upgrade to (hopefully) a nice and stable system again.

Regards
Iain

---


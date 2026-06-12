---
title: "Updating Brave on Ubuntu"
date: 2022-01-18
forum: General Help
---

### Post by Daveski17 on 2022-01-18
According to *About Brave* I'm running Version 1.34.80 Chromium: 97.0.4692.71 (Official Build) (64-bit).

[ATTACH=CONFIG]289842[/ATTACH]

However *Safety Check Updates*  shows Version 97.1.34.80 (Official Build) (64-bit). Is there a Terminal Command for just updating the Brave browser?

---

### Post by GhX6GZMB on 2022-01-18
I'm running the same.
Dunno how you got that message, but it's to my mind irrelevant.

---

### Post by Daveski17 on 2022-01-18
> **ml9104 said:**
> I'm running the same.
If you've installed using the PPA, the next sudo update/upgrade round should change this.

I installed using this: [https://brave.com/linux/#linux](https://brave.com/linux/#linux)

I didn't think I needed to add the PPA.

---

### Post by GhX6GZMB on 2022-01-18
> **Daveski17 said:**
> I installed using this: [https://brave.com/linux/#linux](https://brave.com/linux/#linux)

I didn't think I needed to add the PPA.

Well, if you followed and did what's in the first section, you've added a PPA. All is well. If you're uncertain, run:

```
apt policy
```
You should see "brave-browser" somewhere in the list.

---

### Post by Daveski17 on 2022-01-18
> **ml9104 said:**
> Well, if you followed and did what's in the first section, you've added a PPA. All is well. If you're uncertain, run:

```
apt policy
```
You should see "brave-browser" somewhere in the list.

[ATTACH=CONFIG]289843[/ATTACH]

There's this.

[ATTACH=CONFIG]289844[/ATTACH]

But I don't see a Brave PPA here.

---

### Post by Daveski17 on 2022-01-18
> **ml9104 said:**
> Dunno how you got that message, but it's to my mind irrelevant.

I think you're probably right.

[ATTACH=CONFIG]289845[/ATTACH]

My MacBook shows it's up to date but it's more or less the same version number (Version 1.34.80 Chromium: 97.0.4692.71 (Official Build) (arm64)) as my Ubuntu laptop.

---

### Post by DuckHook on 2022-01-19
You are good to go.

Technically, you did not add a PPA. You added an external repository. The real world effect is the same, but the sources are different. This is a rather nitpicking point, but one worth making, just for clarity.

[LIST]
[*]PPAs are a part of Canonical's ecosystem. They are a hodge-podge of contributions from everywhere. They range from the unvetted, unaudited and unknown to the very dependable, maintained by teams of official developers that some organizations dedicate to the task. The Firefox PPAs are such examples. But since just about anyone can join Launchpad and create a PPA, they also encompass dead stuff that their originators haven't touched for years. Moreover, because they are not vetted or audited, they can harbour malware. But because they are part of Canonical's ecosystem, they use Canonical's GPG keys, which means they can be added to your sources easily—with a one line command.
[*]Outside repos do not enjoy the advantage of belonging to Canonical's ecosystem. That's why you had to go through all that rigmarole with Brave—first downloading their GPG key, then adding it to your keyring, etc.
[/LIST]
You are relatively new to Ubuntu, so I will state it again: do not go adding PPAs or outside repos willy&#8209;nilly. It's a bad Windows habit that all too many Windows users drag into Linux. The Brave external repo is fine. The Firefox PPAs are fine. A few more like VirtualBox, WINE, Libreoffice. etc are dependable too. But a depressingly large proportion are unmaintained, dead and insecure.

Re: Brave

Once the repo has been added, don't sweat about the version. It is now up to the Brave repo maintainers to keep their version reasonably current. Your role is to keep updated using your usual update tools.

---

### Post by Daveski17 on 2022-01-19
> **DuckHook said:**
> You are good to go.

Technically, you did not add a PPA. You added an external repository. The real world effect is the same, but the sources are different. This is a rather nitpicking point, but one worth making, just for clarity.

[LIST]
[*]PPAs are a part of Canonical's ecosystem. They are a hodge-podge of contributions from everywhere. They range from the unvetted, unaudited and unknown to the very dependable, maintained by teams of official developers that some organizations dedicate to the task. The Firefox PPAs are such examples. But since just about anyone can join Launchpad and create a PPA, they also encompass dead stuff that their originators haven't touched for years. Moreover, because they are not vetted or audited, they can harbour malware. But because they are part of Canonical's ecosystem, they use Canonical's GPG keys, which means they can be added to your sources easily—with a one line command.
[*]Outside repos do not enjoy the advantage of belonging to Canonical's ecosystem. That's why you had to go through all that rigmarole with Brave—first downloading their GPG key, then adding it to your keyring, etc.
[/LIST]
You are relatively new to Ubuntu, so I will state it again: do not go adding PPAs or outside repos willy&#8209;nilly. It's a bad Windows habit that all too many Windows users drag into Linux. The Brave external repo is fine. The Firefox PPAs are fine. A few more like VirtualBox, WINE, Libreoffice. etc are dependable too. But a depressingly large proportion are unmaintained, dead and insecure.

Re: Brave

Once the repo has been added, don't sweat about the version. It is now up to the Brave repo maintainers to keep their version reasonably current. Your role is to keep updated using your usual update tools.

OK thanks. That's helped a lot. I have to admit that I've been running Ubuntu consistently for about seven years. It's just that I've never needed to get really anorak with it until recently. The only PPA's I have are Vivaldi, Chrome, Stellarium and Cartes du Ciel.

---

### Post by GhX6GZMB on 2022-01-19
@DuckHook, Thanks for the valuable clarification

> **Daveski17 said:**
> 
But I don't see a Brave PPA here.

You did NOT run apt policy!
Instead you relied on the Software & Updates.

Running an apt command means opening a terminal and typing in the command  and executing it.

This is the output on my machine. You'll see Brave around 1/3 down:

```
macro@macro-pc:~$ apt policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-ubuntuhandbook1-avidemux,a=focal,n=focal,l=Avidemux,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-ubuntuhandbook1-avidemux,a=focal,n=focal,l=Avidemux,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-libreoffice,a=focal,n=focal,l=LibreOffice Fresh,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-libreoffice,a=focal,n=focal,l=LibreOffice Fresh,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-kicad-kicad-5.1-releases,a=focal,n=focal,l=PPA for KiCad: 5.1 releases,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-kicad-kicad-5.1-releases,a=focal,n=focal,l=PPA for KiCad: 5.1 releases,c=main,b=amd64
     origin ppa.launchpad.net
 500 https://brave-browser-apt-release.s3.brave.com stable/main amd64 Packages
     release o=Brave Software,a=stable,n=stable,l=Brave Browser,c=main,b=amd64
     origin brave-browser-apt-release.s3.brave.com
 500 http://archive.canonical.com/ubuntu focal/partner amd64 Packages
     release v=20.04,o=Canonical,a=focal,n=focal,l=Partner archive,c=partner,b=amd64
     origin archive.canonical.com
 500 http://archive.ubuntu.com/ubuntu focal-security/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
Pinned packages:
macro@macro-pc:~$

```

---

### Post by Daveski17 on 2022-01-19
> **ml9104 said:**
> @DuckHook, Thanks for the valuable clarification



You did NOT run apt policy!
Instead you relied on the Software & Updates.

Running an apt command means opening a terminal and typing in the command  and executing it.

This is the output on my machine. You'll see Brave around 1/3 down:

```
macro@macro-pc:~$ apt policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-ubuntuhandbook1-avidemux,a=focal,n=focal,l=Avidemux,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-ubuntuhandbook1-avidemux,a=focal,n=focal,l=Avidemux,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-libreoffice,a=focal,n=focal,l=LibreOffice Fresh,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-libreoffice,a=focal,n=focal,l=LibreOffice Fresh,c=main,b=amd64
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal/main i386 Packages
     release v=20.04,o=LP-PPA-kicad-kicad-5.1-releases,a=focal,n=focal,l=PPA for KiCad: 5.1 releases,c=main,b=i386
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal/main amd64 Packages
     release v=20.04,o=LP-PPA-kicad-kicad-5.1-releases,a=focal,n=focal,l=PPA for KiCad: 5.1 releases,c=main,b=amd64
     origin ppa.launchpad.net
 500 https://brave-browser-apt-release.s3.brave.com stable/main amd64 Packages
     release o=Brave Software,a=stable,n=stable,l=Brave Browser,c=main,b=amd64
     origin brave-browser-apt-release.s3.brave.com
 500 http://archive.canonical.com/ubuntu focal/partner amd64 Packages
     release v=20.04,o=Canonical,a=focal,n=focal,l=Partner archive,c=partner,b=amd64
     origin archive.canonical.com
 500 http://archive.ubuntu.com/ubuntu focal-security/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-security,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal-updates,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/main i386 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=i386
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
     release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
Pinned packages:
macro@macro-pc:~$

```

I did run apt policy! I even took a small screenshot with Ksnip and posted it. I know how to use the Terminal. I'm not an anorak, but I'm not a total wazzock either.

---

### Post by Daveski17 on 2022-01-21
The wazzock rules!

[ATTACH=CONFIG]289866[/ATTACH]

I'm happier now I know it updates.

[ATTACH=CONFIG]289867[/ATTACH]

---

### Post by DuckHook on 2022-01-21
Congrats. You'll find that Brave updates about once a month—more frequently if they feel a security issue needs patching. They keep on top of things.

For another perspective on the comparative benefits of Brave, you may want to look at this concurrent thread: [https://ubuntuforums.org/showthread.php?t=2470950&p=14076290#post14076290](https://ubuntuforums.org/showthread.php?t=2470950&p=14076290#post14076290)

One more note on outside repos/PPAs and then I think I'll stop beating this very, very dead horse:

You may wish to consider confining such apps to a VM or a container wherever possible. That way, if they turn out to be nasty, they are at least reasonably sandboxed.

---

### Post by Daveski17 on 2022-01-22
> **DuckHook said:**
> Congrats. You'll find that Brave updates about once a month—more frequently if they feel a security issue needs patching. They keep on top of things.

For another perspective on the comparative benefits of Brave, you may want to look at this concurrent thread: [https://ubuntuforums.org/showthread.php?t=2470950&p=14076290#post14076290](https://ubuntuforums.org/showthread.php?t=2470950&p=14076290#post14076290)

One more note on outside repos/PPAs and then I think I'll stop beating this very, very dead horse:

You may wish to consider confining such apps to a VM or a container wherever possible. That way, if they turn out to be nasty, they are at least reasonably sandboxed.

Thanks, it was a relief to know it will update. Thanks for the link. All I need now is a way of opening Brave without the authentication notice pop-up.

[ATTACH=CONFIG]289868[/ATTACH]

---

### Post by DuckHook on 2022-01-22
Do you have automatic login turned on? If so, it's not at all a good habit and a reinforcement of bad habits.

With automatic login, the operating system has no chance to check if you are the real user or an imposter. Since Brave is a "security" browser, it's default is to run only for the intended user, hence the challenge/response requirement.

---

### Post by Daveski17 on 2022-01-22
> **DuckHook said:**
> Do you have automatic login turned on? If so, it's not at all a good habit and a reinforcement of bad habits.

With automatic login, the operating system has no chance to check if you are the real user or an imposter. Since Brave is a "security" browser, it's default is to run only for the intended user, hence the challenge/response requirement.

Yes I use auto login. Opera and Firefox open without it though. Chrome based browsers seem to need authentication. I don't run the Opera snap now, but I did. I liked the fact that I didn't have to authenticate it. So I definitely can't turn it off for Brave?

---

### Post by DuckHook on 2022-01-22
> **Daveski17 said:**
> I definitely can't turn it off for Brave?
In Linux, anything is possible, but the solutions involve disabling your keyring.

You will have to look to someone else for help with that.

It's a personal thing, but I refuse to give advice that cripples Linux security. I consider security scofflaws to be a threat to the larger Linux ecosystem and will not enable them.

Good Luck and Happy Ubunti-ing.
DH

---

### Post by deadflowr on 2022-01-22
Chromium based browsers, like Brave, offer to save passwords; which are then saved to your local keyring.
As such the default action makes the browser need those unlocked.
I think you should be able to stop it by turning off "Offer to save passwords" in Brave.
Should be in Settings > Advanced or Additional Settings > Autofill > Passwords.

I also think if you have any saved passwords already you will need to delete those.
(assuming you use a password manager like keepassx, or you use something else)

Also double check in the Passwords and Keys program in Ubuntu if you have any passwords entries for brave, chrome, or chromium, and delete those there.

I'm not sure if it helps, but worth a look.

If that doesn't work, still do the above but also switch the password option from the keyring to basic like so
```
cp /usr/share/applications/brave.desktop ~/.local/share/applications
gedit ~/.local/share/applications/brave.desktop
```
change the Exec line and add --password-store=basic
like
```
Exec=brave --password-store=basic %U
```
or however the Exec line reads. And save it.

(Hint: If the desktop file is different or somewhere else you can find the correct name and location with dpkg listing like
```
dkpg -L brave | grep desktop
```

Note that you do the cp/copy of the file from the /usr directory to your .own local directory because the /usr directory can and will be overwritten by any updates that come.
But files in your .local directory will not be overwritten so the changes you make will stay indefinitely.

If you have the launcher in your dock, remove it and re-add it, as the dock would still be using the original.
Removing and replacing should reset it to use the new/edited launcher.


Hope some of this makes sense.
Or works
or something

---

### Post by Daveski17 on 2022-01-22
> **DuckHook said:**
> In Linux, anything is possible, but the solutions involve disabling your keyring.

You will have to look to someone else for help with that.

It's a personal thing, but I refuse to give advice that cripples Linux security. I consider security scofflaws to be a threat to the larger Linux ecosystem and will not enable them.

Good Luck and Happy Ubunti-ing.
DH

OK thanks, I respect your position on security. I am pretty security conscious though and use a bit of browser hardening on Firefox. Security was a big factor in my ditching Windows. My laptop never leaves the house, if it ever did I'd disable the auto-login. I'd just like to open the laptop lid and open Brave as I open Firefox.

---

### Post by Daveski17 on 2022-01-22
> **deadflowr said:**
> Chromium based browsers, like Brave, offer to save passwords; which are then saved to your local keyring.
As such the default action makes the browser need those unlocked.
I think you should be able to stop it by turning off "Offer to save passwords" in Brave.
Should be in Settings > Advanced or Additional Settings > Autofill > Passwords.

I also think if you have any saved passwords already you will need to delete those.
(assuming you use a password manager like keepassx, or you use something else)

Also double check in the Passwords and Keys program in Ubuntu if you have any passwords entries for brave, chrome, or chromium, and delete those there.

I'm not sure if it helps, but worth a look.

If that doesn't work, still do the above but also switch the password option from the keyring to basic like so
```
cp /usr/share/applications/brave.desktop ~/.local/share/applications
gedit ~/.local/share/applications/brave.desktop
```
change the Exec line and add --password-store=basic
like
```
Exec=brave --password-store=basic %U
```
or however the Exec line reads. And save it.

(Hint: If the desktop file is different or somewhere else you can find the correct name and location with dpkg listing like
```
dkpg -L brave | grep desktop
```

Note that you do the cp/copy of the file from the /usr directory to your .own local directory because the /usr directory can and will be overwritten by any updates that come.
But files in your .local directory will not be overwritten so the changes you make will stay indefinitely.

If you have the launcher in your dock, remove it and re-add it, as the dock would still be using the original.
Removing and replacing should reset it to use the new/edited launcher.


Hope some of this makes sense.
Or works
or something

OK thanks. I'll have to do more research I think. I'll probably find a way. You could have just said that you don't want to tell me because (insert explanation of your choice). What I don't understand is that Opera has the same rendering engine as Vivaldi, Chrome and Brave, yet it could log-in without the keyring. Might end up just using my MacBook at this rate lol. 

> **deadflowr said:**
> I think you should be able to stop it by turning off "Offer to save passwords" in Brave.
Should be in Settings > Advanced or Additional Settings > Autofill > Passwords.

Surely this only applies to the browser itself. I just think having a keyring prompt for other browsers than Firefox and Opera is a bit pointless.

---

### Post by deadflowr on 2022-01-22
Opera does the same thing, but if installed from Ubuntu's Software Store, it would default be the snap version, which i do not know if that even has access to the keyring.

---

### Post by Daveski17 on 2022-01-22
> **deadflowr said:**
> Opera does the same thing, but if installed from Ubuntu's Software Store, it would default be the snap version, which i do not know if that even has access to the keyring.


Yes, it was the snap Opera. To say it was a little buggy would be an understatement. I could brew and drink a cup of Earl Grey while I was waiting for it to open, let alone video rendering issues. Which is why I'm a little concerned about the upcoming snap Firefox version. After seven years of running Ubuntu I'm seriously considering a different distro.

---

### Post by Daveski17 on 2022-01-22
I figured it out anyway!

---


---
title: "Uninstalled web browser, and now desktop is gone"
date: 2015-08-26
forum: General Help
---

### Post by elvis6 on 2015-08-26
I have Xubuntu, and I was having strange web browser issues and could not find a solution, so as a last resort, I decided to uninstall the 2 browsers, and planned to re-install them, using the Software Center.
After uninstalling, I restarted, and when I logged in my password to the system, I get this error pop-up that says ": unable to launch "startxfce4" X session --- "startxfce4" not found; falling back to default session"

The only option is to press "okay", but after pressing it, everything on my desktop is completely gone. It's just the Wallpaper, with no icons or anything.
Is there some way I can go into recover mode, or root shell, and type a command that will repair the desktop, without re-installing the whole OS, and losing files ?

---

### Post by CantankRus on 2015-08-26
Which 2 browsers did you uninstall?
So if I understand you can boot to the login screen but when you login you get the error?

---

### Post by TheFu on 2015-08-26
Any chance you've been using sudo with any GUI programs?  Bad idea.  Create a new userid and login using that. If everything is fine under the new userid, it is specific to the other, not-so-good userid and the system is fine.

**Update:** Reading the other responses, it is clear I missed the more critical part of the OP. startxfce is missing. That is desktop related.  Sounds like the xubuntu-desktop meta-package was broken by removing those programs, but I do not know for certain.  Because of the way Software Center hides things, it could be that by removing all the browsers, other dependencies were removed too - but to be clear I don't know if any of this is true or not.

Probably unrelated, but ... for creating other userids, I setup openssh so it is easy to remote into every system from another machine and use shell tools to accomplish administrative tasks - like creating new userids. useradd or adduser - don't remember which one does the most helpful parts. I always have to check the manpages to be sure which to use.

---

### Post by elvis6 on 2015-08-26
> **CantankRus said:**
> Which 2 browsers did you uninstall?

Firefox, and this generic program just called "Web Browser".

The "Web Browser" icon in the Software Center, is actually the same exact icon on the desktop which I (used to) click to open Firefox, so the 2 programs are somehow related, if that makes sense.

> **CantankRus said:**
> So if I understand you can boot to the login screen but when you login you get the error?

Yes, correct

---

### Post by CantankRus on 2015-08-26
At the login screen hit ctrl+alt+F1
Login and the run ...
```
sudo apt-get install xubuntu-desktop
```

When completed type in "logout" and then press ctrl+alt+F7
to take you back to the greeter and try login again.

---

### Post by elvis6 on 2015-08-26
> **TheFu said:**
> Any chance you've been using sudo with any GUI programs?  Bad idea.  Create a new userid and login using that. If everything is fine under the new userid, it is specific to the other, not-so-good userid and the system is fine.

I don't see an option on the login screen to add a user.
There's the Guest Login. But when I choose that, I have the same issues as my main login.
Then below that, there's "Other". When I click on Other, a box appears below that saying "login". But it does not sound like an option to create a new user id.

Or is it done through the recovery mode ?

---

### Post by sudodus on 2015-08-26
I think the problem is that you removed 'this generic program just called "Web Browser"'. It was some kind of infrastructure that should help you point to your favourite web browser. If you know the name (as a command line program), maybe you can install it again. Try with the hotkey combination

***ctrl + alt + F1***

and run a text screen, where you can run apt-get to update and install programs

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xubuntu-desktop
sudo apt-get install firefox  # or another browser that you might prefer
```

If you are lucky, the commands above will restore 'this generic program just called "Web Browser"'. It might happen if it is part of a meta-package that is still there in your system (or of xubuntu-desktop as suggested by CantankRus).

---

### Post by elvis6 on 2015-08-26
> **CantankRus said:**
> At the login screen hit ctrl+alt+F1
Login and the run ...
```
sudo apt-get install xubuntu-desktop
```

When completed type in "logout" and then press ctrl+alt+F7
to take you back to the greeter and try login again.

I followed these steps and it appeared to do an update process and finish it.
But by the time I got back to the main login, and signed in, I had the same problem with my desktop.
I do remember a message at the end of the update, saying something about some files could not be updated, but I don't remember the exact wording

---

### Post by CantankRus on 2015-08-26
go back to ctrl+alt+F1 and run sudodus's commands in post#7.
Firefox should be installed as a recommended dependency of xubuntu-desktop.
Need the error messages to know how to fix.

---

### Post by sudodus on 2015-08-26
Try according to the tips in the following list of commands originally posted by *oldfred* and with added tips from *zika* and *2F4U*

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

# added 2F4U's tips for Package Manager & Update Manager problems

Does executing these commands help?

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

http://ubuntuforums.org/showthread.php?t=1869890

```

---

### Post by elvis6 on 2015-08-26
Just realized why the update did not work for me.
I noticed that I inadvertently removed my Wireless Adaptor from that particular PC, so of course without the internet connection, I failed to get the proper update during that command.
So, I plugged my Wifi adaptor back in, and retyped the commands, and it worked just fine, as I am back in business wtih my desktop.
Thanks to all of you for you kind, quick helpfulness, and the very simple and easy to understand instructions you provided.

---

### Post by sudodus on 2015-08-26
You are welcome :-)

---

### Post by monkeybrain20122 on 2015-08-26
On ubuntu proper removing the "generic web browser" appears to remove a whole bunch of stuffs (14.04) (including unity)
```

$ sudo apt-get remove webbrowser-app 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  bamfdaemon libunity-webapps0 ubuntu-desktop unity unity-webapps-common
  unity-webapps-gmail unity-webapps-googlecalendar unity-webapps-googledocs
  unity-webapps-googleplus unity-webapps-launchpad unity-webapps-service
  unity-webapps-youtube webapp-container webbrowser-app xul-ext-unity
  xul-ext-websites-integration
0 to upgrade, 0 to newly install, 16 to remove and 125 not to upgrade.
After this operation, 10.5 MB disk space will be freed.
Do you want to continue? [Y/n] n 
```

Not sure about xubuntu

[http://discourse.ubuntu.com/t/theres-a-ubuntu-browser-in-trusty/1594/3](http://discourse.ubuntu.com/t/theres-a-ubuntu-browser-in-trusty/1594/3)

Edited: glad that you fixed your problem. Next time be careful what you remove when uninstalling something.

---


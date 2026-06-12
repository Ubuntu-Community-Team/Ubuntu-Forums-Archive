---
title: "Update &amp; Installation Problems"
date: 2007-10-23
forum: General Help
---

### Post by Salazar420 on 2007-10-23
So, here's the scenario:

I recently attempted to install festival, and one library or dependency or whatever (excuse my ignorance), failed, but I did manage to fix this problem. Since installing, however, there has been several updates available; I'll list them:

> (Important Security Updates)
bsdutils
firefox
firefox-gnome-support
libnspr4
libnss3
libssl0.9.8
mount
openssl
util-linux
util-linux-locales

(Recommended Updates)
tzdata

When I attempt to run the updates the update manager fails to do so, and under the details, it fails just after preconfiguring. When I run "sudo apt-get update" everything seems to work, and the update manager's orange icon on the panel disappears momentarily. I get this output:

> xenouser@XeNoCoMp:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
xenouser@XeNoCoMp:~$ 

However, when I run "sudo apt-get upgrade" the orange update-manager icon returns, and I get this output:

> xenouser@XeNoCoMp:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bsdutils firefox firefox-gnome-support libnspr4 libnss3 libssl0.9.8 mount
  openssl tzdata util-linux util-linux-locales
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.1MB of archives.
After unpacking, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 3085 package `libopal-2.2.0':
 field name `Ori#inal-Maantainer2' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

Watch what happens when I try to install the mozilla-thunderbird package via apt-get:

> xenouser@XeNoCoMp:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector
  mozilla-thunderbird-enigmail
The following NEW packages will be installed:
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B/10.9MB of archives.
After unpacking, 30.5MB of additional disk space will be used.
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 3085 package `libopal-2.2.0':
 field name `Ori#inal-Maantainer2' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

My first suspicion is that there is a problem with dpkg, but what do I know. Any help will be much appreciated. A thanks in advance.

---

### Post by ihcnet on 2007-10-23
Try running ```
sudo apt-get install -f
```

---

### Post by Salazar420 on 2007-10-23
Have done so and, in doing so, have yielded said results, but no improvements.

> xenouser@XeNoCoMp:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Thanks for the suggestion though.

---

### Post by ihcnet on 2007-10-23
Try ```
sudo dpkg --configure -a
``` if that doesn't work, try ```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by Salazar420 on 2007-10-23
> **ihcnet said:**
> Try ```
sudo dpkg --configure -a
``` if that doesn't work, try ```
sudo dpkg --clear-avail && sudo apt-get update
```

It's odd how Ubuntu -- for me, at least -- has a way of creating errors, and then later fixing them all on its own. Thanks for the advice; it might have worked if I'd gotten around to trying it. Anyway, the issue is resolved... frustratingly, because I didn't learn much... lol. It just fixed... odd... truly odd.

---

### Post by Burekarna on 2007-10-23
i have a big problem. First of all i would like to apologise for my English.
Anyway, I made an apt-get update and apt-get upgrade and it offers me some packages to upgrade and I confirmed it to do so. After that I restarted the computer and everything was different. Windows are not the same as they were before (my Compiz is still running and windows are wobbly and window borders are the same as before, but the inside it isn't (place where File, Edit etc. is)).
Second problem is that Terminal is not working any more. I want to run it and i can see it says Starting Terminal (down in the menu) but then it closes.
And the third problem is that a lot of the Icons have dissapear. When I click on CompizConfig Settings Manager or somewhere else I don't see icons any more.
I apologize for my English but if someone understand me please help me. I would only like my Terminal to start working again, other problems are not so important.
Packages I've installed thru apt-get were:
```

bsdutils
firefox
firefox-gnome-support
libnspr4
libnss3
libssl0.9.8
mount
openssl
util-linux
util-linux-locales
```
Please help, I'm new guy in linux and without terminal i'm nothing.
Thank you very much!

---


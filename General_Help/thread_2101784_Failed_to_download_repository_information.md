---
title: "Failed to download repository information"
date: 2013-01-05
forum: General Help
---

### Post by rapattack1 on 2013-01-05
HI i just upgraded Artistx and now i have this update-manager problem. Not sure what to do

---

### Post by ibjsb4 on 2013-01-05
Would you post the errors from:

```
sudo apt-get update
```

Just easier to work with than .xcf

---

### Post by rapattack1 on 2013-01-06
```
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 360101A8590E1537
W: Failed to fetch http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Hope i copied the right info

---

### Post by ibjsb4 on 2013-01-06
I am not finding any precise ppa for these.

[https://launchpad.net/~fluxus-maintainers/+archive/stable?field.series_filter=](https://launchpad.net/~fluxus-maintainers/+archive/stable?field.series_filter=)

[http://www.ubuntuupdates.org/ppa/mozilla_team_thunderbird_stable](http://www.ubuntuupdates.org/ppa/mozilla_team_thunderbird_stable)

You need to remove or just uncheck them in you software sources and then update.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by rapattack1 on 2013-01-09
So i uncheck the ones with the 404 error?

---

### Post by oleink on 2013-01-09
> **rapattack1 said:**
> So i uncheck the ones with the 404 error?

There are a few ways to fix it but here is a quick simple gui based tutorial for you [http://www.liberiangeek.net/2012/04/fix-duplicate-sources-list-entry-errors-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/04/fix-duplicate-sources-list-entry-errors-in-ubuntu-12-04-precise-pangolin/")

---

### Post by ibjsb4 on 2013-01-09
> **rapattack1 said:**
> So i uncheck the ones with the 404 error?

Yes  :)

---

### Post by rapattack1 on 2013-01-09
OK the other day the error symbol that was on the top of the desktop dissapeared and when i unchecked those items and reloaded synaptic i got this 
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 360101A8590E1537Failed to fetch [http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-01-09
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net)  precise Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 360101A8590E1537

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en)
------------------------------------------------------------------------------------------------
Failed to fetch [http://ppa.launchpad.net/fluxus-main...source/Sources]("http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/source/Sources")  404  Not Found

Uncheck "Source code" in software sources to fix that.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)
-------------------------------------------------------------------------------------------------
Failed to fetch [http://ppa.launchpad.net/fluxus-main...-i386/Packages]("http://ppa.launchpad.net/fluxus-maintainers/stable/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found

You must of missed this one in software sources or it not showing up there.  If you can't find it in "Other Software"

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Then

```
gksudo gedit /etc/apt/sources.list.d/*
```

And put a hash mark (#) in front of all "fluxus" entries.

#[http://ppa.launchpad.net/fluxus-main](http://ppa.launchpad.net/fluxus-main)...

---

### Post by rapattack1 on 2013-01-10
Ok the first part i don't understand sorry. 

Source code is unchecked already in synaptic.

Ok there were four entries for fluxus and i only unchecked 2 so now all four are unchecked thanks.

Thanks there was only one fluxus entry in that list that didn't have a hash so its done now.

---

### Post by rapattack1 on 2013-01-15
That error red triagle thing is not showing now so somehow things might have got corrected....not sure will give it a few more days

---

### Post by rapattack1 on 2013-02-07
No longer using this distro(artistx) as too many problems

---


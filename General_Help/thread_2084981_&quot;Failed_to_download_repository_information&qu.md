---
title: "&quot;Failed to download repository information&quot;"
date: 2012-11-17
forum: General Help
---

### Post by louisgonick on 2012-11-17
Greetings, 

As I attempted to install some updates, I received this popup: 

"Failed to download repository information

Check your Internet connection."

And this:
"W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

If anybody has any clue on how to fix this, I'll be very thankful.

Any suggestion is appreciated.I am currently running  12.04

---

### Post by claracc on 2012-11-17
> **louisgonick said:**
> Greetings, 

As I attempted to install some updates, I received this popup: 

"Failed to download repository information

Check your Internet connection."

And this:
"W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

If anybody has any clue on how to fix this, I'll be very thankful.

Any suggestion is appreciated.I am currently running  12.04

The error reported is that "The requested URL /elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources was not found on this server.", so the repositories addressed are not in the server you download updates.

You can do:

Disable these two repositories in software sources in order to get the security updates.

Or you can try to change server from which you download updates in order to see if this other server has the two repositories.

what for are these two repositories?

---

### Post by ranger1021994 on 2012-11-17
> **louisgonick said:**
> Greetings, 

As I attempted to install some updates, I received this popup: 

"Failed to download repository information

Check your Internet connection."

And this:
"W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

If anybody has any clue on how to fix this, I'll be very thankful.

Any suggestion is appreciated.I am currently running  12.04

The PPA which you are trying to add has no version for 12.04
It means that you cannot download from this PPA as it does not have packages for 12.04(precise)

You should delete these PPAs

---


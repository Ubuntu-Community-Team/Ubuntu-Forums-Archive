---
title: "Issues with packages, updates/upgrades, etc."
date: 2016-02-19
forum: General Help
---

### Post by 2rtmar on 2016-02-19
I've been using Ubuntu for about 8 months now. Throughout that time I've had a continous problem with installing and updating software via the terminal and sometimes the Ubuntu Software Center. I currently cannot use sudo apt-get install, sudo apt-get update, sudo apt-get upgrade. For example:

sudo apt-get update
I currently get the message

Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [8,444 B]                 
100% [1 InRelease gpgv 8,444 B] [Connecting to us.archive.ubuntu.com (91.189.91Splitting up /var/lib/apt/lists/partial/repository.spotify.com_dists_stable_InRelIgn [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
E: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)


I have had longlasting issues as a result of attempting to install Makerbot Desktop, tor, and Spotify.  (Spotify is the only one of the packages that I have successfully installed, but the process still created problems for installing other packages).

I've tried a few different things and I am altogether not familiar with the command line enough to solve the problems. Help is appreciated

---

### Post by QDR06VV9 on 2016-02-19
Your sources.list does not seem to be what the people at spotify are recommending. The following is from [https://www.spotify.com/us/download/previews/](https://www.spotify.com/us/download/previews/). 

Open a terminal window by typing ctrl+alt+t then type
```
gksudo gedit /etc/apt/sources.list
```

Find the line which looks like 

> [http://repository.spotify.com](http://repository.spotify.com) trusty InRelease

Delete the whole line.... Now add this
```
deb http://repository.spotify.com stable non-free
```

Exit and save the changes to /etc/apt/sources.list

Now in the terminal enter these commands:
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 94558F59
sudo apt-get update
sudo apt-get install spotify-client
```

There is this to Note: _**Note that this is a 'linux preview' version of spotify and may not be entirely stable. **_
Hope This Helps..

---

### Post by 2rtmar on 2016-02-21
Thank you! This helps. I actually fixed other problems by using "software and updates" in the settings to remove third party software developers. Fixed issues with sudo apt-get update and sudo apt-get upgrade

---


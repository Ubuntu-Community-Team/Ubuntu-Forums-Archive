---
title: "Real Player, installing, and uninstalling."
date: 2006-08-23
forum: General Help
---

### Post by Roasted on 2006-08-23
Just a question. I had realplayer in here and figured I'd get rid of it since I didn't like it. So I went to terminal, and I did a sudo apt-get remove --purge realplay.

It prompted me y/n, I hit y and continued on.

Okay, real player is gone.

Out of curiosity I did sudo apt-get install realplay. It installed...

How does the computer still have those files to install it? I thought when I do "remove --purge" it gets rid of EVERYTHING affiliated with real player. How does linux do it?

---

### Post by Roasted on 2006-08-23
Also, second question. When using VLC, after I add some songs to the playlist, if I go to the video screen where the music video would be playing, and I exit out of it, BOTH of the VLC windows disappear (the video playing screen + the add songs to library screen). Okay, fine. But why does the music keep playing? The only way to get it to stop is end both processes in system monitor. Why do they keep playing if I exit? But they only keep playing IF I close the video screen WHILE I have the add-to-library screen up as well. :confused:

---

### Post by amohanty on 2006-08-23
> Out of curiosity I did sudo apt-get install realplay. It installed...

Thats becuase an **apt-get install** will, if need be got out to the sites listed in **/etc/apt/sources.list** to download the required packages.

VLC, I am not quite sure.

HTH
AM

---

### Post by Roasted on 2006-08-23
Ahhh okay. So, I'm going to reword that so I understand more. Basically when you do an apt-get install, if the package cannot be found to install realplayer, it will instantly take another path, locate the sources list, and find the uploaded package on the sources list that is required in order to install realplayer... and it does all of this instantly. Does aptitude install do the same thing as apt-get install?

---

### Post by amohanty on 2006-08-23
Yes. However it doesnt exactly look for the package on the fly. It maitains a list of packages locally. So for eg this line in sources .list on an i386 machine:
deb://archive.ubuntu.com dapper restricted 
(or something to that effect) points to:
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/)

apt maintains the packages.gz locally and looks up quickly to download the pkg.

I believe aptitude does the same thing as apt-get.

HTH
AM

---

### Post by Marsolin on 2006-08-23
> **Roasted said:**
> How does the computer still have those files to install it? I thought when I do "remove --purge" it gets rid of EVERYTHING affiliated with real player. How does linux do it?

remove --purge does get rid of the the program and its default configuration files, but it does not clear your cache, which means the deb file itself is sitting on your hard drive still. "apt-get clean" clears the cache. The cache is located at /var/cache/apt/archives.

---

### Post by Roasted on 2006-08-23
Okay, so if I want to get rid of the program, anything associated with that program, and clear the cache, I'd do the following:

sudo apt-get remove --purge realplay
sudo apt-get clean

So if I do an apt-get clean, that gets rid of the source of the realplay files for installation. So if I'd clear the cache, when I did sudo apt-get install realplay, it'd have to go to the sources list to find the package since it would of been completely wiped off of my machine. Correct?

---

### Post by amohanty on 2006-08-23
Yes and no. yes it would clean the cache and you would no longer have the sources. However, it already **knows** where the app is on the internet via the local copy of packages.gz (unless that is outdated - something which rarely if ever happens). 

Then when you do a **apt-get install** it just downloads the file from the already **known** location from the local copy, and you should see the downloading message with the increasing % number in the left.

AM

---

### Post by amohanty on 2006-08-23
Yes and no. yes it would clean the cache and you would no longer have the sources. However, it already **knows** where the app is on the internet via the local copy of packages.gz (unless that is outdated - something which rarely if ever happens). 

Then when you do a **apt-get install** it just downloads the file from the already **known** location from the local copy, and you should see the downloading message with the increasing % number in the left.

AM

---

### Post by Roasted on 2006-08-27
Just curious, I just got rid of XMMS player. Then I decided to search my file system for "xmms" and I found 13 items.

I did:

sudo aptitude remove --purge xmms
sudo aptitude purge xmms
sudo aptitude clean
sudo aptitude clean xmms

Yet I still get the 13 files to show up when I search for xmms. Most of these are images associated with xmms. Why wouldn't they of been deleted when I purged?

---

### Post by amohanty on 2006-08-28
Not quite sure why those are still there. Have tried doing it with Synaptic (selct completely remove pacakge)?

AM

---


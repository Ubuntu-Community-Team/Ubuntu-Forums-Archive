---
title: "I've been trying to install Mplayer/Mplayerplug-in for days..."
date: 2007-05-03
forum: General Help
---

### Post by RevolutionaryBird on 2007-05-03
Let me start off by saying that I am a Linux noob. I have no idea what I'm doing. I need to install the mplayerplug-in for Firefox, and I just can't! I've tried downloading tar.gz files and running configure, and I get some error about C++ compiling. I've tried running "apt-get install mplayer" and "apt-get install mplayerplug-in" in Terminal, and get an error about being unable to find the packages. Can someone please help a brother out?

PS: I am running Ubuntu 6.06 LTS - the Dapper Drake.

---

### Post by discmaster on 2007-05-03
Well, I am far from knowing what I am doing here :D, but I was easily able to install it by using the Synaptic Package Manager; use the search function in the manager.

---

### Post by enlightened on 2007-05-03
you could try these command
sudo apt-get install mplayer mozilla-mplayer

---

### Post by RevolutionaryBird on 2007-05-03
Thanks for the suggestion, I just tried:

"# sudo apt-get install mplayer mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer"

As for Synaptic, I looked in there and didn't find it.

Well, I'll be darned! I just search again and found "KMPlayer." Is that the same thing as Mplayer? I'm installing it right now. *crosses fingers*

---

### Post by eugene.shaddow on 2007-05-03
The quickest way is to go to Systems-Snaptic Package Manager-settings-repositories....check all boes than select the server that is nearest to you.

Mplayer is restricted software because od libdvdcss2 and transcode that is required to watch movies....and don't forget you will also need  more libs. This is not an easy straight forward chore.

After selecting or x ing the boxes go to the terminal window and as an exaple use this command

sudo apt-get updates

than maybe something like this

sudo apt-get inatsll mplayer..

Need further help e-mail me

---

### Post by qpwoeiruty on 2007-05-03
First of all, for mplayer, ditch the command line and go into System/Administration/Synaptic Package Manager.

Go to the Settings menu and click on repositories and enable multiverse and universe. Search for mplayer and mozilla-mplayer and install it by right clicking on it, choosing ¨Mark for Installation¨ and then ¨Apply¨.

---


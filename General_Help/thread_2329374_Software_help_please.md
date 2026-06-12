---
title: "Software help please"
date: 2016-06-30
forum: General Help
---

### Post by Softa on 2016-06-30
I have xubuntu on my Acer netbook. When I go to update, it fails to download the repository and file packages. My desktop and my brothers are not having this problem. I am sending the URL to my brother, as he is my *go-to* in these matters. Any and all help is greatly appreciated.

---

### Post by sideburns on 2016-06-30
Brother here.  The netbook just keeps asking us to check the settings, but all we can check are what repositories and so forth, nothing about her connectivity.  And, as I don't use Ubuntu, or any Debian-based distro, there's only so much I can suggest.  Our connectivity is fine, and we're able to browse anything else, so we know it's not that.  I'm mentioning this to keep suggestions from going down dead-ends we've already tested.  Thanx in advance for any help.

---

### Post by ian-weisser on 2016-06-30
What release of Xubuntu? (14.04? 16.04? Something else?)
Did this problem recently start on an older system? Or was this a recent install?

Open a terminal and please show us the complete output of the following two commands
```
sudo apt update
sudo apt upgrade
```

---

### Post by Softa on 2016-07-01
Here is what I tried at your suggestion: sudo apt upgrade, and it didn't work.  At it's suggestion, I tried
sudo apt-get upgrade --fix-missing, and here is the result...At the end of sudo apt update, it says E: Some index files failed to download. They have been ignored, or old ones used instead.
Next I tried sudo apt upgrade, and it says: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? I tried that and this is what I got...E: Failed to fetch [http://dl.google.com/Linux/chrome/deb/pool/main/g/google-chrome-stable/google-stable](http://dl.google.com/Linux/chrome/deb/pool/main/g/google-chrome-stable/google-stable) 48.0.2564.97-1 i386.deb 404 not found [IP: /4.125.22.136 80]

BTW, I'm using distro 14.04

---

### Post by speartip on 2016-07-02
The problem looks like google chrome. You seem to be trying to download a 32 bit version of Google Chrome, which as far as I am aware doesn't exist anymore. Google only release Chrome for 64 bit computers now, hence the error.
You need to disable the Google Chrome repo in software sources. Then run:
```
sudo apt-get update && sudo apt-get upgrade
```
Your problem should now disappear.

---

### Post by sideburns on 2016-07-03
OK, and how do we disable that repo?  (Remember, neither of us is skilled at using Ubuntu.)  And I presume that using sudo apt-get remove chrome first would get rid of it if it's not being used?

---

### Post by Mopar1973Man on 2016-07-03
Easiest way is to install Synaptic package manager if you haven't yet. 

```
sudo apt-get install synaptic
```

Then you can remove the repository that is hanging up the update also remove the old Chrome browser and then you can update to the 64 Bit version as well. Graphical interfaces are bit easier on less technical minded folks.

---

### Post by sideburns on 2016-07-03
Thank you; we may already have it installed, but we'll check.  And, although I'm very comfortable with a CLI, my sister isn't and she's the one who should do the job.

---


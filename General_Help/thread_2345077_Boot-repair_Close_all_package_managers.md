---
title: "Boot-repair? Close all package managers?"
date: 2016-11-30
forum: General Help
---

### Post by Macamba on 2016-11-30
My dual boot system had a bit of a SNAFU. My MBR got corrupt, and I ended up with a single boot Windows 10 system. I'm trying to get GRUB2 installed using 'boot-repair' downloaded to a session started with a life CD, but I run into 
```
Please close all your package managers (Software Center, Update Manager,
Synaptic, ...). Then try again.
```

How can I close my package managers? I did not start them. Are they running in the background?

---

### Post by oldfred on 2016-11-30
What version of Ubuntu.
Live install should not have other update managers open unless you actually opened them.
Occasionally we have seen where not closed correctly and the lock file for updates remains, preventing all updates. But live install should not have that issue.

I have gotten same message when I use synaptic to check something and forget to close it before using command line to install a package.

---

### Post by Macamba on 2016-11-30
> **oldfred said:**
> What version of Ubuntu?

It reads 14.04 on the DVD. I started this DVD, choose to 'Try Ubuntu', opened a Terminal, and
```
sudo add-apt-repository -y ppa:yannubuntu/boot-repair; \
sudo apt-get update; \
sudo apt-get install -y boot-repair && boot-repair
```

And then I get this error message.

---

### Post by oldfred on 2016-11-30
Usually Boot-Repair works even if Windows 10 is hibernated or fast start up on. But it will give messages that partition cannot be mounted.

Is fast start up off in Windows? But I doubt if that is your current issue, but it must be off to install.

Or it just could be a bad download, I might try getting a new ISO and install to flash drive to see if that solves issue.
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
        [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
      [/URL][https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by Macamba on 2016-11-30
> **oldfred said:**
> Usually Boot-Repair works even if Windows 10 is hibernated or fast start up on. But it will give messages that partition cannot be mounted.

Is fast start up off in Windows? But I doubt if that is your current issue, but it must be off to install.

Or it just could be a bad download, I might try getting a new ISO and install to flash drive to see if that solves issue.
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
        [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
      [/URL][https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

In the past I did my best to turn off fast startup. I checked today, and found out it is still turned off. So I will burn a new ISO on an USB stick and reboot my system. ;-)

---


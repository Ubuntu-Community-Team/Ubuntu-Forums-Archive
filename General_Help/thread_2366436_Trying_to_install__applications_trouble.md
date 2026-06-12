---
title: "Trying to install  applications trouble"
date: 2017-07-17
forum: General Help
---

### Post by RobGoss on 2017-07-17
Hello everyone, I'm trying to install a few applications but each time I run any terminal commands I get the following message
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```


Thanks for any help with this issue

---

### Post by deadflowr on 2017-07-18
Was this solved?
Anyway if not, do you have anything running apt in the background?
(It could be the software center, or synaptic or unattended-upgrades perhaps?)

---

### Post by unityforever on 2017-07-18
type
sudo rm /var/cache/apt/archives/lock sudo rm /var/lib/dpkg/lock

but this operation is not recommend, that sign is always means there are installer running in background.
i suggest you check it and close the process safely.

---

### Post by RobGoss on 2017-07-18
I was trying to install Brave browser and I'm assuming it was the command provided by their website that was causing the error massage, this is the website I was using for the Ubuntu OS for Brave
[https://github.com/brave/browser-laptop/blob/master/docs/linuxInstall.md](https://github.com/brave/browser-laptop/blob/master/docs/linuxInstall.md)

I was able to get it installed anyway..Thanks so much

---

### Post by vocx on 2017-07-18
> **RobGoss said:**
> Hello everyone, I'm trying to install a few applications but each time I run any terminal commands I get the following message
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```


Thanks for any help with this issue
This message happens when you try to use "apt", "apt-get", or "aptitude", or the graphical interfaces, like Software Center, and Synaptic, and an instance of the APT program is already running, as you cannot have more than one instance of it running.

I see many people get worried about this error, and think their system is seriously damaged. In most cases, **this is not a serious error**, it just means than the "apt" process is running, probably in the background, checking the sources list for updates. It is a very common "error" message, and **the cure is to simply wait for a minute or two**. Afterwards, you can use "apt" and similar programs without problem.

You may see this message when you first boot up your system or return from suspend. If you immediately try to "apt update", for example, you may see the lock error. It just means your system was faster than you, and it's already looking for updates. So, not a serious issue, just wait for it to finish.

Only if you wait many minutes, even hours, and you really cannot use "apt" at all, that means the lock file for some reason remained and was not deleted automatically. So then you need to delete it manually, and continue with your life.

[https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

---


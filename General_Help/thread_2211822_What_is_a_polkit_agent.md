---
title: "What is a polkit agent?"
date: 2014-03-18
forum: General Help
---

### Post by vasa1 on 2014-03-18
Please see Julien's response at the bottom of [this link]("https://lists.ubuntu.com/archives/lubuntu-users/2014-March/006913.html"): "[I]be sure to have policykit-desktop-privileges package
installed and a polkit agent running. That's may fix strange permissions
problems.[/I]"

I have *policykit-desktop-privileges* installed:

```
$ apt-cache policy policykit-desktop-privileges
policykit-desktop-privileges:
  Installed: 0.16
  Candidate: 0.16
  Version table:
 *** 0.16 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
$
```But how do I find out about whether or not I have "*a polkit agent running*"? I just see```
$ pgrep -l agent
1145 ssh-agent
$
```
I don't have any permission problems (that I know of) but I'm curious about this *polkit agent* business. I ran the *pgrep* command in an Openbox session (no desktop session, no gnome-settings daemon).

---

### Post by vasa1 on 2014-03-18
After a little digging I found I have
```
root       620     1  0 15:35 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug
```
Maybe that's the "agent"?

---

### Post by Dennis N on 2014-03-18
> [from Arch Linux Wiki] Authentication agents

An authentication agent is used to make the user of a session prove that the user of the session really is the user (by authenticating as the user) or an administrative user (by authenticating as an administrator). The polkit package contains a textual authentication agent called 'pkttyagent', which is used as a general fallback.

If you are using a graphical environment, make sure that a graphical authentication agent installed and autostarted. Cinnamon, GNOME, MATE, KDE and LXDE have an authentication agent already. 


I believe the authentication agent service we use is provided by **policykit-1-gnome** and it displays the authentication dialogs when needed, **polkitd** being the daemon part which runs in the background, keeping watch.

---

### Post by vasa1 on 2014-03-19
> **Dennis N said:**
> I believe the authentication agent service we use is provided by **policykit-1-gnome** and it displays the authentication dialogs when needed, **polkitd** being the daemon part which runs in the background, keeping watch.
Thanks for responding!

As the image shows, I have **policykit-1-gnome** as well and I see no problems when running gksudo leafpad (which I rarely do). So even though I'm using an Openbox session, it looks like things are being taken care of.

I forgot to mention that I think I needed to do this for some reason:```
Start-Date: 2014-01-29  16:49:35
Commandline: apt-get install policykit-desktop-privileges
Install: policykit-desktop-privileges:amd64 (0.16)
End-Date: 2014-01-29  16:49:37

```
It wasn't installed by default. I think I read about its function in a mailing list post by Julien. I'll link here if I find it.

Found it: [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html)

---


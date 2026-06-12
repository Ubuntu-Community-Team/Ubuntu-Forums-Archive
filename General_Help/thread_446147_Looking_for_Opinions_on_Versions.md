---
title: "Looking for Opinions on Versions"
date: 2007-05-16
forum: General Help
---

### Post by SteveF on 2007-05-16
I currently keep two versions of Linux on my computer.  So far, I put latest Ubuntu on one and latest Kubuntu on the other.  This hasn't been a problem until Feisty.  I ran into a CD burning problem that I have not been able to fix.

This has lead me to believe I made a mistake keeping both up to date.  I decided what I should do is have a stable version and one that is current (and hopefully stable).  This leads me to 3 paths and I'm just looking for opinions:

1) Keep latest good version of Ubuntu and update the other.  If that makes it OK, then the next version will be updated on the prior (ie alternate).  If it has problems, leave good one alone and update broken one.  repeat until fixed.  My concern is the length of support time if I have problem over a couple of versions.

2) Make one version be the LTS version and update the other.  Is the LTS really more stable?  Is it worth having older software for the duration.

3) Look for a known stable distribution instead of LTS (like Debian stable).  Is it really any more safer than LTS?  It can take even longer to update stable leaving me with even older software.

Anyway, fire away.

Steve

---

### Post by aysiu on 2007-05-16
The LTS version isn't any stabler than the newest version. LTS means "long-term support," which means it gets security updates for three years instead of eighteen months. It does *not* mean it is stabler than non-LTS releases.

The best thing to do is [back up your current installations](http://www.psychocats.net/ubuntu/backup) and then upgrade. If the upgrades go badly, then restore the backups.

---

### Post by zoogTHOMzoog on 2007-05-16
Why do you want the two (i.e. Kubuntu and Ubuntu) to be separate? Are they on two different computers? I would just use one if they are on the same computer so that whether I am using KDE, gnome or XFCE, all the software is up to date. 

Not to be presumptuous, but you can have kubuntu(kde) and ubuntu(gnome) on the same partition by doing 
```
sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get xubuntu-desktop  
```
for which ever environment you desire/lack. You can choose which session is default from gdm or kdm. 

I hope I helped!

:guitar:

---

### Post by aysiu on 2007-05-16
> **zoogTHOMzoog said:**
> Why do you want the two (i.e. Kubuntu and Ubuntu) to be separate? There are a lot of reasons one might want them separate. If you install both on one system:
1. Your applications menu gets cluttered up with a mix of Gnome and KDE applications
2. Sometimes KDE makes your Gnome applications look ugly if you use the option to have Gnome apps use the KDE theme in KDE
3. There can be only one Usplash or default display manager
4. I'm not sure if this still applies, but at one time you could not shut down from KDE using GDM without logging out first (and the same for Gnome using KDM)

---

### Post by SteveF on 2007-05-16
> **zoogTHOMzoog said:**
> Why do you want the two (i.e. Kubuntu and Ubuntu) to be separate? Are they on two different computers? I would just use one if they are on the same computer so that whether I am using KDE, gnome or XFCE, all the software is up to date. 

Not to be presumptuous, but you can have kubuntu(kde) and ubuntu(gnome) on the same partition by doing 
```
sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get xubuntu-desktop  
```
for which ever environment you desire/lack. You can choose which session is default from gdm or kdm. 

I hope I helped!

:guitar:

The main reason was to play around with both versions to see which I preferred (using default applications).  I have found that if I limit what I have access to, I can determine if I like using the software.  And Kubuntu and Ubuntu have different default software.

For example, though I could install Firefox on Kubuntu, I didn't forcing me to use Konqueror and get used to using (I think you need to spend time with any software to really determine if you like it).

After I started doing that, it then became more of a upgrade one and see if it breaks with the other being a fallback.

Steve

---

### Post by SteveF on 2007-05-16
> **aysiu said:**
> The LTS version isn't any stabler than the newest version. LTS means "long-term support," which means it gets security updates for three years instead of eighteen months. It does *not* mean it is stabler than non-LTS releases.

The best thing to do is [back up your current installations](http://www.psychocats.net/ubuntu/backup) and then upgrade. If the upgrades go badly, then restore the backups.

I was going with the assumption (possibly wrong) that if a version was getting LTS then the developers would have spent more time making sure it was stable.

The other thing is the longer support means I can upgrade one version until it works while possibly holding on to the LTS as backup since it is supported longer.

Thanks,

Steve

---


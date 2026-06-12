---
title: "How To Check If A PPA Is Added Correctly?"
date: 2013-06-05
forum: General Help
---

### Post by Doctor J. on 2013-06-05
On my Precise machine, i already added a PPA for ClassicMenu.  This went well.  Now i want another PPA to install Handbrake.  I followed the directions on [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases) .  It seemed like it went well, but i can't "sudo apt-get install handbrake", nor does it show up in the Software Center.  How do i view the added PPAs to see if there was a typo or something?

---

### Post by btindie on 2013-06-05
Did you do ```
sudo apt-get update
``` after adding the PPA?

There should be a file in /etc/apt/sources.list.d/ that corresponds to the new PPA.

---

### Post by Steeperton on 2013-06-05
From memory, you should use:
```
sudo apt-get install handbrake-gtk
```

---

### Post by mc4man on 2013-06-05
For whatever reason that ppa's packages may not show up in Software Center search if searching on the default 'All Software'

If you did actually get it enabled (the ppa), then in Software Center you'll see it in the drop down as in screen. Select the highlighted source if there & then packages will show

Otherwise from apt-get you need to use the actual package name
```
sudo apt-get install handbrake-gtk
```

---

### Post by slickymaster on 2013-06-05
There are two official HandBrake PPAs, [ppa:stebbins/handbrake-releases]("https://launchpad.net/~stebbins/+archive/handbrake-releases"), for stable releases, which are updated about once a year and [ppa:stebbins/handbrake-snapshots]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots"), for nightly builds, which are updated daily.

To install HandBrake stable release, just run the following:```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-cli handbrake-gtk
```

---

### Post by slickymaster on 2013-06-05
> **mc4man said:**
> For whatever reason that ppa's packages may not show up in Software Center search if searching on the default 'All Software'

If you did actually get it enabled (the ppa), then in Software Center you'll see it in the drop down as in screen. Select the highlighted source if there & then packages will show

Otherwise from apt-get you need to use the actual package name
```
sudo apt-get install handbrake-gtk
```

(Currently that ppa may not be added if using  - 
sudo add-apt-repository  ppa:stebbins/handbrake-release[COLOR=#ff0000]**s**[/COLOR]
as the address add-apt-repository uses seems wrong

I think you are missing an 's' in release.

---

### Post by mc4man on 2013-06-05
> **slickymaster said:**
> I think you are missing an 's' in release.

Your right - sloppy copy & paste on my part...

---

### Post by Doctor J. on 2013-06-06
> **btindie said:**
> Did you do ```
sudo apt-get update
``` after adding the PPA?

Well, i thought i had, but possibly i forgot that crucial step.

---

### Post by Doctor J. on 2013-06-06
> **Steeperton said:**
> From memory, you should use:
```
sudo apt-get install handbrake-gtk
```

Yup, that missing '-gtk' was what had me stymied.  It's curious that Software Center doesn't find handbrake-gtk when the search term is "handbrake", though.

---

### Post by Doctor J. on 2013-06-13
> **mc4man said:**
> For whatever reason that ppa's packages may not show up in Software Center search if searching on the default 'All Software'

Okeh, i'll bite.   Since Software Center is unable to show me what i was looking in default mode, how do interact with it for it to be useful?

---


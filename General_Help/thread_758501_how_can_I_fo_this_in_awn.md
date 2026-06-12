---
title: "how can I fo this in awn?"
date: 2008-04-18
forum: General Help
---

### Post by ADBD on 2008-04-18
[http://www.gnome-look.org/content/show.php/dock+icons+for+elegant+brit?content=77142](http://www.gnome-look.org/content/show.php/dock+icons+for+elegant+brit?content=77142) How can I make other icons come out of another one like in that pic (like on a mac)?

---

### Post by aktiwers on 2008-04-18
That link seams pretty dead to me?

---

### Post by ADBD on 2008-04-19
> **aktiwers said:**
> That link seams pretty dead to me?

Oops. Fixed.

---

### Post by soldats on 2008-04-19
it says in the link to try cairo-dock instead as that is what tha person is using. the posts suggest that AWN cant do that as of yet.

---

### Post by odysseusjak on 2008-04-19
The latest version of AWN has 3 'stacks' applets: Stacks Applet, Stacks Plugger, and Stacks Trasher.

---

### Post by prshah on 2008-04-19
> **odysseusjak said:**
> The latest version of AWN has 3 'stacks' applets: Stacks Applet, Stacks Plugger, and Stacks Trasher.

Sorry to jump in; but I can't seem to "populate" the stack. I've tried dragging and dropping, right clicking, etc. Any help, please?

---

### Post by odysseusjak on 2008-04-20
> **prshah said:**
> Sorry to jump in; but I can't seem to "populate" the stack. I've tried dragging and dropping, right clicking, etc. Any help, please?

All I did was activate the stacks applet from the AWN manager window.  I then right clicked on the icon and selected preferences.  I changed the backend to 'folder backend' and just used the default (it points to your home directory).  On the stacks tab, you can change the look of the stack from the default to a curved stack similar to that of Apple's.  Click apply and you're all set!

I hope that helped.

---

### Post by ADBD on 2008-04-21
I don't even have those. I have awn 0.2.1, how can I update it? This is the latest release in the synaptic and trying to install the extras from those sources.list didn't work: [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

---

### Post by moonbeam on 2008-04-21
> **ADBD said:**
> I don't even have those. I have awn 0.2.1, how can I update it? This is the latest release in the synaptic and trying to install the extras from those sources.list didn't work: [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

The extras packages in awn-testing is not compatible awn <0.2.2.

If you want to use the awn-testing ppa you will need to remove the official Ubuntu awn packages and install both core and extras from the awn-testing ppa.

Some instructions can be found here:  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by ADBD on 2008-04-21
> **moonbeam said:**
> The extras packages in awn-testing is not compatible awn <0.2.2.

If you want to use the awn-testing ppa you will need to remove the official Ubuntu awn packages and install both core and extras from the awn-testing ppa.

Some instructions can be found here:  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

Yes, that's what I tried to do. But step 8. "Click the "Reload" button. This will download the new Awn package information." Just gives me an error.

---

### Post by Oofda33 on 2008-04-23
I am using AWN 0.2.6 with Ubuntu 8.04 Hardy Heron and it is working pretty good.  I am playing with stacks atm and have only ran into a couple problems.  One is that I have lost my Awn Manager icon on the bar and can't seem to get it back.

The Second one is that I am trying to make an OpenOffice Stack.  I can get the OpenOffice programs to show up on the stack and I can click on them but then I get the following error .. /home/dad/%U does not exist. ..  The OpenOffice program will open after I acknowledge the error by clicking ok.

I have tried the default directory as well as "/usr/share/applications/stacks/openoffice" and get the same problem.

The Stacks Applet Layout functions, Stacks Layout functions and Behavior all work well.

I used the install instructions on this page [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml]("http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml")

---


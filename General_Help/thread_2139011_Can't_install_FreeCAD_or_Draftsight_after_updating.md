---
title: "Can't install FreeCAD or Draftsight after updating to lts-quantal kernel and xserver"
date: 2013-04-25
forum: General Help
---

### Post by AleveSicofante on 2013-04-25
I was running 12.04.2 with the 3.2 series kernel. I thought the "latest and greatest" would be a good idea, so I installed the lts-quantal kernel and corresponding xorg-lts-quantal components. I'm actually planning to do the same with the upcoming lts-raring and lts-salamander kernels and xserver components until the next 14.04 LTS arrives (or even beyond, it's too early to tell).

A few weeks later I tried to install FreeCAD and Draftsight and both want to remove xorg-lts-quantal and replace it with the "plain" older xorg packages (actually, I did install Draftsight completely without paying too much attention, only to get a non-booting system that I could repair fortunately by booting into recovery mode and reinstalling xorg-lts-quantal, which in turn removed Draftsight for not matching the dependencies, I guess).

I understand it's the duty of the developers of these applications to keep an eye on the updates provided by the so called "hardware enablement stack", but I'm not quite sure if that's the case or if I can do something to work around this issue. I'm also curious about what would happen with a fresh install of the current 12.04.2 and these CAD apps.

Should I file a bug to the developers of FreeCAD and Draftsight or is there something I can manually do to change the dependency requirements of these two packages?

---

### Post by Frogs Hair on 2013-04-25
I had Draftsight installed on 12.10 , but didn't pay attention to the details of the installation . I also had proposed updates enabled when it installed with no ill effects. I have not thought about installing the application since installing 13.04 but they are still sending me email .

---

### Post by AleveSicofante on 2013-04-25
Sorry I should have put this is about 12.04 in the thread's title. Is there a way to change the thread's title?

---

### Post by Gemnoc on 2013-06-29
Hello AleveSicofante,

Sorry for coming in late to the party. I am the current maintainer of the [FreeCAD PPA repository]("https://launchpad.net/~freecad-maintainers/+archive/freecad-stable"). We witnessed the same problem with our packages when the LTS Enablement Stack came out. After much struggling (I am in no way a specialist in debian packaging, I just know enough to get by) I managed to find and fix the packaging error.

I have no control over the FreeCAD package residing in the official Ubuntu repository, in any case I strongly recommend you install FreeCAD from our PPA since it hosts a newer version (0.13.1830) with a boatload of new features.

Here's the instructions page on how to install: [https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Install_on_Unix](https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Install_on_Unix) *(Posting the link to the deprecated wiki since the [new one]("http://www.freecadweb.org/wiki/index.php?title=Main_Page") is currently down. AFAIK the contents of this specific page has not been changed.)*

As for DraftSight, since this is a packaging error, there is no way a user can correct this other than rebuild the package himself. Since DraftSight is proprietary you don't have this choice because you would need the source code. You can try posting on the official forum about your problem.

---

### Post by AleveSicofante on 2013-06-29
Thank you very much. I sincerely appreciate the work you've done.

I just got tired of this sort of issues in 12.04 and went to 13.04. So much for the LTS "stability"...

---


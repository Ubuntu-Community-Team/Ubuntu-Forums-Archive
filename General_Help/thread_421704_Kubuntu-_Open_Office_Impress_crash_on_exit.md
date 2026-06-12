---
title: "Kubuntu- Open Office Impress crash on exit"
date: 2007-04-24
forum: General Help
---

### Post by mykrob on 2007-04-24
Hey-

I ma having an issue with Open Office crashing on exit. I have seen the thread about selecting an icon set other than crystal within OpenOffice, which I have done.. The app works fine, but when I go to close it, it crashes, the crash recovery thing comes up, and then opens a blank document...

Can this be fixed?

Thanks,
-myk

---

### Post by hvbakel on 2007-04-24
Same problem here...

---

### Post by canadianwriterman on 2007-04-24
Are you talking about Impress crashing after viewing a presentation in slideshow?

---

### Post by mykrob on 2007-04-24
actually, now that you mention it, i think it does only crash after exiting if i have tested the presentation.. If i just open the document and edit it without test viewing it, it closes normally.. Is this a bug with this version of open office, or in ubuntu itself?

thanks,
-myk

---

### Post by canadianwriterman on 2007-04-25
This is a bug in the Ubuntu version of OpenOffice. It has been filed as a bug report, confirmed and marked as critical. No one has a fix for it yet. However, if you install the official OpenOffice from openoffice.org, everything works as expected with no bug.

The install is a bit involved, due to the large number of files to download and install, but there are easy-to-follow instructions that I can post if you're interested in taking that route.

---

### Post by mykrob on 2007-04-25
please do. I think some others may benefit from it as well.

thanks,
-myk

---

### Post by canadianwriterman on 2007-04-25
Okay, folks, here is the answer I got on the OpenOffice Impress forum (don't know if you have to create a free account to read it or not). A couple of things to note first:

[LIST]
[*]You need Alien to convert the RPMS. It's easy to get (info in the link).
[*]There is a desktop integration mentioned for GNOME, but the files you download include desktop integration for KDE as well. You'll just have to check the names of the files in the integration folder and change the text in the command line shown in the link.
[/LIST]

Other than that, I was impressed by the extra speed and stability of the "factory" version of OpenOffice versus the version provided with Ubuntu.

[http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370]("http://http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370")

---

### Post by canadianwriterman on 2007-04-25
Just tried the link that I included in my post above and it doesn't work for me. So, I'll cut and paste the instructions from the OpenOffice forum below just in case.

> In case you had not followed the links, here is a simple procedure : 
- Download the RPMs from OOo site. 
- Remove the OOo version installed by default in Ubuntu out of the box if still installed (all green packages with 'openoffice.org2 in Synaptic). No need if you've already upgraded once before. 
- Then in the console : 
Code: 
cd rep_install_OOo/RPMS [MAY HAVE TO CHANGE THIS LINE TO REFLECT THE NAME OF THE DOWNLOADED DIRECTORY]
sudo alien -d --scripts *.rpm 
sudo dpkg -i *.deb 

- Then update the Gnome menu: 
Code: 
cd desktop-integration 
sudo dpkg -i openoffice.org-debian-menus_2.0.4-2_all.deb 

NB: if alien is not installed, then: 
Code: 
sudo apt-get install alien 

---

### Post by mykrob on 2007-04-26
thanks, that works fine.

---

### Post by stchman on 2007-05-16
> **mykrob said:**
> Hey-

I ma having an issue with Open Office crashing on exit. I have seen the thread about selecting an icon set other than crystal within OpenOffice, which I have done.. The app works fine, but when I go to close it, it crashes, the crash recovery thing comes up, and then opens a blank document...

Can this be fixed?

Thanks,
-myk

Yes, it is strange.  I can open Impress, load a presentation, view a slideshow and do other stuff.  When I exit Impress it then tells me that it is going to recover the document.  The document is still intact so there is no damage.  It is a minor nuisance.  The fonts with Feisty installed OO2.2 look WAAAYYYY better than the fonts with the downloaded OO2.2.

I am sure Ubuntu will get around to fixing the problem.

---

### Post by Hagar Delest on 2007-05-16
> **canadianwriterman said:**
> Other than that, I was impressed by the extra speed and stability of the "factory" version of OpenOffice versus the version provided with Ubuntu.

[http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370]("http://http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370")
There is an additional "http://" string in your link in fact (first part).

Here is the good one : 
[http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370]("http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370")
I confirm I've always installed the official OOo version and never had any issue. The Feisty release is really a bad one (much more than previous ones). I don't understand why so much issue for a so important application. What a bad advertisement for Ubuntu :confused:

---

### Post by IgnorantGuru on 2007-05-17
This is probably a different problem, but I'll throw it in here in case someone searches for it...

I installed Kubuntu Feisty from scratch on 3 different machines, one with the LiveCD and two with the Alternate.  On all machines, when I tried to open my OO 2.0.4 spreadsheets, OO calc crashed.

I finally narrowed it down to something this simple:  open a brand new spreadsheet, add a button control, add an event 'when mouse button released' to link it to a macro (Sub Main will do).  Try to exit design mode - crash.

After trying a number of complicated things, I happened to uninstall all of OO and reinstall it from the repos (in Adept).  Problem solved on all three machines.

So I know it sounds Windows-like, but if you're getting OO crashes I suggest uninstalling and reinstalling the whole OO set.

---

### Post by jedimasterk on 2007-06-20
Doesn't fix the crash on exit problem. Even if you do a complete uninstall/re-install.. Needs to be fixed with an update by Canonical.

---

### Post by kiev on 2008-06-15
for me it bug takes place on 4th computers!!!

sudo aptitude **reinstall** openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-hyphenation openoffice.org-impress openoffice.org-kde openoffice.org-style-crystal openoffice.org-style-human openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us openoffice.org-writer - **does not decide a problem** [img]http://ubuntuforums.org/images/icons/icon8.gif[/img] ((((((((((

---

### Post by Hagar Delest on 2008-06-15
Give the official version a try: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---


---
title: "how to set the external screen"
date: 2008-05-22
forum: General Help
---

### Post by freespire on 2008-05-22
hello!i am a new member and new linux user.all these years i was stacked with the disgusting windows.then i tired all the linux distributions and i find ubuntu....just amazing.

Now for my bad luck my laptop had an ''accident'' and i had its screen broken.fortunately ia made a connection with an external screen device but now i have both of them switched on.
Does anybody knows how can i set to work only the external screen?

thank u very much

i use the latest ubuntu with gnome desktop--->8.04

---

### Post by BandD on 2008-05-22
Go to System--> Preferences--> Screen Resolution.  It should show two monitors, one will most likely say laptop and the other will be the external monitor.  Click the laptop screen and in the resolution box, select, Off.  That should do the trick.

---

### Post by freespire on 2008-05-22
thank u very much!!
it was exactly as you said!!!:p

if you allow me i would like to ask a few things.i undersand that the newbies like me are a pain in the *** but i would appreciate any help cause in greece linux are not yet popular.so if you allow me--->

1.do i need  an antivirus?cause i hate antivirus industry....
2.my system keeps telling me that it is unable to mount my external disk devices which have are ntfs
3.i have problems in playing dvds.it keeps on telling me---.error reading the source(totem player...should i give a try to ogle player...but i still can not find the installation instructions
4.and now the most important of all is what must i do with the microsoft office files....unfortunately in the university everything is based on office 2003/2007.how can i open these files+how can i write a doc. which can be read by microsoft office?
i also found these cross-platforms---->wine
                                       win4lin
                                       crossover
are these fit?


please help me cause i really really hate the microsoft platform...](*,)

---

### Post by BandD on 2008-05-22
1. You don't really need any antivirus software for your Linux machine.  There just aren't really any viruses for the Linux platform.  But if it makes you feel 'safer' there are some anti-virus programs for Linux.  You can read this post about [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765696").

2. I would post a new thread about the mounting problems.  I'm not too good in that area.  Ubuntu doesn't have any problems with the NTFS filesystem, so something else is happening.  Be sure to tell them how you connect the external devices--usb, SATA, etc.

3. I'm not exactly sure what the error means.  But Ubuntu doesn't have the capability to read the DVD codec initially.  Did you install the 'Ubuntu Restricted Extras' package?  Go to System--> Administration--> Synaptic Package Manager.  Then search for "ubuntu-restricted-extras".  Then click it and Mark for Installation.  Then click Apply.  That will install the needed files to play DVD, MP3, AAC, and other proprietary (private) file types.

4. OpenOffice.org, the office suite that comes with Ubuntu can read all most all MS Office files.  There is even an option to save the files in the MS Office format.  So you can try that out first.  I haven't ever used Wine or Crossover, but I've read good things about them and MS Office.

So give it a shot!  I hope that helps.

---


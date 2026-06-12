---
title: "No Kickoff Apps kde-plasma-desktop"
date: 2014-03-13
forum: General Help
---

### Post by Rob Sayer on 2014-03-13
Someone's probably going to suggest using forum.kde.org for this since it isn't kubuntu.  I would, but I lost my password and every time I try to reset it, it tells me my user name is wrong, which is isn't.  I searched.

Anyway, I have lubuntu 13.10 on my 1Gb netbook and I'm trying to set up a minimal footprint kde setup ... I use kubuntu on my more powerful laptop.

So, I installed kde-plasma-desktop.  PLus everything else I thought I'd need.

But when I go to the kickoff launcher there are appplications listed, period.  Just krunner.  This doesn't seem right ...

It happens in both openbox (which I'd prefer for speed) and plasma.

I used dpkg-reconfigure on kdm to make it the default.  No change.  Set it back to ldm.

One more thing ... there's no system settings except for power management, and even that isn't complete.

WTF?  This is supposed to be the bare minimum KDE install?  Doesn't that imply that it would be actually functional?

Nothing I've found on using kde-plasma-desktop indicates it's this difficult, and I can't find anything on what to add to make this actually work.

Is there anyone out there who's actually got this actually useable?

Would it make more sense to just frakking install kubuntu and remove things?

---

### Post by Rob Sayer on 2014-03-14
So I purged all the kde stuff I had installed with synaptic.  Then reinstalled kde-plasma-desktop in terminal.

Still no applications whatsoever in the kickoff launcher, and not even the system settings app available through krunner.

I just watched a a youtube video showing some guy installing kde-plasma-desktop through terminal in a VM in unity.  HIS applications and system settings were there.

WTF?

Is this 13.10 screwing up again?  I'm using lubuntu 13.10 mostly because I was getting sick and tired of fighting kubuntu 13.10.

---

### Post by Rob Sayer on 2014-03-15
So I tried deleting .kde from my home directory.  Nothing.  Still doesn't find apps ...

---

### Post by Rob Sayer on 2014-03-16
OK, I got apps showing through this ...

[http://askubuntu.com/questions/262888/how-to-get-openbox-as-kdes-window-manager/263065#263065](http://askubuntu.com/questions/262888/how-to-get-openbox-as-kdes-window-manager/263065#263065)

... which is good.

Still don't have any Sytem Settings.  Which is frustrating.  The youtube video I saw had them immediately after install.  But I guess that's a separate thread ...

Actually I got system settings going ... unfortunately I wasn't changing just one thing at a time so I'm not sure what I did, so I can't post anything useful there.

---


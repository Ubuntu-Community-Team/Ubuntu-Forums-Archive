---
title: "Keeping Thunderbird 2 profile on NTFS?"
date: 2007-05-02
forum: General Help
---

### Post by melat0nin on 2007-05-02
Hello all

I'd like to use my Thunderbird profile from XP but I'm having a bit of trouble with it.  I've installed Thunderbird 2 using the installer script, but when I point profiles.ini to the relevant place on my NTFS drive, Thunderbird refuses to run (it gives me a notice saying that it is already running).

I have enabled the NTFS write support from the Add/Remove Programs applet, and I've searched for a 'lock' file in the profile, but there isn't one.  The profiles.ini setting IsRelative is also set to 0, and the path I've put is "/meda/hda5/My Documents/Thunderbird/xlt722ry.default" (with quotes because of the space in 'My Documents').

Any ideas what I can try?  I also can't find a way to get rid of TB2, if that's what I end up having to do.  Anyway, I really need to get access to my emails, and my profile is very important so I really don't want to have to start afresh.

Any help much appreciated!!

-m

---

### Post by shae on 2007-05-03
I will put it like this.  I tried to do the same with firefox.  It completely blew up in my face and wiped out both profiles so make a backup.

In linux go to ~/.mozilla and delete the Thunderbird folder.  Then create a link in there to where it is on your windows partition.

I am not promising this will not blow up in your face bad.

---


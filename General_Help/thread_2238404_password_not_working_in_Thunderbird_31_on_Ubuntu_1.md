---
title: "password not working in Thunderbird 31 on Ubuntu 12.04"
date: 2014-08-07
forum: General Help
---

### Post by Ka_Chun_Yu on 2014-08-07
I've been having trouble with getting Thunderbird 31.0 working on my Ubuntu 12.04 box.  The OS was built from scratch on this machine a few months ago, and I've done regular updates through the Update Manager.  My Thunderbird profile has been migrated through multiple versions of Ubuntu (and Redhat before that).  I've noticed some odd glitchiness in the past, but nothing like what I've seen today.  (Note: things were fine a week ago, the last time I logged onto this desktop machine.)

I am using Thunderbird to access an Exchange server at my work place.  I had to change the Exchange password in the past week while away from the office.  After coming back, my Ubuntu Thunderbird isn't downloading new messages, nor is it complaining about not having the right password.  When I click on "Get Messages", the program freezes with a "Loading Message..." message at the bottom of the GUI frame.  I've tried to (re-)move the password files (key3.db and signons.sqlite) out of my main profile directory, to force Thunderbird to request a new password.  However that doesn't elicit any requests from Thunderbird when I restart it.  If I check Preferences->Security->Passwords->Saved Passwords, the GUI display shows *no* passwords. That is, there isn't a single one to select and look at, and searching for my username or server name doesn't return any results either.  I am not using a Master Password. If I try to send a message, the "Sending message..." progress window hangs in perpetuity (it seems), again without any complaints or error dialogue windows popping up.

I've tried re-starting with all Add-Ons disabled. I've used Synaptic to re-install Thunderbird.  I've done a complete removal of the program before re-installing it again.

I have Thunderbird (version 24.2.0) running on a Windows 7 machine, accessing the same Exchange server, without any problems.  So it doesn't seem like it's the server's problem. Theoretically the server could be responding to the Ubuntu and Windows TB's differently, but the behavior described above seems to imply something really broken with TB on my Ubuntu 12.04 box.

Any ideas?

--kachun

---

### Post by whitesmith on 2014-08-07
Have you tried renaming .mozilla when FF is shut down, and then launching it? That would force FF to create a completely new profile. I think your problems relate someway to the profile. If the server were at fault, then you would have a problem with Windows 7. Good luck.

---

### Post by Habitual on 2014-08-08
I actually had this experience also in Xubuntu 14.04 with Tbird 31.
I had to go to the mail server and *reset* my password to the same password I had been using.
It's weird.

---

### Post by Ka_Chun_Yu on 2014-08-11
Resetting the password to the old one was not an option.  So I took the suggestion of creating a new profile.  This is relatively easy by starting thunderbird with profile manager:

> thunderbird -P

Once it was connected to the mail server, all of my accumulated messages that hadn't downloaded for the old profile now appeared in the new one.  I then made some test copies of the mail files and folders (ignoring the *.msf files) from the old profile to the new one.  Thunderbird automatically read them, so I was satisfied that a straightforward *mv* command would work for the remaining mail files (no small matter, since I was dealing with almost 7 gigabytes of data). I renamed the new Inbox file, so that I would be able to move the old Inbox into the new profile.  Now I can slowly delete or move the recent messages around my old folder structure. (I will also have to migrate my address books and message filters, but I can take my time to do that.)

So far, everything has been running smoothly, and without any weird hiccups and hangups like I'd seen before.  Apparently I had accumulated so much crud over the years (through multiple versions of Ubuntu among other operating systems), that this detritus brought Thunderbird to a halt.

---


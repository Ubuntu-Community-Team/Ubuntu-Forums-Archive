---
title: "Setup Ubuntu 12.04LTS as Kiosk"
date: 2013-09-15
forum: General Help
---

### Post by Alan5127 on 2013-09-15
Hi All,

I have a need to set up a machine running Ubuntu 12.04LTS as a 'kiosk' style system.

What I want is for the machine to boot up straight into a user profile that has almost no rights.  That user profile will have a login password that our staff will know.

The machine will be physically secure (or at least, let's assume so since I acknowledge that if someone gets physical access things get dicey).

After the profile login password is entered by our staff, the machine will boot direct into a 'database' (actually probably just LibreOffice Calc will suffice) and will be used to enter peoples contact details.

I don't need any help on the Calc side itself (at least not in this posting).

What I want is for users of the system not to be able to do anything other than enter data in the spreadsheet, save the file (we'll probably code Calc to autosave after each enter anyway), and exit from it.  If they do exit, then I want the machine to completely close down, and not present a desktop or give access to any other functionality.

To administer the machine, we'll have a second user account with normal access levels.


I already have the machine booting up and opening Calc (and the file itself) automatically, so what I need help on is locking the profile to stop people breaking out to the desktop / broader OS.

Is that possible?  If so, how do I go about it?

Thanks in advance,

Alan.

---

### Post by derekpock on 2013-09-15
Yes this is possible.  [http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
This is for the GNOME version, let me know how far you can get with unity in the way.
Ubuntu-Tweak may also be useful for locking down some unity settings. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Alan5127 on 2013-09-15
Hi Derek,

That's great - I will go along that path as far as I can, then come back here if I get stymied at any point.

Thanks,

Alan.

---

### Post by Alan5127 on 2013-09-15
Hi Derek,

i have followed the instructables tutorial to Step 6:

[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/step6/Set-up-Kiosk-Desktop-Mode-in-Xsessions/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/step6/Set-up-Kiosk-Desktop-Mode-in-Xsessions/)

This is where it diverges from my requirement.

It asks me to set up an XSession Dektop entry, and then a shell script to run Chromium, whereas I will be running Calc.

I have already gotten the resticted profile booting directly into Calc and opening the file, so can I just ignore Step 6 entirely, or should I be replacing my use of the 'Startup Applications' feature with a shell script to better lock down Calc?

Thanks,

Alan.

---


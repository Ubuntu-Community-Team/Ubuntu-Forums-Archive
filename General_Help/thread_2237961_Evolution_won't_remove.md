---
title: "Evolution won't remove"
date: 2014-08-05
forum: General Help
---

### Post by Brandon_MacEachern on 2014-08-05
I am at wits end here, I can not get Evolution to remove completely, and the addressbook factory, calendar factory and registry source keep always running at boot.  It's not in startup applications, and I purged evolution..  But every time a calendar event happens, it still pops up.

I went back to thunderbird and don't understand why I can't just trash the stupid thing.

I tried this:  sudo apt-get --purge remove evolution evolution-plugins evolution-common
But this didn't work, and only ended up removing my dconf-editor too.

---

### Post by claracc on 2014-08-05
Perhaps this link can help you:

[http://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](http://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution)

---

### Post by Brandon_MacEachern on 2014-08-05
Hasn't worked actually.  It's still there running in the system and won't go away.  In the clock menu it has calendar entries too from Evolution still present also.

Where is this possibly starting automatically?  Something must be launching it.

---

### Post by ian-weisser on 2014-08-05
Evolution-data-server is the package that keeps appointments, calendar entries, contacts, and communicates that data to the rest of the system using dbus.
E-d-s is a set of services that start automatically on user login.

You can uninstall it, but be warned that a lot of services in Unity depend upon it...and you may start getting mysterious errors because of that.
If you *really* don't want e-d-s integrated into the desktop, you might consider a different Desktop Environment (kubuntu, xubuntu, etc.)

---

### Post by Brandon_MacEachern on 2014-08-05
Well it wasn't integrated like this before I installed Evolution.  Why is it such a problem to remove something I installed?  Even after removing Evolution, it shouldn't still be syncing my calendars, being they were removed..

This seems silly.

---

### Post by ian-weisser on 2014-08-06
> **Brandon_MacEachern said:**
> Well it wasn't integrated like this before I installed Evolution.

Yes, it probably was. Ubuntu is designed to have it 'integrated like this' from the very first boot.
But since you weren't using Evolution to manage a calendar or contacts, there was no data to share. But e-d-s was still there.

What do you want to do?
Do you want to delete the shared data?
Do you want to uninstall e-d-s?
Do you want to try a less-integrated Desktop Environment?  (overkill, perhaps, but has satisfied others)

---

### Post by Brandon_MacEachern on 2014-08-06
No, it was NOT like this.  There was no "Add Event" button in the gear menu, now there is.  There was no calendar data in the menu, now there is.

I should not have to switch desktop environments just to go back to the way it was before even using Evolution.  That is a severe flaw no matter if it's integrated.  I booted up my other Ubuntu machine and it does not have those Evolution processes running but yes are present in /usr/lib/Evolution.  Does not have things like "Add Event" in the gear menu though, which is exactly what I am saying.

If you are saying I should switch desktop environments, then you just don't know how to roll it back.  Yes I want the data gone, when I give it the removal command to also remove configuration, it should remove data too, to a state before it was installed, so it should STOP syncing my calendars.

If I remove my account from Evolution, then remove it, calendar data will be gone, but "Add Event" remains.  It should not remain because Evolution is gone, and on a new Ubuntu install with Evolution never have being installed in the first place yet, that button is NOT present.

And also, Evolution-Calendar-Factory, and Evolution-Source-Registry continue to run, taking up 40MB of RAM.  I would like that gone.  On a new Ubuntu install without ever touching Evolution, those processes are NOT starting at login taking up RAM.

So I am not wrong, this is NOT how it was before.  If you don't know how to fix it that's fine, but do not recommend I switch desktop managers because of it.

---

### Post by ian-weisser on 2014-08-06
How strange.

I have installed and uninstalled Evolution several times over the years, including once today in a VM to test if I could recreate your issue.
Sadly, I was unable to reproduce your problem. On a fresh test install, 'add events' did not remain for me after uninstall. The e-d-s processes ran at first-use instead of login (good, it's improved!), and did not occupy significant RAM when not in use.

---

### Post by Brandon_MacEachern on 2014-08-08
Yea sadly not the case here.  So I don't know what to do.  I don't know what could possibly be triggering it if it's not in Startup Applications (and I did have it show hidden items).

---

### Post by karinainmaz on 2014-08-24
I would love to delete evolution but have read that it is difficult and you need to reinstall some other things afterward.  Obviously I am not proficient at these things and frankly, just afraid to do it.  Any suggestions......

---

### Post by ian-weisser on 2014-08-24
> **karinainmaz said:**
> I am not proficient at these things and frankly, just afraid to do it.  Any suggestions......

Please post the result of the following terminal command, which will make no changes to your system:
```
sudo apt-get remove --simulate evolution
```

---


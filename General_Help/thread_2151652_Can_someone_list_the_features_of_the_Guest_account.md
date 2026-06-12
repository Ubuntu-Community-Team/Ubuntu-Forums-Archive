---
title: "Can someone list the features of the Guest account?"
date: 2013-06-05
forum: General Help
---

### Post by Cursed Lemon on 2013-06-05
I'm having a little bit of trouble finding all of the specifications of what the guest account does, all its security features (and holes?) and whatnot.

---

### Post by slickymaster on 2013-06-05
Any Ubuntu user by default can access the home directory of any other user on the same computer. However, Ubuntu's built-in Guest Session does not have this access. A user account designated for guests and the guest session feature are not quite the same thing. The guest session feature is convenient and secure, but does have limitations. For instance it does not allow guests to log in from the login screen, but can only be launched from a regular user session.

You might want to see this [GuestAccount]("https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount"), on wiki.

---

### Post by zombifier25 on 2013-06-05
Well, the guest account is identical to a normal (non-root, non-admin) user, except for some key differences:
1. The home folder is stored in the temp /tmp folder, (/tmp/<random_characters> to be exact) instead of the more permanent /home for regular users.
2. Anything guest does will be wiped out the moment he/she logs out, and a new guest account will be created when someone uses guest again. The /tmp folder itself is wiped every boot.

Other than that, there is nothing a normal account can do that the guest can't (that is, other than storing files permanently) Of course, the guest, like a normal user, cannot modify system files without the admin's permission. Everything is stored in the guest's home.

---

### Post by grahammechanical on 2013-06-05
What security concerns do you have? List those concerns and then try to use a guest session to do what you think that a guest session user should not be able to do.

I can tell you this. A guest session will not save documents created during the guest session. Files created in a guest session are lost when that session is ended. A guest session user cannot shut down the machine. Allowing a guest session to do that would risk a logged in user losing work. Shut down on a guest session comes back to the log in screen. The logged in user has to log back in and select shut down for the machine to actually shut down.

Regards.

EDIT. I just checked and I sit corrected. A guest session will actually shut down a machine even though I was logged in. I am not sure I would like that in a employment environment where a person gets turfed off the machine by a visiting manager who does not have an account on that particular network.

This is on saucy salamander. I was hoping that a reboot would restore my user session but it did not. Still I only had Chromium open. I wonder what would happen if I was using Libreoffice and editing some files?

---

### Post by zombifier25 on 2013-06-05
> **slickymaster said:**
> The guest session feature is convenient and secure, but does have limitations. For instance it does not allow guests to log in from the login screen, but can only be launched from a regular user session.

Actually, last time I checked (which is about 6 seconds ago) you can do that. Since 11.04 (or 11.10) I think. Before that you can only enter guest session via other users.

> **grahammechanical said:**
> A guest session user cannot shut down the machine.
Unless s/he is the only user logged on. But yeah, the guest cannot shutdown the machine if there are other users logged in. Same with other non-admin users really.

---

### Post by Cursed Lemon on 2013-06-05
Basically, what I'm trying to do is find the best solution for "kiosk" computers here at my job, that will be used by contracted employees on the fly as the cycle in and out of our workplace. 

Ideally I'd like it so that the guest account cannot modify the file system (I don't know if this is something I have to do with permissions on the whole root system, or what have you), and I'd like for the guest session to be wiped clean after they log out (which apparently it already does). The only thing that they need to be able to do is access the internet, view PDFs, and perhaps use LibreOffice.

---

### Post by slickymaster on 2013-06-05
> **zombifier25 said:**
> Actually, last time I checked (which is about 6 seconds ago) you can do that. Since 11.04 (or 11.10) I think. Before that you can only enter guest session via other users....

You can be right, but thing is I don't see that possibility on my Saucy machine. Strange...

---

### Post by zombifier25 on 2013-06-07
> **Cursed Lemon said:**
> Basically, what I'm trying to do is find the best solution for "kiosk" computers here at my job, that will be used by contracted employees on the fly as the cycle in and out of our workplace. 

Ideally I'd like it so that the guest account cannot modify the file system (I don't know if this is something I have to do with permissions on the whole root system, or what have you), and I'd like for the guest session to be wiped clean after they log out (which apparently it already does). The only thing that they need to be able to do is access the internet, view PDFs, and perhaps use LibreOffice.

Well, the guest account already does all that (not able to modify root, automatically wipes itself clean every log out, everything else normal)

---


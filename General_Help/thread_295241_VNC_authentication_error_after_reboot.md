---
title: "VNC authentication error after reboot"
date: 2006-11-07
forum: General Help
---

### Post by abobo on 2006-11-07
I setup a user to automatically log in on boot.
From System->Preferences->Remote Desktop I setup a password.

From a different machine when I launch my UltraVNC client I cannot as many times as I need.

If I reboot the Ubuntu Edgy box, the user is automatically logged in as usual.  If I attempt to connect from my UltraVNC client I will get a VNC authentication error.

I will repeatedly get this error until I go back to:
System->Preferences->Remote Desktop 
And retype in my password.

The password (listed as **'s) is still there from before.

I also checked this file:
~/.gconf/desktop/gnome/remote_access/%gconf.xm

Specifically this entry:
<entry name="vnc_password" mtime="1162733746" type="string">
<stringvalue>encrypted password</stringvalue>
</entry>

It appears to be unchanged between reboots.

Does anyone have any suggestions for me.  This is really annoying since I often have to do this while I am configuring the machine.

I am relatively new to Linux, so if you need information from me I would appreciated it if you could tell what command (or where) to get the information you need.

I am using all the standard packages from Edgy using the Synaptic Package manager.

TIA

---

### Post by bclinton on 2006-11-08
I am running into this same issue. If you get the fix could you let me know too?

Thanks

---

### Post by gumby1 on 2006-11-11
I just beat my head on the desk (again) after running into this problem too. I decided to look here to see if anyone else was having this problem too. Glad its not me. I hope someone finds an answer.

---

### Post by at0mic on 2006-11-13
hi,

this is a known bug for edgy. 

[http://ubuntuforums.org/showthread.php?t=79069&highlight=vnc](http://ubuntuforums.org/showthread.php?t=79069&highlight=vnc)

between this annoyance and the general sluggishness , its back to dapper for me

---


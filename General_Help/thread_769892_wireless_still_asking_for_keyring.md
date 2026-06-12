---
title: "wireless still asking for keyring"
date: 2008-04-26
forum: General Help
---

### Post by gearshifter on 2008-04-26
Even with the hardy upgrade it still asks me for the keyring.  

I tried removing the wireless network from the list of networks and removing the keyring.

Still asks even I set up the network over again.


Anyone know how to fix this?

I have the computer set to autologin-  does that have anything to do with it not remembering the password?

Please help me.

thanks

---

### Post by gradysghost on 2008-04-27
I have the exact same issue.  I also have autologin selected.  I will try turning autologin off and will post back.  It's most obnoxious, and I don't see a setting anywhere to specify that the keyring should not be prompted for.

---

### Post by ghost_ryder35 on 2008-04-27
i do belive autologin is the culprit here.

---

### Post by gradysghost on 2008-04-27
Yup.  It certainly is.  I just disabled auto-login, rebooted, and logged in properly.  No issues.  The PC went straight online via wireless.  My weather panel item even updated on its own at boot time.  Autologin is definitely the culprit.

---

### Post by ghost_ryder35 on 2008-04-27
theres a way around it i used in feisty fawn...
 
"
When using Feisty Fawn with Network Manager controlling your wireless **[COLOR=#ff0000]it[/COLOR]** adds **[COLOR=#ff0000]the[/COLOR]** WEP and WPA code to **[COLOR=#ff0000]the[/COLOR]** keyring manager, in some cases this causes problems and is annoying since you want to be able to log into your computer and be connected automatically to **[COLOR=#ff0000]the[/COLOR]** internet. With **[COLOR=#ff0000]the[/COLOR]** keyring manager you have to manually enter your keyring password every time before you are allowed to connect to **[COLOR=#ff0000]the[/COLOR]** wireless network. To remove this keyring password prompt,

**sudo apt-get install libpam-keyring**
**sudo gedit /etc/pam.d/gdm**
and add this line:
**@include common-pamkeyring** 
to **[COLOR=#ff0000]the[/COLOR]** bottom of your /etc/pam.d/gdm file, Then reboot and enjoy.
 
"

---


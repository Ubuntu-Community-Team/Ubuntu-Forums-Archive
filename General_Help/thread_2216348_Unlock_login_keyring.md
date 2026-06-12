---
title: "Unlock login keyring"
date: 2014-04-11
forum: General Help
---

### Post by Kojak Peg on 2014-04-11
Hi Everyone
In the last few days I've been getting an unlock login keyring prompted whenever I start up chrome. All I have to do is close the dialogue box, but why has it suddenly begun happening and how do I stop it 

Many Thanks

---

### Post by slickymaster on 2014-04-11
[Chrome asks for password to unlock keyring on startup]("http://askubuntu.com/questions/31786/chrome-asks-for-password-to-unlock-keyring-on-startup")

---

### Post by trag on 2014-04-11
[COLOR=#333333][FONT=UbuntuRegular]In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. [/FONT][/COLOR]
[COLOR=#000000][FONT=PT Sans Caption][/FONT][/COLOR]

[LIST=1]
[*][COLOR=#333333][FONT=UbuntuRegular]Open Applications --> Accessories -->Password and Encryption Keys[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Right-click on the "login" keyring[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Select "Change Password"[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Enter your old password and leave the new password blank[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"[/FONT][/COLOR]
[/LIST]

---

### Post by gifford on 2014-04-11
I am curious as to why when opening the chrome browser you are asked about login keyring prompt? Are you referring to Ubuntu giving you the prompt? Or is Chrome asking you to sign in?
What version of Ubuntu and Chrome are you using?

---

### Post by grumblebum2 on 2014-04-11
Have a look in seahorse and see what chrome may have stored there.

---


---
title: "google chrome keying password?"
date: 2014-04-19
forum: General Help
---

### Post by frank18 on 2014-04-19
Hi guys how can i get rid of Google Chrome keying password notification whenever i open the browser?

---

### Post by coldcritter64 on 2014-04-19
Note what the request is actually telling you (particularly what is bolded),
> The **login keyring did not get unlocked** when you logged into your computer.

Have you changed your user login (sudo) password recently?  

The keyring not being unlocked can occur when an original installation password is still in the keyring setup but the user changes their password, leaving the 2 out of sync. Any login keys stored in the original keyring when used will give that very error (like google chrome for instance needing to access keys in your case).

I am not on ubuntu, and I think the location may vary in later Ubuntu releases (not sure though), but to fix means deleting the old login keyring at $HOME/.gnome2/keyrings/login.keyring and restarting the installation (logging out may work, I usually restart the machine, but that may not be entirely necessary).
$HOME is a system variable for your users home folder.

Use the next command in a terminal to check where it is in your install,
```
locate login.keyring
```

locate and delete that file and restart. You will _lose any stored credentials_ and will need to either _*save details first*_ or redo from scratch keys for any application using the login keyring currently. The new keyring generated on restart will use the current sudo password matching the 2 up again, getting rid of that request box. Cheers.

---

### Post by monkeybrain20122 on 2014-04-19
It is a google bug that affects some people, and not just on Ubuntu. I have never seen it on Ubuntu, but on Manjaro Linux (and I read similar reports on OSX), I don't remember how I fixed it, but there is a lot of info on the internet, just google it.

---

### Post by trag on 2014-04-19
Here  is the fix **Make Keyring Accessible Without Password:**[COLOR=#000000][FONT=PT Sans Caption][/FONT][/COLOR]
[COLOR=#000000][FONT=PT Sans Caption][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=PT Sans Caption][/FONT][/COLOR]

[LIST=1]
[*][COLOR=#333333][FONT=UbuntuRegular]Open Applications --> Accessories -->Password and Encryption Keys[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Right-click on the "login" keyring[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Select "Change Password"[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Enter your old password and leave the new password blank[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"[/FONT][/COLOR]
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]As the message states: This will expose all passwords saved in the keyring (e.g. email passwords) to anyone using your computer or having access to your files and is not recommended. 
Good luck
trag

[/FONT][/COLOR]

---

### Post by frank18 on 2014-04-20
> **trag said:**
> Here  is the fix **Make Keyring Accessible Without Password:**

[COLOR=#333333][FONT=UbuntuRegular]In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. 
[/FONT][/COLOR]


[LIST=1]
[*][COLOR=#333333][FONT=UbuntuRegular]Open Applications --> Accessories -->Password and Encryption Keys[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=UbuntuRegular]Right-click on the "login" keyring[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=UbuntuRegular]Select "Change Password"[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=UbuntuRegular]Enter your old password and leave the new password blank[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=UbuntuRegular]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"[/FONT][/COLOR] 
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]As the message states: This will expose all passwords saved in the keyring (e.g. email passwords) to anyone using your computer or having access to your files and is not recommended. 
Good luck
trag

[/FONT][/COLOR]

Thanks actually i did that per instructions from here link: but when rebooting there it came again, <biiip> ,i had problems with firefox streaming videos that's why i installed google chrome but today i decided to do new fresh install and resolved all my issues with fire fox so i'm back on fire fox again  and <biiip> google chrome, beside it would take to long to enter a site it would say waiting for add-block,i never liked google chrome anyway.

 [http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/)

---


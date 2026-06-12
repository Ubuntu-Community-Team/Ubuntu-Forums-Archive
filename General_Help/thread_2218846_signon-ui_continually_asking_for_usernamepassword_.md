---
title: "signon-ui continually asking for username/password after upgrade to 14.04"
date: 2014-04-22
forum: General Help
---

### Post by dalekky on 2014-04-22
This is the exact problem, posted by someone else on askubuntu.com -

[http://askubuntu.com/questions/451245/signon-ui-enter-your-credentials-dialog-on-desktop](http://askubuntu.com/questions/451245/signon-ui-enter-your-credentials-dialog-on-desktop)

Anyone found a solution yet? The prompt won't go away. I have no idea what it is asking me for.

---

### Post by ajgreeny on 2014-04-22
Just as a trial, see if you can use Ctrl+Alt+F1 to get to a command line, login at that with username and password, then rename the hidden **.Xauthority** file in your home as **.Xauthority-backup** and see if you can then login to the GUI when a new .Xauthority file should be generated.

Have you mistakenly used **sudo** for any GUI applications instead of the required **gksudo**?  That can sometimes mean that ownership of some files in your home is changed to root, causing the problem you see here.  What is the current output of ```
ls -al .Xauthority
``` from the command line, if you can get to it.
It should look something like```
-rw------- 1 *user user* 157 Apr 22 09:27 .Xauthority
``` If it says **root root** where it should say **user user**, that will be the reason

---

### Post by dalekky on 2014-04-22
The current output of ls -al .Xauthority is as above with my user user, not root root.
Now I will try to generate a new .Xauthority file.

---

### Post by dalekky on 2014-04-22
Generated a new .Xauthority
The username, password box still pops up after logging back into gui.

---

### Post by dalekky on 2014-04-25
This problem disappeared by itself for 2 days. It came back again this morning.
I never touched anything or changed anything.

EDIT: Ok I worked out that it only went away, because during those 2 days I had no internet connection.
Problem came back as soon as I had working internet connection again.

---

### Post by trag on 2014-04-26
get rid of it following this procedure [COLOR=#333333][FONT=UbuntuRegular]In order to remove the Unlock Login Keyring dialog set the password for the keyring to an empty password. This prevents being prompted for a password. [/FONT][/COLOR][COLOR=#000000][FONT=PT Sans Caption][/FONT][/COLOR]

[LIST=1]
[*][COLOR=#333333][FONT=UbuntuRegular]Open Applications --> Accessories -->Password and Encryption Keys[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Right-click on the "login" keyring[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Select "Change Password"[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Enter your old password and leave the new password blank[/FONT][/COLOR]
[*][COLOR=#333333][FONT=UbuntuRegular]Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"[/FONT][/COLOR]
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]As the message states: This will expose all passwords saved in the keyring (e.g. email passwords) to anyone using your computer or having access to your files and is not recommended. [/FONT][/COLOR]

---

### Post by dalekky on 2014-04-27
I found a different solution to my issue.

             In my case, it was a Yahoo account in Online Accounts which was the culprit.


  Symptoms of a faulty Yahoo account in Online Accounts manifest as the  following:
When you go to System Settings > Online Accounts, click on your Yahoo  Account in left column, then click on "Edit Options", there will be NO  information displayed - window will be blank instead of the expected  username & password fields.


  To fix a faulty Yahoo account in Online Accounts you need to delete  the account and re-add it:
Go to System Settings > Online Accounts, click your Yahoo Account in  left column, click "Remove Account", then click "+ Add account..."
The username & password fields will display as expected and you can  fill out your account info.
Congratulations, the "Enter your credentials" popup is now gone when you  reboot.

---


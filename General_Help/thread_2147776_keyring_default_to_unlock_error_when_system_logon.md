---
title: "keyring default to unlock error when system logon"
date: 2013-05-23
forum: General Help
---

### Post by nilguy11 on 2013-05-23
Hello,

At each startup, kubuntu asks me for the password for the keyring.  	Code:

 	
An application wants access to the keyring 'Default', but it is locked.  Enter password for keyring 'Default' to unlock 
Even if I choose:
to login it says pssword wrong 
n how to just get rid of such error 
i hav seen the forums but most solution are gnome based

but i dont use gnome its kubuntu kde 12.04 lts version
Is there a way to remove this?

---

### Post by Eaton on 2013-06-09
I had this problem recently in Ubuntu.  I expect my solution will be the same for you.  
The Keyring asks for its password because it is different from your login password.  If you set the Keyring password to your login password, it won't keep asking you for it.  To change your Keyring password: 

1. Navigate to Passwords & Keys (probably in System-Tools/Preferences). It will open in the Passwords folder.  
2. Right-click on "Passwords: default" and select "Change Password". 
3. Now enter your usual, computer, login password.  
4. Click on File/Quit

Voila!

---

### Post by markbl on 2013-06-09
OP, if you are using auto-logon like I do then I suspect you want to get rid of that prompt. The way you do that is to do as the reply above says but enter an empty password in the default key.

---


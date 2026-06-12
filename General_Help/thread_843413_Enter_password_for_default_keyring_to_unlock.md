---
title: "Enter password for default keyring to unlock"
date: 2008-06-28
forum: General Help
---

### Post by Blackprint on 2008-06-28
I keep getting this error message when I am trying to save the password to my shared windows folders. I have tried every password I can think of but nothing takes. I would really like to access my shares without having to type the password in every time as I want to use this as a media box.

I have a program installed "Passwords and Encryption Keys" but I have no idea how to use it! Bit of a linux noob but linux runs so much more quickly than windows.

---

### Post by VMC on 2008-06-28
> **Blackprint said:**
> I keep getting this error message when I am trying to save the password to my shared windows folders. I have tried every password I can think of but nothing takes. I would really like to access my shares without having to type the password in every time as I want to use this as a media box.

I have a program installed "Passwords and Encryption Keys" but I have no idea how to use it! Bit of a linux noob but linux runs so much more quickly than windows.

Maybe I'm missing your point, but the only Keyring I can think of is the Evolution Mail Keyring. It's just another layer of security. Several updates ago we didn't have it.  I'm not sure if you want to turn it off or store this in some password program. It should be just your user password. 

What is the error message say? Maybe you can start 'evolution' through your Terminal and see if any error messages come out.

---

### Post by Blackprint on 2008-06-28
Hi,

Sorry I may not have been clear. I'll start at the beginning. I click Places >> Connect to Server. Then I type in all the details (Server, Share, Username and Domain) and press OK. Then it asks me for the password. I type in my normal Windows password but there are three options below:

Forget password immediately
Remember password until you logout
Remember password forever

If I select to remember the password it gives me the dialogue:

Enter password for default keyring to unlock

It also points to a file in usr/lib/gvfs/gvfsd-smb

My guess (being a linux noob) is that this is the key which saves my Windows password and it wants the default password to continue. But I havnt set any passwords.

I also got the same error but pointing to a different file in the same directory when trying to save my WPA key.

I've been researching and it looks like i need a keymanager but I dont know which one/where to get one.

---

### Post by Blackprint on 2008-06-28
ok new problem.

followed the advice here:

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

I now cannot do anything. the login screen shows but says authentication failed. I click ok but it brings the same window up. I cannot type in the login text box, or click on the options button. basically cant do anything.

---


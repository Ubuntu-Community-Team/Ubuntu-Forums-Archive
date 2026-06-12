---
title: "[SOLVED] file sharing"
date: 2008-06-30
forum: General Help
---

### Post by dpwilson on 2008-06-30
I am trying to set up my desktop and laptop so that I can access files on both, (both have ubuntu 8.04).  I am not sure that I am going about it in the right way.  If I right click a folder and go to "sharing options", then select "share this folder", once I click "create share", I get the following error message...
[I]'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/I]

What must I do to get the permission to create a share and then, once I do, how would I connect to the other computer?

Any help is appreciated.

---

### Post by manfer on 2008-06-30
Without root privileges you can only share folders in your users home folder. You could share any other folder if you have root privileges. But if you don't mind to put your shares under user home folder I suggest you do so and not trying to share a folder that needs root privileges.

Then you would see the shares going to Places->Network.

---

### Post by plucky on 2008-06-30
> What must I do to get the permission to create a share and then, once I do, how would I connect to the other computer?

Did it install samba? If it did,then you have to log off and back on to get the correct permissions to share a folder in your home directory.

Goto Places > Network to see shared folders

Good Luck

---

### Post by dpwilson on 2008-06-30
OK, I guess logging off and back on did it. Is there a way to access the anything outside the home folder?  Thanks for the help.

---

### Post by soccerboy on 2008-06-30
```
sudo nautilus
``` should allow you to do it but it is highly dissuaded.  You don't want to expose critical system files to possible cracking/damage.

---

### Post by dpwilson on 2008-06-30
One more question, when I try to access a folder from the other computer it asks for a password, however, I didnt assign any password.  I tried the pasword I log on with and no dice there either.  Where would I get or assign the password from?

Sorry for any stupid questions, but am completely new to networking and file sharing.

---

### Post by plucky on 2008-07-01
> **dpwilson said:**
> One more question, when I try to access a folder from the other computer it asks for a password, however, I didnt assign any password.  I tried the pasword I log on with and no dice there either.  Where would I get or assign the password from?

Sorry for any stupid questions, but am completely new to networking and file sharing.

Did you try without a password? Just hit <enter> and see if it mounts your share.
Did you tick all the boxes when you set up the share?

My system doesn't ask for a password,so I am not sure what is going on here.

Good Luck

---

### Post by manfer on 2008-07-01
> **dpwilson said:**
> One more question, when I try to access a folder from the other computer it asks for a password, however, I didnt assign any password.  I tried the pasword I log on with and no dice there either.  Where would I get or assign the password from?

Sorry for any stupid questions, but am completely new to networking and file sharing.

It asks for user, domain and password.

If you are accessing from computer A to a share folder on computer B the username and password you have to type are the ones for computer B (the one with the share folders) and not user and password in computer A. The domain is just filled for you.

You would see you can tick an option to remember that user and password and maybe that way won't ask for it anymore.

---

### Post by dpwilson on 2008-07-01
[QUOTE=manfer;5296856]....the username and password you have to type are the ones for computer B (the one with the share folders) and not user and password in computer A. QUOTE]


OK, I will try that this evening when I get home.  I think by default it is giving me the username for the computer I am on, so I will change it to the one that I am accessing.  That makes sense.  Will let ya know how that works out.

Thanks.

---

### Post by dpwilson on 2008-07-02
Worked great.  Thanks to all who helped out.

---


---
title: "Transfer current ubuntu settings to another ubuntu comp?"
date: 2007-06-17
forum: General Help
---

### Post by m4ttjirM on 2007-06-17
Hi I have been using ubunto for a few days and I love it.

I have another computer in my house that wasn't in use before that I would like to install ubuntu on.  I would like it to have the SAME EXACT SETTINGS AND CONFIGURATION as my current computer

I thought there was a very simple way to transfer the files to the 2nd computer with a USB key drive.  I want my 2nd computer to be just like this one.

Is there any simple way to do this?  I googled the question so many times but I can't really find anything, I'd come here as a last resort.

Thank you,

Matt

---

### Post by m4ttjirM on 2007-06-17
Does anybody have any idea how to do this?  Is it possible?  I'm hoping it's an extremely simple task.

---

### Post by ACQ on 2008-04-29
I chose to necro this because I too would like to know if this is at all possible. A simple yes or no with an explanation would be fantastic.

I wanted to see if sbackup could do this, but haven't been able to try it yet.

Thanks

---

### Post by jken146 on 2008-04-29
If you copy everything in /home/yourUserName to the other computer (particularly the hidden files whose names begin with a .) your apps will take the same settings.  If you don't have the same username on both computers, you'll need to change the ownership of the files after you've copied them:
```
sudo chown -R userNameOnSecondPC:userNameOnSecondPC /home/userNameOnSecondPC
```


If you want to copy an entire ubuntu install, not just the user settings, I'm sure this is possible.

---

### Post by ACQ on 2008-04-29
> **jken146 said:**
> If you copy everything in /home/yourUserName to the other computer (particularly the hidden files whose names begin with a .) your apps will take the same settings.  If you don't have the same username on both computers, you'll need to change the ownership of the files after you've copied them:
```
sudo chown -R userNameOnSecondPC:userNameOnSecondPC /home/userNameOnSecondPC
```


If you want to copy an entire ubuntu install, not just the user settings, I'm sure this is possible.

Sweet, thanks for the reply.

Are desktop settings also stored in /home/username (GNOME and such)? If not, where?

---

### Post by jken146 on 2008-04-29
> **ACQ said:**
> Sweet, thanks for the reply.

Are desktop settings also stored in /home/username (GNOME and such)? If not, where?

Yes.  Everything that is specific to an individual user is within that user's $HOME directory.

---

### Post by ACQ on 2008-04-30
Man, that's elegant. Many of my questions about Linux would seem silly to the veteran user. Not to mention I have a hard time getting out of the restrictive and convoluted Windows registry mentality.

---


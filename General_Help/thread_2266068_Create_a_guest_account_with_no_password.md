---
title: "Create a guest account with no password"
date: 2015-02-19
forum: General Help
---

### Post by zathras1974 on 2015-02-19
I wish to create a guest account with no password. I am running UbuntuGnome 14.10 with Gnome 3.12.2. 

Now, before anyone starts lecturing me about the security risks, I have considered them and will not be using the account for my day-to-day work. Heck, I hope the account will _never_ be used. I have installed Prey 1.3.6 on the system and want a potential thief to see and use the guest account rather than try to hack my normal admin account. Hence the need for the guest-account bait.

I've secured the laptop with a BIOS password to prevent changing the boot order. So a thief will have trouble trying to wipe the system. Same with swapping out the HDD. So, apart from disassembling the system to reset the BIOS (a length I don't find likely a local thief will go to), I believe I've reasonably protected the system. 

The entire point I'm trying to achieve is to funnel a thief toward the guest account and let Prey do it's thing from there. 

I'm sure I'm not the only one who has thought of this idea, and am hoping someone else has conquered the beast. 

Thanks for any help that can be provided.

---

### Post by Frogs Hair on 2015-02-19
Ubuntu requires no password for the guest account and there is an arrow that appears in the password box.I was not aware that Ubuntu Gnome was set up in a different way. Do you have guest account at all ?

---

### Post by zathras1974 on 2015-02-19
Thanks for your reply. :)
I have created a guest account under "Users" in Gnome, but it asks for a password to be set. I have, for the moment, set it so that it will require the guest to set a password upon next login, but that seems a rather untidy solution. I have attempted to set a null password, but the "change" button remains greyed out unless I set a password of at least nine characters. 
I am familiar with the guest account under Unity, but it appears Gnome has not duplicated that function. :/

---

### Post by Frogs Hair on 2015-02-19
A user account regardless of name will require a password , but I did come across some documentation that may provide a starting point.

[https://help.ubuntu.com/community/PasswordlessGuestAccount](https://help.ubuntu.com/community/PasswordlessGuestAccount)

---

### Post by zathras1974 on 2015-02-20
That looks promising. I'll try that out and let you know if it works. Thanks! :)

---

### Post by zathras1974 on 2015-02-22
Unfortunately, that did not solve the issue. :cry:

Upon attempting to log-in with the guest account, I was confronted with a change password prompt before it would allow the execution of the desktop environment. I attempted to use a null password, to no avail. 

Any other suggestions, or should I keep the guest account in a perpetual state of "I'll set it next login"?

~Z

---

### Post by Frogs Hair on 2015-02-22
Starting point was written because the task seems to me to be complected. First, you would have to understand how Ubuntu implements the guest account and then apply it to the the default environment in Ubuntu Gnome.

 I find only outdated(2010)instructions for pre Gnome 3 versions of Ubuntu which would be use at your own risk. I also use prey on one device and haven't worried about it being disabled some how before the device was discovered missing.I don't usually leave electronics unattended outside the home where a theft would be covered anyway. Backups, either via cloud or removable device are always a good idea.

[http://ubuntuforums.org/showthread.php?t=1601911](http://ubuntuforums.org/showthread.php?t=1601911)

---

### Post by zathras1974 on 2015-02-22
> **Frogs Hair said:**
> Starting point was written because the task seems to me to be complected. First, you would have to understand how Ubuntu implements the guest account and then apply it to the the default environment in Ubuntu Gnome.

 I find only outdated(2010)instructions for pre Gnome 3 versions of Ubuntu which would be use at your own risk. I also use prey on one device and haven't worried about it being disabled some how before the device was discovered missing.I don't usually leave electronics unattended outside the home where a theft would be covered anyway. Backups, either via cloud or removable device are always a good idea.

[http://ubuntuforums.org/showthread.php?t=1601911](http://ubuntuforums.org/showthread.php?t=1601911)

I don't leave my stuff around either, I'm just OCD enough to plan for "what if". *shrug*

I guess I can set a password for the guest account, and just set it to auto-login after a specified time. I think that will achieve what I'm aiming for, albeit somewhat inelegantly. I'll set this thread as solved.

Thanks for your help. :)

~Z

---


---
title: "Password change. Possible bug?"
date: 2013-03-11
forum: General Help
---

### Post by l0nd0n on 2013-03-11
After my installation of Ubuntu 12.04, I removed the recovery console entries the from burg menu. I was messing around with user accounts and accidentally turned automatic login on. It, for whatever reason, did not keep the previously saved password and as a result will not allow sudo access. Every time I am prompted, my password is denied. I have tried leaving it blank and using the previous password with no avail. My computer is up to date and fully functional now (aside from sudo access which is essential for me), and I would like to keep it that way. So my question really is, what can I try to keep everything I've installed? Is there a command line hotkey for the burg menu that will allow me to boot from the recovery console despite being hidden and/or possibly removed?

---

### Post by schragge on 2013-03-11
Can you still log in on the first text console (**Ctrl**+**Alt**+**F1**)? To change back to GUI from there press **Ctrl**+**Alt**+**F7**. Also, there's the *pkexec* command which is sort of a poor man's *sudo*. Are you still able to perform administrative tasks in terminal with *pkexec*?

---

### Post by ajgreeny on 2013-03-11
I don't know burg, but for grub you need to hold **shift** at bootup to see the grub menu; it may be the same for burg.  Try it and come back again if it does not help.

Once in recovery mode follow [this]("http://www.psychocats.net/ubuntu/resetpassword") to reset your password.

---

### Post by l0nd0n on 2013-03-12
Sorry for the late response, I had college. The *pkexec* command was a no-go, however, from the *tty1* screen I typed the username, and it actually did work. 
I have the $ symbol, but have not the slightest idea on what to do to restore my user account back.
And I found an oddity, Super Boot Manager and Burg Manager both require my root password, which I leave blank, and will work by merely pressing Enter.
Yet, any other application will not work at all. I believe this might have something to do with the fact it has a different UI password confirmation screen and doesn't use the native password validation screen that most other programs use. 
And another thing that I found peculiar is that in User Accounts under Login Options it says "Password" followed by "None." Yet the sudo password is still in place, and seems to have changed (my problem).
But I know for a fact it would ask for a confirmation of current password ensued by the new password 2X. Right?
Apologies for my ramblings, all I really need to know is if its possible to use the tty1 screen to change my password again? Thanks for your responses, I much appreciate them.

---

### Post by c2tarun on 2013-03-12
> **l0nd0n said:**
> Sorry for the late response, I had college. The *pkexec* command was a no-go, however, from the *tty1* screen I typed the username, and it actually did work. 
I have the $ symbol, but have not the slightest idea on what to do to restore my user account back.
And I found an oddity, Super Boot Manager and Burg Manager both require my root password, which I leave blank, and will work by merely pressing Enter.
Yet, any other application will not work at all. I believe this might have something to do with the fact it has a different UI password confirmation screen and doesn't use the native password validation screen that most other programs use. 
And another thing that I found peculiar is that in User Accounts under Login Options it says "Password" followed by "None." Yet the sudo password is still in place, and seems to have changed (my problem).
But I know for a fact it would ask for a confirmation of current password ensued by the new password 2X. Right?
Apologies for my ramblings, all I really need to know is if its possible to use the tty1 screen to change my password again? Thanks for your responses, I much appreciate them.

Its my request, please be patient and be verbose in telling your problem. It is really difficult to understand that what is going on with you. I am no burg expert but I can guess that since you removed recovery mode option from your boot menu then you'll not be able to boot into recovery mode and the link shared few posts above to reset your password will not work for you. I also don't think that you can revert this without using sudo. I am not sure about the following solution, but if I remember correctly when you boot using live CD there is an option of booting into recovery mode. See if it is still there, if yes then boot into recovery mode, mount your root partition somewhere then try to add your user account to sudoer list. To add your username to sudoer list please follow instructions on [this]("http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line") page. 

Or even if you don't see an option "Boot into recovery mode" in Live CD, try booting in live CD and start ubuntu and then you can mount and try adding your account to sudoer list.

Just curious: how did you get burg on your system? Did you install it manually?

---

### Post by schragge on 2013-03-12
Log in on the tty1, and from the [COLOR=#008000]$[/COLOR] prompt run this:
```
pkexec adduser $USER sudo
```
Then reboot.

---


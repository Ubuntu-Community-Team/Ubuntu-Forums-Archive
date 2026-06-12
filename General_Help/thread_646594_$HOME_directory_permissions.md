---
title: "$HOME directory permissions"
date: 2007-12-21
forum: General Help
---

### Post by chrisndebb on 2007-12-21
Help!! I was screwing around with my /home file and set the directory to be "writeable by others" and now I can't even login. I get an error message "Users $HOME/.dmrc file is being ignored......Users $HOME directory must be owned by user and not writable by others."

I can get to a text prompt from the login screen but still denied access. Anybody know what I can do?

---

### Post by taurus on 2007-12-21
Boot into recovery mode from GRUB menu and at the prompt, run

```
chmod -R 755 /hom/**chris**
chown -R **chris**:**chris** /home/**chris**
chmod 644 /home/**chris**/.dmrc
shutdown -r now
```
_Assuming_ your login name is **chris**.

---

### Post by Pumalite on 2007-12-21
Don't you have an 'x' where you can just click and ignore the message?

---

### Post by zekica on 2007-12-21
I don't recommend you to leave your home folder writable, but you can login with writable home if you set **Allow login if all write permission on user's home directory** under **Security** tab in **Login window preferences**.

You will have to revert it to be non writable before you can login and set this.

---

### Post by Pumalite on 2007-12-21
I meant ignore the message to get IN the system; then change the permission as taurus suggested.

---

### Post by chrisndebb on 2007-12-21
That did it taurus. Thanks for the quick response.

---

### Post by gumpontheweb on 2007-12-22
I deleted my user and wanted to put it back and can't because when I login I get the same error!
Should I follows the steps too???
I am A Total Newbie and dont have a clue...
I read that I could erase thr group that has mu name to fix it? I think I'll make my own thread.

Here is my thread :
[http://ubuntuforums.org/showthread.php?t=647183](http://ubuntuforums.org/showthread.php?t=647183)

---


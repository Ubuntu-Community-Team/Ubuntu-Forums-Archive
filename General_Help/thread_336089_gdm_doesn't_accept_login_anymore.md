---
title: "gdm doesn't accept login anymore"
date: 2007-01-11
forum: General Help
---

### Post by QwUo173Hy on 2007-01-11
THE ORIGINAL POST DIDN'T CORRECTLY REFLECT THE PROBLEM I'M HAVING.. APOLOGIES! READ ON FOR THE CORRECTION.

After I enter my username/password, the screen goes blank momentarily, then X is rebooted (before the desktop starts up). I can log in via virtual terminal so my username/password are correct.

 I have been using the same system for the last few months and dont see what could have changed.

Can anyone please help? I'm not too terminal savvy and I need to check my emails.

Thanks,
Jarlath

---

### Post by DerHesse on 2007-01-11
Are you sure you do not have an xserver problem? If you can log in at the console but not to X soemething differnt is the problem. Any updates installed recently? Did you install manufacturer drivers for your graphics card?

[http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update](http://www.ubuntuforums.org/showthread.php?t=334839&highlight=update)

---

### Post by QwUo173Hy on 2007-01-11
I haven't done anything that I can think of lately. There are updates available but I did not install them. Since I can log in at the terminal. What command can I type when logged in as a user to run gnome (bypassing the gdm login screen obviously).

Also, if anyone has a workaround for this, that would be great too.

I'm using edgy.

Thanks,
Jarlath

---

### Post by QwUo173Hy on 2007-01-11
You're right, the password is not being rejected by GDM - the screen goes black for a moment and the X-Server seems to get restarted.

Can anyone help?

---

### Post by endless_dark on 2007-01-11
> **jarlath said:**
> You're right, the password is not being rejected by GDM - the screen goes black for a moment and the X-Server seems to get restarted.

Can anyone help?

I have a similar problem :(

---

### Post by QwUo173Hy on 2007-01-12
I've solved it. My hard drive was completely full (I ran "df /" from the console to find this out. X didn't have enough harddrive space to defragment whatever files it needed so it rebooted. I deleted over 1GB of stuff and now I'm back in X. Only problem now is that some of my applets dont work but I'd say reinstalling will help.

---


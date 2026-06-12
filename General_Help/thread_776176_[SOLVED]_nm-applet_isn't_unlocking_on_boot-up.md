---
title: "[SOLVED] nm-applet isn't unlocking on boot-up"
date: 2008-04-30
forum: General Help
---

### Post by NullHead on 2008-04-30
Well I already posted this, but I'll do it again. 

When I boot the network manager wants access to the keyring. I have to enter the password every time I boot and it gets annoying. 

Does anyone have an idea on how to make this automatically unlock on boot? it used to unlock :(

---

### Post by raiwo on 2008-05-01
I am having same problem, they fixed it in 7.10 but now it's back and it is bloody annoying!

So, HOW TO DISABLE KEYRING MANAGER???

edit: just found bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/223076](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/223076)

---

### Post by raiwo on 2008-05-01
Just found a solution in this one: delete existing key, reboot & when keyring manager next time asks a new password for keyring just press OK without entering any password. It will ask if you're sure about it just click yes & after that your network should start automatically on startup.

---

### Post by NullHead on 2008-05-01
Thak you, This worked for me! :D

---

### Post by darco on 2008-05-13
> **raiwo said:**
> Just found a solution in this one: delete existing key, reboot & when keyring manager next time asks a new password for keyring just press OK without entering any password. It will ask if you're sure about it just click yes & after that your network should start automatically on startup.

Where is this Keyring? I see many and do not know which to delete.

thxs
darco

*nevermind, I found it /home/user/.gnome2/keyrings and it worked!!!

---

### Post by talz13 on 2008-05-27
I have a question, if you delete your keyring, do you have to re-enter your WPA key?  The only reason I ask is because I'm trying to remotely fix this on my grandpa's pc, and I'd rather not have to walk him through inputting his WPA key again.

If I delete the key and he can just enter the blank password I'll go ahead and do that.

---

### Post by NullHead on 2008-05-28
> **talz13 said:**
> I have a question, if you delete your keyring, do you have to re-enter your WPA key?  The only reason I ask is because I'm trying to remotely fix this on my grandpa's pc, and I'd rather not have to walk him through inputting his WPA key again.

If I delete the key and he can just enter the blank password I'll go ahead and do that.

Yes I believe you'll have to re-enter the password into the keyring and then after you put in the wpa/wpa* key it'll ask you for a keyring password. The idea here is to remove the keyring password. So you're deleting the keyring and making a new one. So if you have any network mounts or a wifi connection than you'll have to put them back into the keyring when prompted for passwords. **make sure not to put in a keyring password!**

---

### Post by wkulecz on 2008-05-28
Storing remote system passwords unecrypted is a less than desirable solution!

--wally.

---

### Post by NullHead on 2008-05-28
This is true, but the keyring manager will not save your user or root password. I can use this solution because I just connect to my wireless network and that's all I use the keyring manager for. So yes it is insecure, but it works for me.

---

### Post by Ux64 on 2008-05-30
> **wkulecz said:**
> Storing remote system passwords unecrypted is a less than desirable solution!

True. Strange question is, why passwords aren't then stored using login password as encryption key? And then when passwords are needed it could be possible to choose if you wan't to allow access to keyring or not, but not to prompt for password. Passwords are also stored in encrypted format. Naturally with proper salting etc.

---

### Post by dogeth on 2008-06-27
Worked like a charm for me.  Ta.  
Hardy Heron version.

---

### Post by tux_rox on 2008-09-02
Had the same problem with the Evolution alert notifier and deleting the keyring worked perfectly.  Ubuntu 8.04.

---

### Post by bartlomiejp on 2008-09-27
It works well for me as well, but you don't have to delete a keyring, just choose change password option, enter old one, and the new just leave blank.

---

### Post by fballem on 2008-10-01
There are more detailed instructions on how to change the password for the keyring in this post: [http://ubuntuforums.org/showthread.php?p=5886460#post5886460](http://ubuntuforums.org/showthread.php?p=5886460#post5886460)

Hope this helps,

---

### Post by ed5000 on 2008-12-30
That worked. Thanks!

---


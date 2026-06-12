---
title: "How to unlock keyring automatically for autologin user"
date: 2012-12-17
forum: General Help
---

### Post by tigerchan on 2012-12-17
Dear all,
  As stated in the following link, a window will popup for the user to input the keyring password when it is autologin:
[https://answers.launchpad.net/ubuntuone-client/+question/85771]("https://answers.launchpad.net/ubuntuone-client/+question/85771"):
  [I]If you are autologin'ing to your machine, gdm uses su to become your user, without ever using the password. As a result pam-gnome-keyring can't pass the password along, and you need to unlock the gnome-keyring by entering the password.

  If you are autologin'ing to your machine, you can set your gnome-keyring password to blank. You will no longer be prompted to enter the gnome-keyring password, but your credentials/passwords/etc. will be stored on your system in plaintext, where anyone (i.e. bad hacker) who gains access to your system could see them.[/I]

I don't think it is a good idea to set the keyring password to blank. Is there any other way to skip the input-keyring-password window when autologin?
Thanks.

---

### Post by raja.genupula on 2012-12-17
[http://askubuntu.com/questions/68292/how-to-auto-unlock-keyring-manager](http://askubuntu.com/questions/68292/how-to-auto-unlock-keyring-manager)

---

### Post by tigerchan on 2012-12-17
Thank you raja for the information.
But the solution in the link you provided, was still the same one: *set the keyring password to blank*. This might damage the security of the OS.
Is there any other way?

---

### Post by raja.genupula on 2012-12-17
OK [http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot](http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot)

---

### Post by tigerchan on 2012-12-17
Thanks again, raja. 
But I can still see nothing but the blank keyring password, although this new link is a bit longer.

---


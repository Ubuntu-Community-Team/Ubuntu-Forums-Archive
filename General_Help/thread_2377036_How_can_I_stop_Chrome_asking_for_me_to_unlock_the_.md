---
title: "How can I stop Chrome asking for me to unlock the keyring?"
date: 2017-11-08
forum: General Help
---

### Post by orschiro on 2017-11-08
Every time I start Chrome, it asks me to unlock my Gnome Keyring. Not only once. I have to enter my password approx. 9 times for this message to disappear. 

Does someone have a similar problem?

I use Chrome 62 on Ubuntu 17.10.

Ideally I would love to get rid of this message completely!

Thank you.

---

### Post by RobGoss on 2017-11-08
You can try this fix as indicated in this thread, [https://askubuntu.com/questions/791950/how-to-get-rid-of-google-chrome-keyring](https://askubuntu.com/questions/791950/how-to-get-rid-of-google-chrome-keyring)

I do believe you can also delete the default files for keyring in the Google Chrome folder that should get rid of the annoying pop up each time you open Chrome

---

### Post by deadflowr on 2017-11-08
Switch to basic for the password store
basic is chrome's builtin password storage, but it stores password's in plain text.
This is why chrome defaults to using the Ubuntu keyring. They store password encrypted.

To set it to default to use basic try this
copy the google-chrome.desktop file from /usr/share/applications into your home folder applications folder:
```
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
```
then open gedit (you can open it dircly with the following command:
```
gedit ~/.local/share/applications/google-chrome.desktop
```
in gedit Find each of the lines that begin with Exec and add --password-store=basic like so
```
Exec=/usr/bin/google-chrome-stable --password-store=basic %U
```
then save and now when you launch chrome you should never be asked for your keyring.

More on password store here:[https://askubuntu.com/questions/525019/where-are-my-browser-passwords-stored]("https://askubuntu.com/questions/525019/where-are-my-browser-passwords-stored")

---

### Post by orschiro on 2017-11-08
Thank you both very much!

I will go with the solution explained by @deadflowr.

---

### Post by vasa1 on 2017-11-08
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by orschiro on 2017-11-09
Thanks guys! I marked this thread as solved. 

The solution to modify the .desktop file and have it use the basic password storage works like a charm! :-)

---

### Post by orschiro on 2017-11-13
Just saw that this is already extensively covered in the Arch Wiki [1].

[1] [https://wiki.archlinux.org/index.php/Chromium/Tips_and_tricks#Force_a_password_store](https://wiki.archlinux.org/index.php/Chromium/Tips_and_tricks#Force_a_password_store)

---

### Post by RobGoss on 2017-11-13
Glad to you were able to solve your issue

Have a great day

---

### Post by orschiro on 2017-11-13
> Have a great day

Likewise, thank you for all your help! :-)

---

### Post by lexj on 2018-02-26
> **orschiro said:**
> Every time I start Chrome, it asks me to unlock my Gnome Keyring. Not only once. I have to enter my password approx. 9 times for this message to disappear. 

Does someone have a similar problem?

I use Chrome 62 on Ubuntu 17.10.

Ideally I would love to get rid of this message completely!

Thank you.

In my case this problem was caused by me setting up automatic login when I did the install.  When I then installed google chrome it asked me for a password for the default keyring and everytime I opened chrome I needed to enter the password. It took me a while but I finally figured out how to fix this issue correctly.

1. Open google chrome and in settings signout of your google account. Close chrome.
2. Disable automatic login for linux so you are required to enter your username and password when logging in.
3. Reboot and make sure you are required to login with your username and password, if not go back and fix the issue. This will not work with auto login on.
4. From the menu, open Passwords and Keys.
5. Delete the default keyring.
6. In the login keyring, delete the password for the default keyring.
7. Reboot, signin, and then open google chrome.
8. Go to setting and signin to chrome.

After doing these steps, give chrome a few minutes to sync and all of your saved passwords, etc. that were stored in the default keyring should be restored into your login keyring and working correctly.

---

### Post by orschiro on 2018-02-26
@lexj thanks for your detailed steps, very appreciated and super useful!

---

### Post by deadraven on 2018-05-13
for those who don't like any of the options.  here is a way to fix it fast

change your short cut command and add this to the very end

--password-store=basic

i.e.
chromium-browser %U --password-store=basic
google-chrome-stable %U --password-store=basic

---

### Post by lnowakowski on 2018-07-19
Is this for sure working for you? In my case after this change I had to log-in to Chrome (Google account) each time after reboot. For now only solution is to hit "Escape" for each password request to new keyring until Chrome launches.

---

### Post by mIk3_08 on 2018-12-02
I'll go with deadflowr. its more safe. And its working fine. I'm using ubuntu 18.04

---

### Post by ejsiqueirajr on 2019-04-03
I did almost what @deadflowr suggested. 
Edited google-chrome.desktop in its source as I am the only one that use this computer. 
Working like a charm. 

Thanks a lot.

Chromium version 73.0.3683.75 (Official Build) Built on Ubuntu, running on Ubuntu 16.04 (32-bit)

---

### Post by vlskrbek on 2019-05-04
The daedflowr solution is not more safe because it store the password in plain text.
The only solution that is save is to use keyring like solution from lexj and not display message or not use any password at all.

The solution from lexj works fine but only when you login to ubuntu with password. If you want to login automaticaly then this does not work.
The solution is do not use any password. You will do it in the first time when you run chrome it ask you for new password. Just put blank. It will tell you that it is not secure but it will work. If you already put any password then open keyring and set the blank password for the chrome "Default keyring". This solution is here:
[https://www.ricksdailytips.com/prevent-chrome-from-asking-for-a-password-with-ubuntu/](https://www.ricksdailytips.com/prevent-chrome-from-asking-for-a-password-with-ubuntu/)

---

### Post by cornelisweyers on 2019-09-01
Thank you for posting this, your solution works perfectly for me!

---


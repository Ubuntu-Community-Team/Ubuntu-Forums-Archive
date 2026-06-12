---
title: "Enter password to unlock default keyring issue"
date: 2012-11-01
forum: General Help
---

### Post by wmdvanzyl on 2012-11-01
I know. This issue has been posted about time and time again. There have been a plethora of scenarios and it always boils down to the following combination:


[LIST=1]
[*]Default keyring and Login password don't match
[*]Some application (eg. wireless network) requires access to the keyring
[/LIST]
The reason i am opening yet another thread is that my default keyring password and my login password, matches. Which means that it doesn't matter what program is trying to access it, it should be unlocked, but it is not. So please don't suggest anything that has to do with point 2, the issue is clearly at point 1.


My specific question, how do i resolve the unlocking the default keyring issue, when my passwords already match?

---

### Post by timgood on 2012-11-01
I seem to remember that I had this problem and solved it by deleting the Login keyring, and then recreating it and setting the new one as default. You will need to call the new keyring 'Login' as well.

Hope this helps.

---

### Post by wmdvanzyl on 2012-11-01
> **timgood said:**
> I seem to remember that I had this problem and solved it by deleting the Login keyring, and then recreating it and setting the new one as default. You will need to call the new keyring 'Login' as well.

Hope this helps.

So you suggest i delete the Default keyring, create a new one and name it Login? It's not that i am reluctant, it's just that it's a lot of effort to re-add all those keys based on a suggestion that "seem to recall". :-P No offense. I jJust want to be a bit more confident in the proposed solution before attempting it. :-) 

Can anyone else support this suggestion?

---

### Post by mcduck on 2012-11-01
Are you using automatic (or password-free) login? Neither of those options will unlock the keyring automatically, even if the password matches the login password...

---

### Post by wmdvanzyl on 2012-11-04
Hi mcduck.

No, i have to enter a password when ubuntu starts up, so no auto-login and not pw free.
Also, that pw matches the keyring pw.

---

### Post by DuckHook on 2012-11-09
This seems to be a pernicious problem in various flavours of Ubuntu. What flavour are you using? I ran into this problem in my Lubuntu 12.04 installations and it turns out that Lubuntu does not install *libpam-gnome-keyring* by default. Therefore, when linking the Lubuntu machine to my existing UbuntuOne account for the first time, the *default* keyring was created, but because the pam module was missing, it was not possible to link the *default* keyring to the *login* keyring.

Try

```
sudo apt-get install libpam-gnome-keyring
```

If the module already exists on your system, no harm done.

Then logout and log back in.

When the pop-up for unlocking the *default* keyring comes up, do not simply type in the password to unlock. Instead, click *details* and select the *automatically unlock this keyring on login* radio button. Then enter your password to unlock the *default* keyring. You will now have linked the *default* keyring to the *login* keyring. Even if the pam module was installed, it is possible that the link was not established. In that case, the last portion of these instructions may still solve the problem.

To test, logout and login again. If the pop-up does not come up, you have solved your problem. If it still comes up, then the problem is elsewhere and I'm stumped.

BTW, Ubuntu should install *libpam-gnome-keyring* by default on both Lubuntu and Xubuntu to solve this problem once and for all. A lot of users are frustrated by the additional step needed to unlock the keyring and it creates a bad taste for Ubuntu. The documentation for solving this problem is also nonexistent or misdirected. The Ubuntu site itself contains nothing. The OneUbuntu site tries to solve a totally different problem. And the AskUbuntu site is full of frustrated users with this issue who are being given the terrible advice of deleting the keyring altogether, thus leaving their passwords unencrypted and completely exposed. This is a problem with potentially serious consequences and should be addressed as quickly as possible.

I will leave a bug report in Launchpad.

---

### Post by ypoepie on 2013-02-12
Hi there!

This solved the problem for me:  

xxx@xxx~$: cd ~/.local/share/keyrings
[email]xxx@xxx~/.local[/email]/share/keyrings$ rm default.keyring
[email]xxx@xxx~/.local[/email]/share/keyrings$ rm Default.keyring
[email]xxx@xxx~/.local[/email]/share/keyrings$ rm default-1.keyring
[email]xxx@xxx~/.local[/email]/share/keyrings$ rm Default_1.keyring

see, if it does the job for you
(Ubuntu 12.10 is running for 5 days now on my laptop!)

cheers,
ypoepie

---

### Post by antoniogarciaiii on 2013-03-22
I signed in just to thank you. This worked fine for me.

---

### Post by jcoles on 2013-04-28
Part of the problem might be that libpam-gnome-keyring is not competently installed. From my new  xubuntu 13.04  system:
> ** (gnome-keyring:3170): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-YTwJ5viazI: Connection refused

This won't show at the GUI level, but it means that anything you do there regarding the keyring will have no effect.
A re-install of the package made no difference.

---


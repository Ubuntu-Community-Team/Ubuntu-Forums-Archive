---
title: "Online Accounts App"
date: 2019-06-12
forum: General Help
---

### Post by mIk3_08 on 2019-06-12
Hello everyone,

Just wanted know if Online Accounts in Ubuntu 18.04 I've tried many time to login using gnome online accounts panel and unity online accounts panel but sad to say I haven't see any log-in or sign-in button for me to use the Ubuntu Single Sign-On Account.
Any response will be much appreciated.

Many Thanks,
Michael

---

### Post by mIk3_08 on 2019-06-12
Hello everyone,
Any help please.. Any response will be much appreciated.


Many Thanks

---

### Post by mIk3_08 on 2019-06-13
Hi.

thus online accounts panel still work until now?

michael

---

### Post by deadflowr on 2019-06-13
This is unity, right?
The missing login button for Ubuntu SSO in Online Accounts is a well known issue.
The current workaround is to logout and if possible log into the Ubuntu session and set it there.
Then logout of that and reset it to log back into unity.
From the wayback machine (of 2018):
[https://askubuntu.com/questions/1025923/ubuntu-18-04-unity-cant-login-to-my-ubuntu-sso-account-from-unity-control-cen]("https://askubuntu.com/questions/1025923/ubuntu-18-04-unity-cant-login-to-my-ubuntu-sso-account-from-unity-control-cen")
As far as I've seen Ubuntu SSO is the only account setup this affects.

---

### Post by mIk3_08 on 2019-06-14
Thanks a lot deadflowr. I will try this one.... 

Many Thanks...
Michael

---

### Post by mIk3_08 on 2019-06-14
I had a problem when logging-in using unity with this login keyring after my successful login using Ubuntu desktop, It work fine using Ubuntu. I just cancel this login keyring pop up window.

When I cancel the window login keyring window in unity. It says;
Error logging into the account 
Failed to store credentials in the keyring

---

### Post by deadflowr on 2019-06-14
Does a reboot work instead?
Also, is this using the gdm (Ubuntu' new login screen), or have you switch to lightdm (The older login screen Ubuntu used)?
I seem to remember there have been issues logging in and out with gdm.
Not seen anything like that with lightdm.

---

### Post by mIk3_08 on 2019-06-14
Yes, Im using the LightDM instead of GDM. I already switch to LightDM since the time I've installed unity in my system.

Here's some screenshot after I logout from the gnome desktop and switching to unity desktop;
run on unity online account;
[ATTACH=CONFIG]283429[/ATTACH]

run on gnome online account;
[ATTACH=CONFIG]283430[/ATTACH]

error screenshot; 
[ATTACH=CONFIG]283431[/ATTACH]

---

### Post by deadflowr on 2019-06-14
The problem seems to be it's not getting (or cannot be) saved to the login keyring.
Are you auto-logging in or something?

---

### Post by mIk3_08 on 2019-06-15
Yes, I need to use this for network resource purposes. Is there any way that we can fix this login keyring?

---

### Post by mIk3_08 on 2019-06-17
Thanks deadflowr for the response. Anyone have any idea for this?

---

### Post by deadflowr on 2019-06-17
I would think you'd have to unlock the keyring (It's in Passwords and Keys > Login)
You'd have to do this before adding the account to online accounts.
And then every time you logged in.

---

### Post by mIk3_08 on 2019-06-18
Thanks deadflowr. I'll be back to you for the feedback.

---

### Post by mIk3_08 on 2019-06-19
Thanks a lot deadflowr. It work.  But every time I shutdown the system and turning on again then login back to the system there is always a pop-up keyring window asking me to unlock, but its okay. I think this is for the security purposes. I unlock it and lock it back again.

Many Thanks

---


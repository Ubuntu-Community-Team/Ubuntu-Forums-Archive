---
title: "Strange keyring message during Skype login"
date: 2017-10-16
forum: General Help
---

### Post by MibunoOokami on 2017-10-16
Hi all,

For the past few weeks Skype is making me enter my username and password every time I want to use it and once I have, it throws up a message saying > The password you use to login to your computer no longer matches that of your login keyring and wants me to enter a matching password.

The problem is, not only has my computer login password never changed, I've tried using my Skype PW and my email PWs but it tells me the password doesn't match!? If I hit cancel Skype will proceed to login, if not it just sits there.

I want to know what this error is and why, when I try login to Skype, I'm being told my computer login doesn't matches the keyring. One should not have anything to do with the other. Perhaps Skype is trying to phish passwords? It seems odd that I'm being asked for a matching password and told mine doesn't match, and then it proceeds to log me into Skype after I click cancel.

I'd appreciate any input on this matter. Thanks

---

### Post by MibunoOokami on 2017-10-17
I've taken a screenshot of the message if that helps.

---

### Post by untrustytahr on 2017-10-17
It is trying to access your login keyring in Seahorse (aka Password & Keys).  People usually get that when they set their user account to "Auto Logon" or if they change their password through some other unorthodox means.

---

### Post by MibunoOokami on 2017-10-17
> **untrustytahr said:**
> It is trying to access your login keyring in Seahorse (aka Password & Keys).  People usually get that when they set their user account to "Auto Logon" or if they change their password through some other unorthodox means.

Thanks for your reply. 

If "auto logon" is the same as no password needed at startup then it's not that as I have it set so that I always need to login to the PC. There have been no password changes for a considerable amount of time.

---

### Post by untrustytahr on 2017-10-18
There are other reasons why the keyring cannot be accessed.  Most revolve around dbus-user-session.  It seems several people are having issues with the new skype.  Perhaps these links will help:
[https://askubuntu.com/questions/962733/how-can-i-open-skype-without-entering-a-keyring-password-each-time](https://askubuntu.com/questions/962733/how-can-i-open-skype-without-entering-a-keyring-password-each-time)
[https://askubuntu.com/questions/936059/seahorse-does-not-provide-passwords-anymore#937269](https://askubuntu.com/questions/936059/seahorse-does-not-provide-passwords-anymore#937269)

---

### Post by MibunoOokami on 2017-10-19
Hmm, those troubleshooting tips didn't work. 

1) When trying to change the keyring login PW it asks for an old one. Since I haven't changed the PW and there's only one it tells me the PW is incorrect. (see screenshot)
2) Upon using the dbus command I got this message ```
~$ dpkg -L dbus-user-session
dpkg-query: package 'dbus-user-session' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```
3) When #2 failed I went to follow the other instructions to delete any files in the keyring directory located in the hidden directory .gnome2, but there's only one directory in there called "accels". (see screenshot)
[ATTACH=CONFIG]277173[/ATTACH][ATTACH=CONFIG]277172[/ATTACH]

---

### Post by heytracy on 2018-01-06
I just had this happen to me, too!

Mint 17.1. I have my pc set to auto-login & I've not touched Skype's PW.

What/who initiated this? Is it a direct change for security from Skype?

I have my doubts when M$ owns/controls Skype (& has really messed it up).

---

### Post by ortermagic on 2018-01-06
Perhaps you should try using your Microsoft log in? just a thought.

---

### Post by Habitual on 2018-01-07
I'd just delete the Skype key and restart Skype.
You should be prompted for it one more time, hopefully the last.
this should be your password for Skype. 
Additionally, you can verify your Skype password at web.skype.com

---


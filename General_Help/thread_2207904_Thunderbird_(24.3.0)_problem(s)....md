---
title: "Thunderbird (24.3.0) problem(s)..."
date: 2014-02-25
forum: General Help
---

### Post by bc.haynes on 2014-02-25
How do I find out when Thunderbird was last updated?....to see if that had anything to do with the "problem." 
Problem is: I installed TB as usual, typed in my password, and put a tic in "Remember password." All worked fine until yesterday. Then, I wrote an email and tried to send it. It gave me an error message and and went to the password box. I entered the correct password (CAPS LOCK was not on.), and it again asked for the password. I very carefully reenterd the password, and it went back to the box to type in the password. I went to the AT&T site and used the password and it worked. I cannot find a place in TB settings to check or change the password. Being paranoid (from Windows) I wondered if someone or something has changed my password. I am the only one on this computer.

And there you have it.

EDIT: This persists, and I can't email anyone. Should I remove TB and re-install? If so, how do I do it?

---

### Post by wamses2 on 2014-02-26
I'm sure there will be better ways, but as nobody has suggested them yet, try the dpkg.log in var/log. I think this contains entries for upgrades, you should see it somewhere near the end of the file, or do a search for Thunderbird with the version number.

---

### Post by bc.haynes on 2014-02-26
Thank you **wamses2**, T-Bird was updated shortly before this happened:
```
2014-02-19 18:10:25 upgrade thunderbird-locale-en 1:24.2.0+build1-0ubuntu0.12.04.1 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:26 status unpacked thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:26 status unpacked thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:26 upgrade thunderbird 1:24.2.0+build1-0ubuntu0.12.04.1 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 upgrade thunderbird-gnome-support 1:24.2.0+build1-0ubuntu0.12.04.1 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 status unpacked thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 status unpacked thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:28 upgrade thunderbird-globalmenu 1:24.2.0+build1-0ubuntu0.12.04.1 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:29 status unpacked thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:29 status unpacked thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:29 upgrade thunderbird-locale-en-us 1:24.2.0+build1-0ubuntu0.12.04.1 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:29 status unpacked thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:29 status unpacked thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 configure thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-19 18:10:32 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status unpacked thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status half-configured thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status installed thunderbird 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 configure thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-19 18:10:32 status unpacked thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status half-configured thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status installed thunderbird-locale-en 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 configure thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-19 18:10:32 status unpacked thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status half-configured thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:32 status installed thunderbird-gnome-support 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 configure thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-19 18:10:33 status unpacked thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 status half-configured thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 status installed thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 configure thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-19 18:10:33 status unpacked thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 status half-configured thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-19 18:10:33 status installed thunderbird-locale-en-us 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 status installed thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 remove thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1 <none>
2014-02-20 13:36:17 status half-configured thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 status half-installed thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
2014-02-20 13:36:17 status config-files thunderbird-globalmenu 1:24.3.0+build2-0ubuntu0.12.04.1
ben@MissionControl:/var/log$ 

```
How do I get my T-Bird back to normal?

---

### Post by xeonix on 2014-02-26
@op:
You can check your "remembered password" in,
Menu bar -> Edit -> Preferences -> Security -> passwrods

As, the issue is concern, I did faced the issue with 24.3.0, but, I am not sure if its TB issue, because, after closing the TB and restarting it after some time, it did accepted password.
Howerver, if you want to re-install the TB, you can simply.

```
sudo apt-get purge thunderbird && sudo apt-get install thunderbird
```

---

### Post by bc.haynes on 2014-02-26
Thank you **xeonix** for your help.

---

### Post by wamses2 on 2014-02-26
Well b.c.haynes, I'm not sure if this will help or not, but....
My wife's machine uses Ubuntu 12.04 and I installed a heap of upgrades yesterday. This morning she couldn't send email. Tbird (yes 24.3.0) was complaining about the connection STARTTTLS not being supported by the email service.  Pretty odd because the value for connection security was set to none (and this had been working fine).  Also the Authentication method was set to 'Password transmitted insecurely (and this too had been working fine).
For reasons I cannot explain, I changed the Authentication method to 'TLS certificate' and Tbird then sent the email.  As you are prob aware all of these settings are configured under the user/server.
Not too much help to you, but it does suggest Tbird is acting a bit cranky.  Good luck.

---

### Post by bc.haynes on 2014-02-26
@ **wamses2** - Purging and reinstalling seems to have gotten T-Bird back and running. I even still had my folders and saved emails. (This happened to me in Windows several months ago.).

@** xeonix - + 1** -Thank you for your help.

---


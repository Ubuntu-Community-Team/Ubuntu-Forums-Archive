---
title: "I changed user name and pw, and cannot log in"
date: 2008-06-26
forum: General Help
---

### Post by rinacutybaby on 2008-06-26
Hello, I have a compaq, it is my dad's old laptop and gave it to me, and he put ubuntu and made me a username and pw, and I changed it, I changed almost everything like background, sounds, fonts etc. I logged out then log in but it doesnt let me log in, showing me that not found or I have to me in a failed session. Pls help.:confused:

---

### Post by ryanhaigh on 2008-06-26
How did you change your username and password?

---

### Post by p_quarles on 2008-06-26
From the initial boot menu (press esc if it doesn't show up automatically), select the "recovery mode" boot option. Once it logs you in to the terminal, run the following:
```
passwd username
```
Replace "username" with the name of user whose password you want to set. It will prompt you for a new password. Type:
```
reboot
```
to get back to the normal boot mode.

---

### Post by rinacutybaby on 2008-06-26
Hi, I changed my user name and paasword by going to administration. I tried rebooting but it gave me error. I tried reinstalling ubuntu but it doesnt let me. Help I am a new user of ubuntu.

---

### Post by timcredible on 2008-06-26
you can't change your username from the 'Users and Groups' menu option.  Try your old username and password.

---

### Post by rinacutybaby on 2008-06-26
Can I just reinstall ubuntu 8.04? and how? cuz I tried and it dont let me.

---

### Post by p_quarles on 2008-06-26
Did you try booting into recovery mode like I said?

And of course you can reinstall. But you don't need to.

---

### Post by p_quarles on 2008-06-26
Did you try booting into recovery mode like I said?

And of course you can reinstall. But you don't need to.

---

### Post by marufaberlin on 2008-06-26
how far does it go when booting?

can you boot without "quiet" and "splash" parameters?

hint: press "c" in grub or find a grub tutorial

---

### Post by rinacutybaby on 2008-06-26
I did boot it and foolowed what you said but it didnt do anything, It sez command not found. pls help me just start from the scratch.

---

### Post by rinacutybaby on 2008-06-26
did tried all I can find from the forum,it didnt help, it is saying to me that My user name is different from the root name.I think it is easier for me to just delete and reinstall the ubuntu? I have never heard about ubuntu and it is killing me.

---

### Post by rinacutybaby on 2008-06-26
I went back to log in area, now it told me to go to fail session and I went there, now it is telling me to see "man sudo_rooT" for details.I am getting frustrated...I just want to start from the scratch. pls help, sorry for confusions and disturbance.

---

### Post by p_quarles on 2008-06-26
What you're saying isn't making much sense. Were you or were you not able to boot into Recovery Mode? Did you run 
```
passwd *username*
```
?

If you want to reinstall, that should be no trouble. The instructions are right on the download page.

---

### Post by rinacutybaby on 2008-06-26
yes I was able to change the password but it is saying that my log in is diff than user root, I changed user name, ex from nora to rina, so when I log in using rina it doesnt recognize it but when I log in using nora it take it but showing that the root is rina.

---

### Post by KeyserSoze93 on 2008-06-26
reboot

select single user mode (you may need to press esc to see the grub menu)

it should do some stuff, then say something like "running local boot scripts [OK]" (if you can't get that far, how far can you get?)

press enter

type this (where usename is your username, without the quotes): "passwd username"

enter a new password

type "finger username"

does it say use doesn't exist? if not does it give some info like your shell and when you last logged on etc.

boot normal and try and log in, if you can, report exactly why it says you can't.

---

### Post by p_quarles on 2008-06-26
> **rinacutybaby said:**
> yes I was able to change the password but it is saying that my log in is diff than user root, I changed user name, ex from nora to rina, so when I log in using rina it doesnt recognize it but when I log in using nora it take it but showing that the root is rina.
Well, you left that part out. It's easy to fix, in any case. Boot back into recovery mode and run this:
```
adduser nora admin
```
And "nora" will now have root privileges by using "sudo."

---

### Post by rinacutybaby on 2008-06-26
OK Ill try that one....brb.

---

### Post by rinacutybaby on 2008-06-26
Ok this is what it gave me....root@Rina toner:~#finger nora   log in:nora  Directory: home/rina  name:Leonora Toner    shell:/bin/bash    Never logged in   No mail   No Plan
then I boot...but I didnt see the option on changing to single user.

I tried to log in again this is what it gave me...

your home directory is listed as:'/home/rina' but it does not appear to exist. Do you want to log with the (root)directory then told me to use failsafe...but it didnt do any good....it gave me 644 permissions.

---

### Post by xebian on 2008-06-26
> **rinacutybaby said:**
> Ok this is what it gave me....root@Rina toner:~#finger nora   log in:nora  Directory: home/rina  name:Leonora Toner    shell:/bin/bash    Never logged in   No mail   No Plan
then I boot...but I didnt see the option on changing to single user.

I tried to log in again this is what it gave me...

your home directory is listed as:'/home/rina' but it does not appear to exist. Do you want to log with the (root)directory then told me to use failsafe...but it didnt do any good....it gave me 644 permissions.

Ok.  this is what we should do.  Boot the pc until you see the prompt as in the first line above and repeated below

```
[COLOR="Red"]root@Rina toner:~#[/COLOR]

```

then type this at the prompt and enter.  It will ask for password (new ) and then ask again to confirm

```
adduser rina admin
```

Then reboot normally, and then you can use rina as user

---

### Post by rinacutybaby on 2008-06-27
I did that also, and it gave me user not found. but Ill try again...

---

### Post by rinacutybaby on 2008-06-27
ok this is what it gave me the user 'rina' does not exist.

---

### Post by rinacutybaby on 2008-06-27
when I di the adduser nora admin, it gave me the user 'nora' is already a member of 'admin'

---


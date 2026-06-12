---
title: "Passwrd command seems to be uninstalled"
date: 2018-06-20
forum: General Help
---

### Post by alowe2 on 2018-06-20
My father died and I inherited his laptop with Ubuntu on it.
Things were fine until I needed to access a website which says it won't load without a newer version of Firefox.

I don't know what the root password is whenever it tries to update anything. So, I looked into how to change the root password and apparently the way to do it is via the passwrd command.

Problem is the passwrd command isn't on the system. Using whereis returns nothing.

I tried going into the terminal and typing sudo passwrd, but it needs the root password to install that command.

Seem to be snookered. Anything I can do about it beyond formatting the hard drive? My dad left a lot of family pictures and such on the laptop. There's a lot of sentimental stuff I'm not sure I've found, so I'm reticent to format the main drive as any mistake and stuff might get lost.

---

### Post by PaulW2U on 2018-06-20
The following are links to a couple of guides that show you how to reset a lost administrator password:

[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")
[LostPassword]("https://help.ubuntu.com/community/LostPassword")

By the way, the command that you were trying to use isn't **passwrd** but **passwd**. I think you'll find that it is installed. :)

Welcome to the Ubuntu Forums.

---

### Post by Holger_Gehrke on 2018-06-20
First: the command to change passwords is **passwd**, not passw**r**d.

Second: modern Ubuntu does not use a root passwort, you're not supposed to log in as root; the password you're being asked to supply is the password of the account you're using and presumably the same password you typed in when logging into the machine (unless -- of course -- the machine does an automatic login without password ...)

Third: there are [ways to get around this situation]("https://help.ubuntu.com/community/LostPassword") even if you don't have the password.

Holger

---

### Post by oldos2er on 2018-06-20
If you don't already have a backup image of that drive I would make one ASAP.

---

### Post by alowe2 on 2018-06-21
Ok, I figured out how to boot up into the command console which was a bit more complicated because it's a dual boot laptop.
Typed in passwd (without the r, this time).
Entered the new password twice.
Got an error: "authentication token manipulation error"

Did a google search on that error and only got one result. That advised me to connect to the laptop remotely and change the password via SSH which to me sounds wayyy too complicated.
I'll try the links people have posted but if they rely on the passwd command and/or don't address that error I'm stuck again.

PS for those curious as to what website doesn't allow Firefox version 51, it's ebay's advanced listing tool.
Until I can update Firefox all my ebay listings are forced to accept nearest offers which I don't want.

---

### Post by alowe2 on 2018-06-21
> **PaulW2U said:**
> The following are links to a couple of guides that show you how to reset a lost administrator password:

[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")
Tried this guide. Pretty much mirrors what I figured out for myself except using the mount command.
But when I entered the mount command exactly as shown got an error back.

mount: special device remount does not exist

I did ls /home and got the user name. Had entered it wrong before with the first letter capitalised (as shown on the desktop).

But still getting the error:

authentication token manipulation error

I'll try the other guides...

**Edit:** tried the Lost Password link as well. That doesn't work because Shift and Esc do nothing on my laptop during bootup. Maybe because it's a dual boot. Anyway, the instructions thereafter are the same as the first guide so it's no more likely to succeed. Just a different method to get into the shell but thereafter the instructions are the same. Won't work. So onwards and upwards to the other guides. See if one of them will work...

**Edit:** the link posted by Holger_Gehrke is the same as the Lost Password link posted by PaulW2U. So that rules that one out.

---

### Post by PaulW2U on 2018-06-21
alowe2, do you have **any** username and password to use for this laptop?
Are you logging in as root or was that how you were referring to the need for an administrator password?
I suspect you're not logging in as root as you're prefixing commands with sudo.
If you're logging in with a username and password then the administrator password is your user password assuming that your user is set up to have administrator privileges.
Has more than one user been set up on the laptop? "ls /home" would have revealed any other users.
Perhaps you could clarify the above points.

---

### Post by alowe2 on 2018-06-21
Sorry for triple post but wanted this to be read separately.

Success warning!

Googled the error: "mount: special device remount does not exist"
and discovered this is caused by entering a space between the "rw," and "remount" parts. Durp.

This time when I tried the passwd command, it worked. Yay!

So, the "authentication token manipulation error" was fixed (at least for me) by remounting the system drive (hoping I got that concept understood).

But you guys pointed me in the right direction and with a little noobish flare from me, we triumphed.

---


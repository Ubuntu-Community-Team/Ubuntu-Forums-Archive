---
title: "Chromium ask about unlocking keyring at start"
date: 2013-05-19
forum: General Help
---

### Post by woxuxow on 2013-05-19
Excuse me i didn't find any proper category to to ask my question and decided to ask it here (Desktop Environments category)

Anytime i run Chromium the window that ask password for unlocking keyring appears
Dos chromium store its passwords(websites password) in "keyring"?
Or something is wrong?

Should i trust in chromium i enter the password or not?

---

### Post by wildmanne39 on 2013-05-19
*Thread moved to **General Help**.*

---

### Post by woxuxow on 2013-05-19
> **Wild Man said:**
> *Thread moved to **General Help**.*

Thanks
It's better to have a Software category or internet software category or something like that

Dos anybody know what's my problem? or have the same problem?

---

### Post by cwsnyder on 2013-05-19
It is Ubuntu which stores the passwords used by your browser (for example to log in to your Google account if you do opt to use the Chrome/Chromium password storage) in a keyring.  So if you have a Google account and store your bookmarks on the cloud, Chromium tries to log in to your Google account when it starts and tries to load your account and password from the Ubuntu keyring.

---

### Post by Charlotte18 on 2013-05-20
> **woxuxow said:**
> Dos chromium store its passwords(websites password) in "keyring"?
Or something is wrong?Ubuntu is asking for the keyring password. You can make this stop by opening seahorse and changing the Chromium keyring password to blank.

---

### Post by woxuxow on 2013-05-20
Thanks
So chromium is not able to access google account directly (without ubuntu permission)

---

### Post by mastablasta on 2013-05-20
sort of. your saved passwords (if you checked for example save my password in browser) are encrypted and stored in this keyring. so if someone breaks into the browser they still need to break into keyring to get to the saved passwords.  that's how i understand it. on th eother hand knwoing the keyring password will unlock all passwords. you will only need to type it once to unlock all saved passwords.

and as mentioned you can disable the feature.

---

### Post by woxuxow on 2013-05-20
> **mastablasta said:**
> sort of. your saved passwords (if you checked for example save my password in browser) are encrypted and stored in this keyring. so if someone breaks into the browser they still need to break into keyring to get to the saved passwords.  that's how i understand it. on th eother hand knwoing the keyring password will unlock all passwords. you will only need to type it once to unlock all saved passwords.

and as mentioned you can disable the feature.

How to disable it?
I just checked "Encrypt your password with your google credentials" 
didn't find any keyring options or where to store passwords

---

### Post by Charlotte18 on 2013-05-22
> **woxuxow said:**
> How to disable it?

Open the terminal and type seahorse.  The "Passwords and Keys" window will open.  Unlock the "default" under passwords, right click on default, and then choose change password.  When you change the password, leave the new password blank

---

### Post by woxuxow on 2013-05-23
> **Charlotte18 said:**
> Open the terminal and type seahorse.  The "Passwords and Keys" window will open.  Unlock the "default" under passwords, right click on default, and then choose change password.  When you change the password, leave the new password blank

I can`t find defualt
where is it?
[http://i39.tinypic.com/ftphs.png](http://i39.tinypic.com/ftphs.png)

[IMG]http://i39.tinypic.com/ftphs.png[/IMG]

---

### Post by Maverick Meerkat on 2013-05-23
This is good to know about "Seahorse", I would have never figured that out.
I had run into this keyring message soon after installing 13.04
I thought I had clicked on something strange during the install, so I went and re-installed 13.04
For several days everything was fine until I synced my Ubuntu-1 cloud, after that, the keyring message showed up again.
It seemed as though it was after my system would come out of hibernation.
I am still playing with this. I logged out of Ubuntu-1 and the keyring message went away.
It may be because I didn't have to enter my password upon awakening from hibernation?
Perhaps I will reconnect with Ubuntu-1 and see if the message returns.

I have been using Ubuntu for 2 years and always used Chromium for my browser until several weeks ago when I decided to give Google Chrome a shot.
Of my 3 systems, 2 are running Chrome on 12.04 without any keyring message.
It's the third system, running 13.04 where it showed up.

Thanks for the Seahorse info.
I have it if I will need it :-)

Rick

---

### Post by Maverick Meerkat on 2013-05-23
Hey, Woxuxow,
I tried the Seahorse thing to see what I would get, and I only had 2 items listed, unlike your list.
Mine is a new install though, but I have Ubuntu-1 and Facebook listed.
Clicking on Ubuntu-1, gives me the option to change the password and I guess that is the part that I could save as blank.
The password shown is much larger than the one I would have typed in, so maybe it is system generated?

I left it alone for now, but I don't know which one you need to look for... is there a listing for Chromium?

Rick

---

### Post by OrangeCrate on 2013-05-23
> **woxuxow said:**
> Excuse me i didn't find any proper category to to ask my question and decided to ask it here (Desktop Environments category)

Anytime i run Chromium the window that ask password for unlocking keyring appears
Dos chromium store its passwords(websites password) in "keyring"?
Or something is wrong?

Should i trust in chromium i enter the password or not?

Edit:

Sorry, I misread the direction of this thread prior to posting. Rather than delete my post, I'll just leave it.

-----

It has been noted, that the keyring does not unlock in Xubuntu 12.04, and continues to ask for a password, which is a bug. I doubt this might be your direct answer, but, it wouldn't hurt to take a look for ideas...

See here for discussion and solution:

[https://lists.ubuntu.com/archives/xubuntu-users/2012-July/004268.html](https://lists.ubuntu.com/archives/xubuntu-users/2012-July/004268.html)

---

### Post by woxuxow on 2013-05-23
Thanks anybody posted here
I entered my user password in password box of "account.google.com"'s field in "Passwords and keys" and keyring unlock dialog never shown again (yet)

---

### Post by Maverick Meerkat on 2013-05-24
Update: When rebooting my computer, I was asked for my keyring password.
I noticed that it shows up when my Ubuntu-1 turns on, I had it off but I guess reboot turns it on.
I may go and run that seahorse thing.

Usually, I keep the computer on.
Also, I made it where I don't need a password on start-up and this, too, could be a part of all this keyring stuff.

Rick

---

### Post by Charlotte18 on 2013-05-25
> **Maverick Meerkat said:**
> 
Clicking on Ubuntu-1, gives me the option to change the password and I guess that is the part that I could save as blank.
I switched to lubuntu a few weeks ago because unity was too slow on my old hardware, so my options in seahorse apparently look slightly different from yours. However, to make Ubuntu stop asking for the keyring password every time you login, you should pay attention to the* left* column in seahorse. Under Passwords, mine says "default" in lubuntu. In woxuxow's post, it looks as if it says "Login" in gnome.  If you want to stop the keyring from asking for a password, you should change *this *password to blank, not the individual passwords in the right column.

---

### Post by woxuxow on 2013-05-25
> **Charlotte18 said:**
> I switched to lubuntu a few weeks ago because unity was too slow on my old hardware, so my options in seahorse apparently look slightly different from yours. However, to make Ubuntu stop asking for the keyring password every time you login, you should pay attention to the* left* column in seahorse. Under Passwords, mine says "default" in lubuntu. In woxuxow's post, it looks as if it says "Login" in gnome.  If you want to stop the keyring from asking for a password, you should change *this *password to blank, not the individual passwords in the right column.

Yes
in gnome to stopping keyring asking password, just right click on "Login" on left panel and choose "change password" and leave the "change password" dialog empty

---

### Post by Maverick Meerkat on 2013-05-26
Thanks, guys, but my dialog box doesn't have that left hand column.
 I'm running Ubuntu 13.04 on this machine.
It's not really a problem, I was just wondering what was different between this installation, and my two other systems that run 12.04 that never ask for the keyring.
Perhaps it's 13.04?
Or maybe because I set this up not requiring a password at boot up.

---

### Post by Charlotte18 on 2013-05-27
> **Maverick Meerkat said:**
> Thanks, guys, but my dialog box doesn't have that left hand column.
 I'm running Ubuntu 13.04 on this machine.I cannot see what you're seeing, but at the top of your window, it may say, "Passwords: login," which is an expandable menu and under which the individual keys appear. If so, the "Passwords: login" is where you would change the keyring password to blank.
> It's not really a problem, I was just wondering what was different between this installation, and my two other systems that run 12.04 that never ask for the keyring.
Perhaps it's 13.04?
Or maybe because I set this up not requiring a password at boot up.
I've read elsewhere that this happens when you set a keyring password that is different from your login password.

---

### Post by woxuxow on 2013-05-27
> **Maverick Meerkat said:**
> Thanks, guys, but my dialog box doesn't have that left hand column.
 I'm running Ubuntu 13.04 on this machine.
It's not really a problem, I was just wondering what was different between this installation, and my two other systems that run 12.04 that never ask for the keyring.
Perhaps it's 13.04?
Or maybe because I set this up not requiring a password at boot up.

Run "Passwords and Keys" or "type" seahorse in terminal
Then click "By Keyring" in "view" menu to show right panel

---


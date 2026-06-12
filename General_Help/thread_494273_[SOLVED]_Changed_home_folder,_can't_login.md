---
title: "[SOLVED] Changed home folder, can't login"
date: 2007-07-06
forum: General Help
---

### Post by eelensar on 2007-07-06
I did something, which I now realize was really stupid. I went into Users and Groups and changed my profile settings (so far, so good). I changed my username and password, which I can still use. But I also changed my home folder, so now, even though Ubuntu recognizes my username and password, I can't log in. It gave me an option to load as root or load the root folder (can't remember now) and that game me an error and brought me back to the login screen. Any way to change the home folder back to what it was?

I tried booting in recovery mode and looked at some of the manual pages, but I'm very new at this, so I don't know the command line enough.

---

### Post by Old *ix Geek on 2007-07-06
Let me start off by admitting that when I first read your post...I didn't believe it!  That's because in 20+ years of using *nix I've never seen that happen.  However...I thought I'd try reproducing what you did just to see what would happen, and guess what?  I got exactly the same result!  :shock:

Just to clarify, these are the steps I took:

. created a new user, with the default home directory
. logged in as that user
. went to 'users and groups' and changed this user's username and password
. went to the 'advanced' tab and changed this user's home directory
. logged out
. **attempted** to log back in

This is where it starts failing.  Although I definitely was entering the correct [new] password, the screen would go blank for a second and then just return to the same login screen.  Yet if I deliberately entered an incorrect password, it'd tell me "login failed."  So it was definitely recognizing the correct username/password combo, but NOT continuing on as it should after logging in.

Now, I can tell you how to fix it, but that depends on your having already created another user that you can log in as, or your ability to log in as root from the login screen.  The latter can be done--I've done it myself--but neither Ubuntu nor most users recommend doing it.  At any rate, to fix the problem here's what I did:

. logged in as a different user
. went to 'users and groups' and changed the above user's username back to what it was originally
. tried logging in again, using the original username, but it still failed
. logged in again as a different user
. went back to 'users and groups'  and changed their home directory back to what it was originally
. tried logging in as the new user...SUCCESS!

So the moral of the story is that you should be able to fix this and access your original home directory again.  HOW you're going to go about that is the issue at this point.  Since this is *nix everything can be done from a command line, so even if you have to log in as root with only command line access, you'll be able to fix it.

Post again with info about whether or not you have other users already set up, whether or not you have a root password, etc., and we'll take it from there.

---

### Post by HermanAB on 2007-07-06
Hmm, press Ctrl-Alt-F2 to get a text console.  Log in with your user name and password.  It should work, since GDM and Gnome won't run. 

By convention, your home directory is named the same as your username.  It doesn't have to be, but that is the way it normally is, so let's do it that way.

See what your home directory is presently named:
$ ls /home

Now change your home directory to what it should be:
$ mv /home/presentname /home/yourusername

Finally, make sure that your home directory is configured right in file /etc/passwd:
$ sudo usermod -d /home/yourusername yourusername

That should fix it.

Cheers,

Herman

---

### Post by eelensar on 2007-07-07
Thank you for the help.

For the first reply, I was the only user, but I looked in the support wiki and added a user, so I should be able to change to change the home folder.
To the second reply, thank you, I'll have to try that. (I'll be printing it)

Unfortunately, I now have another problem, which is sorta already in another post I posted. I posted that when I booted normally, the computer gets to the progress bar, gets about halfway and then it makes I weird sound and shut offs. Windows, however, still works. I'm thinking it could be the graphic drivers, since apart from codecs and fonts, that's all I changed using EasyUbuntu (and a few other new apps).

---

### Post by eelensar on 2007-07-07
Update:
As normal mode isn't working, I went into original kernel mode, which did. I changed my home folder back like you said HermanAB, thank you. Now, however, all four modes do not boot (including recovery mode and original kernel).

---

### Post by Old *ix Geek on 2007-07-07
Do you have a live CD?  I've never tried this myself, but I've seen other people comment about booting from a live CD and then fixing whatever's screwed up.

---

### Post by eelensar on 2007-07-07
No, I don't. I had to use Wubi since the laptop doesn't have a CD writer.

Anyway, I reinstalled, had the same problem with laptop shutting off. I unplugged everything except for power on the laptop and it booted fine. I added things back one by one (or one by two by two), and it still booted fine. I booted with everything, and it still worked. So I guess, that issue is resolved as well now.

Thank you for the help with the home folder, even if I reinstalled. At least I know how now if I'm stupid enough to do that again. Now that I think about it, the home folder is sorta like the profiles on WinXP - you can change your username and password, but the folder keeps the same name.

---

### Post by Old *ix Geek on 2007-07-08
It's good to hear that the problem is resolved, even though you had to reinstall to fix it.  I strongly suggest that you create more than one user NOW, just in case something like this happens again.  At least that way you'll still be able to log in and fix it!  Also, if you're not in the habit of backing things up...get into it ASAP. :)

---

### Post by Wim Sturkenboom on 2007-07-08
Situations like this is why I have enabled the root account. As root's home folder is not in /home, one should have better chances of recovering from problems.

---

### Post by eelensar on 2007-07-08
I have made a second account named Recovery just in case this time. I don't have anything to backup on right now, but when my dad finally gets around to buying the new computer we were supposed to get in February, I will start backing up stuff.

---

### Post by Old *ix Geek on 2007-07-08
You need to make sure your "Recovery" user has sufficient privileges to administer the system, because if it doesn't, and something screwy happens again, you may not be able to fix it!

---

### Post by eelensar on 2007-07-08
I made it an Administrator when I created it, and I put it in the admin group afterwards. Is that enough?

---


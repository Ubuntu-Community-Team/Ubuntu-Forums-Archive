---
title: "Password Fails Multiple Times At Console Login Then Works"
date: 2007-02-26
forum: General Help
---

### Post by SuSUntu on 2007-02-26
When I switch to a console from my desktop using CTRL+ALT+F1, login is a hit and miss prospect. Typing my user name goes fine, but when prompted to enter my password, it may take 5 - 10 tries (more or less) for my password to be acknowledged as correct. 

I cannot figure out what is happening, but:

- it is not a mistyped password (maybe once or twice in 100 desktop or sudo logins do I incorrectly type my password, so why should I suddenly forget my password or how to type once at the console :) ).

- my keyboard seems to be functioning correctly at the console (I know key sensitivity can change vs the desktop environment, but typing both alpha and numeric characters in my user name presents no issues and seems normal).

I've typed fast and slowwww, and it doesn't seem to matter. When it "decides", the console finally obliges and accepts my credentials.  

By the way, logins to gnome sessions, failsafe terminal, and any sudo or gksudo operations work perfectly with the same password.

Any thoughts on this issue would be appreciated.

Thanks.

-----
Note:
This problem occurs on an Edgy installation (fresh install, not an upgrade).

---

### Post by cronholio on 2007-02-27
That's weird. Do you just get the "Sorry, try again" message or any additional errors along with it?

---

### Post by SuSUntu on 2007-02-27
> **cronholio said:**
> That's weird. Do you just get the "Sorry, try again" message or any additional errors along with it?

The messages are different depending on how many tries have been made. The standard, "Sorry" message appears, then after a time, either a time-exceeded or number-of-tries-exceeded message appears (I believe), neither of which make any difference in proceeding, because after a very brief pause, the prompt to enter user-name pops back up. As I said, eventually the password is accepted, though it is worrisome that it won't be. 

And, yes indeed it is weird. I figured I wouldn't get any replies to this one because the behavior seems unlikely or impossible, as if I'm simply a goof who can't properly input his password. :)

Thanks for the reply.

---

### Post by cronholio on 2007-02-28
What happens when you open a terminal and enter ```
su <yourusername>
``` Can you log in right away?

---

### Post by SuSUntu on 2007-02-28
> **cronholio said:**
> What happens when you open a terminal and enter ```
su <yourusername>
``` Can you log in right away?

That won't work as the console starts with a requirement to log in (not a prompt to enter a command). Here's what I'm greeted with after issuing CTRL+ALT+F1 from within the desktop environment:

Starting up ...
Ubuntu 6.10 ComputerName tty1
ComputerName login:

By the way, I obtained the exact messages I get after password failure depending on how many failures or how much time has transpired during the login process:
- login incorrect 
- login timed out after 60 seconds
- maximum number of tries exceeded (5)

Another oddity is the message returned by the system once I actually get logged in. The message states the number of failed attempts since last login, but the number is incorrect. For example, I successfully logged in initially after 12 or 13 tries, and then I typed 'exit' to get back to the login prompt. In attempting to login a second time, I counted 16 failures (I received three maximum-number-of-tries-exceeded-(5) messages during the login process), yet after I was finally successful, the message stated I only had six failures since last login. 

It's just screwy all the way around. :)

Thanks for your help.

---

### Post by cronholio on 2007-02-28
> That won't work as the console starts with a requirement to log in (not a prompt to enter a command).

I mean the Gnome terminal (Applications->Accessories->Terminal).

---

### Post by SuSUntu on 2007-02-28
> **cronholio said:**
> I mean the Gnome terminal (Applications->Accessories->Terminal).

Oh. Sorry. As I said in my first post, all was working well within the desktop environment.

But ... I fixed it anyway.

Suspecting a problem with xauth, I decided to copy root's .Xauthority file to my home directory, and voilà, fixed.

NOW, since this was something I decided to try based on my limited knowledge of xauth and the .Xauthority file (I was not directed to do this nor was I able to find anyone posting anywhere else with similar symptoms), I'm wondering if what I did is a satisfactory fix.

For example, instead of copying the root .Xauthority file, should I have generated a new .Xauthority using xauth, or would the latter result in the exact same thing as copying the file over from root.

Anyway, thanks for hanging in there with me Cronholio. It's been lonely in this thread. :)

Edit:

The fix lasted through one reboot. A second boot scr*wed me up again and now the same symptoms are back. I think I'm on the right track though, because I was able to successfully login and out multiple times at the console before doing another reboot and getting failure. Do we have any .Xauthority gurus in the house?

---

### Post by SuSUntu on 2007-03-01
**** RESOLVED ** KeyTouch2 (version in the repositories) Was The Culprit**

What I did to determine this beyond what has already been discussed:

**What did not lead to a solution**
- Searching the Internet
- Deleting .Xauthority and .ICEAuthourity files and recreating them
- Adding new users to test if the issue was specific to my main user account (it wasn't)
- Deleting my main user's home directory and deleting the account (user and group), then recreating the account

**What did lead to a solution**
- Backing up home directory contents, /etc, other customized files
- Re-installing Ubuntu 6.10 from scratch, including overwriting home partition
- Systematically rebuilding system using my normal routine (install, update, add additional apps, etc.)

All along the way, I tested for problems with logging in to the TTY console (CTRL-ALT-F1). I follow a written set of notes each time I install to make things go faster and to ensure I don't miss any of my customizations, so I was fairly certain I could identify the cause. KeyTouch2 was installed very late in the process, and I tested for TTY login issues immediately after installing, launching, and setting the keyboard type for KeyTouch2, so when the problem appeared again, I had no doubt what had caused the problem.

**Interesting Points**  
- during testing, the only resolution was uninstalling KeyTouch2 completely; simply killing the process did not fix the TTY login issues.
- since I had created a .keytouch2 folder (with profile settings) before first discovering that KeyTouch2 was causing the issue, I thought perhaps the problem was something specific to the keyboard type, profile, or other user settings, so I uninstalled / reinstalled KeyTouch2, but this time I did not actually run KeyTouch2 nor did I create any user settings (System Monitor also showed no processes related to KeyTouch2 running). After all this , I checked TTY console login and it failed as before. 

The last point is the most perplexing because I don't understand what KeyTouch2 changes simply by installing it (without running it) that munges my console logins. I am glad, however, that the offending changes are 100% reversible by uninstalling the application.

The above results are repeatable. 

Bottom-line ... uninstalling KeyTouch2 did the trick, and now I can move on with my life. :)

---------
P.S

Anyone know of another app (or process) to **easily** get all (most of) the special function keys to work on a keyboard (my specific keyboard is Microsoft's Wireless Elite)? KeyTouch2 worked great at handling the keyboard key-mappings, and I would recommend it if not for the problem I outlined here.

---

### Post by sudoyang on 2008-01-31
Did we ever find a resolution to this?  Today, I'm experiencing something similar today.  Yesterday, the system's working fine but today I can't login whether at the console or via ssh.  I don't have automatic updates enabled.

For me, I can't login at all, not even after a couple of tries.  As soon as I enter the username and password, it immediately comes back with the message:

login timed out after 60 seconds.  

but it didn't take 60 seconds.  It prints this message immediately after supplying a username and password.

---


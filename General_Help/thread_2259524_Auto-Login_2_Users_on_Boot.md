---
title: "Auto-Login 2 Users on Boot"
date: 2015-01-05
forum: General Help
---

### Post by alex309 on 2015-01-05
Hello!

I am new to the forum, but have been scouring the web for an answer to my question.

I have 2 main user accounts on my computer that I would like to start automatically on boot. I have a personal "admin" account that launches all my web applications, VNC server, transmission, etc. on start that i would like to start at boot in the background. I also have a "public" user account that runs web browser and video player that has limited access to files on the PC. I would like the public account to be the first desktop that is usable, with the personal account logged in and running with a locked screen so that all my applications are able to launch. Obviously I am able to autologin to one account or the other, but is it possible to have both users logged in at boot?

Thanks in advance!

---

### Post by TheFu on 2015-01-05
Only 1 account can own the GUI. Having two accounts really isn't needed, IMHO for a single user. If there are 2 people, that would be different.

To start non-GUI programs automatically at boot, you can start them in /etc/rc.local.  Use something like **su userid  -c command**.  No environment will be set, so the command should probably be a script where you setup any environment needed. Do not expect ANYTHING to be set. If you want it, you need it.

---

### Post by alex309 on 2015-01-05
I appreciate the response but I don't think you understand what I am trying to do.

There is more than one user on the particular computer that I am using. User 1, which is my personal admin user account that runs gui applications such as transmission-gtk, and User 2 which is shared between multiple people that is designated for general use (web browsing, videos, etc) and has restricted permissions to much of the filesystem. What I am trying to do is set it up so that User 1 automatically logs in at boot and starts my gui applications (ie. transmission-gtk) and then starts a script that automatically logs in and switches to User 2 (which has no password), effectively leaving User 1 logged in with the startup applications still running. Is this possible to do with a script?

Thank you.

---

### Post by TheFu on 2015-01-05
You are correct.

Not on the same "head" to my knowledge. You can have 2 "heads" and do this.  A head is a keyboard, monitor, mouse grouping.
This is a core UNIX and X/Windows thing.  Sounds like you want "switch users" from Windows and you want it automatic. The security issues with that are huge, but that may not matter to you.

Only one userid can control the X-server at a time.  All X-programs are tied to an X-server. If the X-server is stopped, all X-programs tied to it die.  See the issue?  X-servers run on the "head" you sit behind, not on the remote computer. It is client/server, just backwards.

So - now that I've said this, hopefully someone will come along and prove me wrong or have some other workable option.

---

### Post by alex309 on 2015-01-05
I guess to put it in the simplest way possible, I am looking for a script that will automatically SWITCH USERS to a different user that has no password.

I am not worried about security whatsoever. I am just looking to auto-login to the main user on boot (user 1) and then have it run the script on startup to switch users (not logout) to the secondary user (user 2). This way user 1 is still logged in with a locked screen, but the active X session is on user 2.

---

### Post by TheFu on 2015-01-05
> **alex309 said:**
> I guess to put it in the simplest way possible, I am looking for a script that will automatically SWITCH USERS to a different user that has no password.

I am not worried about security whatsoever. I am just looking to auto-login to the main user on boot (user 1) and then have it run the script on startup to switch users (not logout) to the secondary user (user 2). This way user 1 is still logged in with a locked screen, but the active X session is on user 2.

Let's step back and rethink this a little.

Switching users is easy, provided there isn't any GUI program involved.  This is how init runs all those daemons and how login lets us login.
**sudo -u {userid} command**
or 
**su userid - c command**  - this will require a password
You can setup the sudoers file to specify specific commands and options for those commands to allow without prompting for a password. The problem with this is that the original userid's environment gets passed so any files saved don't usually end up where you wanted OR you can block passing any environment, which will likely break most GUI programs.  Also, when using non-root accounts, this usually leads to error 13 - permission denied as the GUI programs try to write stuff to unknown places - settings mainly. Sudo and sudoers have lots of options and capabilities - it can probably be forced into doing what you want. Every time I review the manpages for those things, I learn something new.

Generally, it is a bad, bad, bad idea to use sudo to run GUI programs. I don't remember all the reasons why that is, but having been burned over the years, that is my rule to stay out of trouble and prevent having userid settings corrupted. If you want to experiment with this, be certain you have backups for any settings, programs, data you care about.

You know, there are non-GUI bt programs. Why not just use those? You can run a status checking tool to see where they are.

---

### Post by ian-weisser on 2015-01-06
> **alex309 said:**
> I have a personal "admin" account that launches all my web applications, VNC server, transmission, etc. on start that i would like to start at boot in the background.

TheFu is right - only one user can own the GUI at a time.

If your admin applications need to run while somebody else is logged in, they should be headless, should run as the proper system user (not you), and should run with the proper permissions to protect your system.

Example: Transmission-daemon is headless, can be started at boot (not login) by a simple Upstart job that listens for the network to come up, and runs as a system user (not you) with limited permission to access any files outside the torrent directories it owns. Your GTK client (or web client, or ssh client) can connect to it anytime you're logged in...or from another machine, but the daemon happily chugs along in the background regardless of who is logged in.

---

### Post by CaptainMark on 2015-01-07
I agree with the people who say that the security flaws here are massive, especially if as you say this is to be publicly available computer, and the general impracticality of what you're trying to achieve is odd to say the least, but warning aside you could try the following, which I have tested and it seems to do what I believe you want. Set your own user account to auto-login, this can be done via the user menu I think still (not using vanilla Ubuntu here any more) then in start-up applications or a bash script (if your comfortable with them) set the command ```
dm-tool switch-to-guest
``` to run as soon as you login.

---


---
title: "New to *nix again"
date: 2008-01-18
forum: General Help
---

### Post by Waukeen on 2008-01-18
Back into Linux after about 10 years away and I decided to install Ubuntu (7.10 Gutsy Gibson) on a Dell Inspiron E1505 to check it out and have been very pleased with it but have a minor question.

Im trying to use the laptop as a Teamspeak server which works fine.  Problem is this I cant get it to start on startup.   I have tried adding it to a session startup list (if im understanding this right) and rebooted to test it and that does not work.  I saw somewhere that editing certain files (have the information on laptop but at work right now and cant remember the names) would work as well but I run into the problem of apparently not having permission to edit those files even on a SU account.  Is there any way I can do this easily since right this minute I dont have the time to play around with Ubuntu the way I would like (plan on doing that Monday and Tuesday) But is there someway I can get the Teamspeak server to run on startup without tearing my hair out?  Thanks for any help guys.

---

### Post by atoponce on 2008-01-18
> **Waukeen said:**
> Im trying to use the laptop as a Teamspeak server which works fine.  Problem is this I cant get it to start on startup.   I have tried adding it to a session startup list (if im understanding this right) and rebooted to test it and that does not work.  I saw somewhere that editing certain files (have the information on laptop but at work right now and cant remember the names) would work as well but I run into the problem of apparently not having permission to edit those files even on a SU account.  Is there any way I can do this easily since right this minute I dont have the time to play around with Ubuntu the way I would like (plan on doing that Monday and Tuesday) But is there someway I can get the Teamspeak server to run on startup without tearing my hair out?  Thanks for any help guys.

What is the binary name of the Teamspeak server?  If you know this, you can check your /etc/rc?.d/ scripts to verify that it's an 'S' script, and not a 'K' script.  Check the man page on update-rc.d.

Also, as far as su is concerned, you can most certainly run a subshell as any user, except for the root account, which is disabled by default.  You have full administration access through the use of the sudo command.

---


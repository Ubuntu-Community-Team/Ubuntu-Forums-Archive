---
title: "TTY skips line to enter password"
date: 2019-02-27
forum: General Help
---

### Post by affenmaster02 on 2019-02-27
Hello there,

recently i ran into an issue with my ttys:

When i switch to any tty i cannot login with any user who has a password - users without passwords (i've created a test user) can login without issues, probably because the password line is not needed.

To describe the issue: i enter my username as prompted and press enter once - then it shows the line to enter my password but instantly skips it (i have time to input smth for like 0.01 sec) into a blank line until after a few seconds the "login incorrect" line appears. After it, the tty just puts me back to the normal "Login:" line - but skips this one now as well (dunno why :confused:) until the 5 attempts have been used and the tty resets itself. 

The Timeout for the Password enter time (in /etc/login.defs) is the standard 60 sec. 

Any login attempt at tty7 (desktop) does work without issues, even logins at the terminal emulator do work for any users as well as sudo.

Auth.log relevant part:
Feb 27 15:57:50 Ebi-Gaming login[3687]: pam_unix(login:auth): conversation failed
Feb 27 15:57:50 Ebi-Gaming login[3687]: pam_unix(login:auth): auth could not identify password for [ebiko]
Feb 27 15:57:54 Ebi-Gaming login[3687]: FAILED LOGIN (1) on '/dev/tty1' FOR 'ebiko', Authentication failure
Feb 27 15:57:54 Ebi-Gaming login[3687]: pam_securetty(login:auth): cannot determine username
Feb 27 15:57:57 Ebi-Gaming login[3687]: FAILED LOGIN (2) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb 27 15:57:57 Ebi-Gaming login[3687]: pam_securetty(login:auth): cannot determine username
Feb 27 15:58:00 Ebi-Gaming login[3687]: FAILED LOGIN (3) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb 27 15:58:01 Ebi-Gaming login[3687]: pam_securetty(login:auth): cannot determine username
Feb 27 15:58:04 Ebi-Gaming login[3687]: FAILED LOGIN (4) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb 27 15:58:04 Ebi-Gaming login[3687]: pam_securetty(login:auth): cannot determine username
Feb 27 15:58:08 Ebi-Gaming login[3687]: FAILED LOGIN (5) on '/dev/tty1' FOR 'UNKNOWN', Error in service module
Feb 27 15:58:08 Ebi-Gaming login[3687]: TOO MANY LOGIN TRIES (5) on '/dev/tty1' FOR 'UNKNOWN'
Feb 27 15:58:08 Ebi-Gaming login[3687]: pam_mail(login:session): cannot determine username
Feb 27 15:58:08 Ebi-Gaming login[3687]: pam_unix(login:session): close_session - error recovering username


I don't thinks this issue is X-Org related, so i don't add the xubuntu prefix - i'll add it if it is related  #Edit: I'm using xubuntu 18.04.02 atm
also i've found several other posts in other forums which were pretty old , and didn't solve my problem. Thats why im asking here now - best chances to find the cause :D


Thanks
Ebiko

---

### Post by coffeecat on 2019-02-27
This sounds like the problem described in a forum thread from yesterday: [https://ubuntuforums.org/showthread.php?t=2413495](https://ubuntuforums.org/showthread.php?t=2413495)

There's a link to the relevant bug in the thread, although it sounds as though the fix won't be released until next Monday, if I'm reading the discussion in the launchpad thread correctly.

---

### Post by affenmaster02 on 2019-02-27
Well thanks then i'll mark this one as solved then for now. Didn't find the thread before. So i'am not alone , good to know :D

---


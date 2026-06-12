---
title: "Securing Ubuntu 18.04 Guest Sessions"
date: 2018-05-21
forum: General Help
---

### Post by Qassis on 2018-05-21
Purpose of this post:  
Until Ubuntu fixes guest sessions for 18.04 I'd like to open a running discussion on what we (Ubuntu users/community) can do to tighten security for guest session. 
 
Issue: Ubuntu 18:04 LTS (Bionic Beaver) guest sessions (guest account)** is NOT secure**.
1.  "guests" have access to user files and data.
2.  "guests" have access to system files and data.
For many more security issues, details, and where Ubuntu is see:
   [https://community.ubuntu.com/t/brain-dump-on-guest-session-progress/3717](https://community.ubuntu.com/t/brain-dump-on-guest-session-progress/3717)
 
The only secure workaround I see is to continue using Ubuntu 16.04 LTS guest sessions as it is secure and still has 3 years support.
 
Why use a guest account?  Many reasons including:
1. Businesses (or churches, etc.) who allow visiting professionals or customers access to the I-net for what-ever reason.
2. Special needs, i.e. outside my home, for example, I donated a computer to our Senior Center. The seniors use guest session (guest account).  They can more safely do their online banking and other business as there is nothing left behind (account numbers, Social security number, passwords, logins, other personal data) when they log out.
3. In my home, it doesn't matter who comes to visit (grandkids, friends) they can surf to their hearts content.
4. Others?
 
My current workaround for removing guess access to user files:
I tackled "guest" access to user files and have a work around for now for my HOME computers (still using 16.04 at the Senior Center).
In the home directory I ran:
   sudo chmod -R o-rwx *
This removed access (rwx (Read, Write, eXecute) access) by “guest” to my user’s files/folders.
Result:  "guests" can no longer view, run, unzip, or otherwise access other user’s file and data.
This work around does NOT secure guest accounts to any acceptable standard (i.e. they still have access to system files) but is 'good enough' for when my grandkids visit me at home.
BTW, I did not try this recursively from / directory as I trust Ubuntu has reasons for permissions as fielded and didn't want to break anything.
 
I'm hoping for other work arounds to better secure 18.04 guest accounts.
Thank you.

---


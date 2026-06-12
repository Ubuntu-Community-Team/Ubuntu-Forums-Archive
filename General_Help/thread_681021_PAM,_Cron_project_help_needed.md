---
title: "PAM, Cron project help needed"
date: 2008-01-28
forum: General Help
---

### Post by timnugent on 2008-01-28
I'm looking for some guidance before I take steps with the following project.

Let me preface by saying that while I've messed around with, and even professionally supported computers (Mac OS 9 & WIn XP) for about 12 years as both a 'techie' and a user, I have no formal training, and feel like a newbie in Linux waters.

OK, the project: I want to shut myself off the computer between the hours of 10 PM and 7 AM. My wife wants her own account and she doesn't need the restrictions. She will have the password for making any administrative changes, though this admin password will be associated with a third account purposed for administration tasks like installation, etc. The idea is, I get the ability to use the computer during reasonable hours, and only with her input do I get administrative capabilities. It's my 'Odysseus and the sirens' solution to a staying up far too late problem I have.

At least, this is how I conceive of setting things up to now--I'm open to other suggestions.

Reading and poking around Ubuntu chat rooms, I've come up with the following plan: 

1) Back up all the book marks, documents, desktop pictures, settings and installed apps I've customized my system with. Actually, this is a major weak spot in my plan right now. I don't know 
how to do this. Any guidance appreciated.

2) Use PAM (read about it in the Dec. 2007 Linux Format magazine issue from the UK) to work out the permissions and administrative character of each of the three accounts, namely, I have non-admin rights, she has non-admin rights, and a third account has admin rights when we need to change anything.

3) Next, I write a cron script telling the computer to shut down at 10 PM, and to not be available again till 7 AM. Presumably, I put this in the admin account I've been mentioning... then it would affect all three accounts, no? If her account is subject to the same shutdown, it's OK.

I've done a little reading about cron and am using the LFX article from the dec. 2007 issue to study PAM enough to do this, but there are holes-- I don't know how to back up, have never written a script and don't really understand how. If I mess up thouroughly, I know I can reinstall and don't mind doing it, but would like to get it right if possible (of course).

Is this project conceived well? Workable, even? I know I'll be needing more guidance as I go, but this is where I am now, in the conceptualization stage. Help and guidance appreciated, and especially with the backup step to begin with.

Thank you,

Tim Nugent

---


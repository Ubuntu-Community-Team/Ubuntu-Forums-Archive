---
title: "Help! I need to reset my password for version 16.04"
date: 2017-10-20
forum: General Help
---

### Post by ahoffritz on 2017-10-20
[FONT=Ubuntu]Hello, I bought a new linux system for a mini pc. I setup my account, and everything. I go to login and my password does not work. I tried several different ways to reset my password, not working. I try to get to recovery mode while holding down shift, but it never enters because of a message poping up before loading all the way that says "Please enter passphrase for disk cryptswap1 on none! I have to click enter to bypass it. I continue to hold down shift and nothing happens. Is there a way around this??[/FONT]

---

### Post by ian-weisser on 2017-10-20
There's a difference between your account password and your encryption passphrase (key).
Make sure you are entering the correct one at the correct prompt.

Did you intend to have encrypted swap? That usually means your entire system is encrypted.
Account passwords are easy to reset if forgotten. Encryption passphrases are impossible to reset if forgotten - that's the entire purpose of encryption.

Please clarify: Are you asking how to change your account password, or how to change your encryption passphrase? Or are you not sure?

---

### Post by ahoffritz on 2017-10-20
Hello, I’m trying to reset my account password. I can worry about the pass phrase later. I can’t get into my account at all. I can bypass the pass phrase section, I just think thatsgetting in the way of me going into recovery mode.

---

### Post by ian-weisser on 2017-10-20
Is your entire system encrypted?
If so, you will need to decrypt it to change your password - the application you need is encrypted, too.

If only part of your system (like /home) is encrypted, then why do you seem to have encrypted swap?

---

### Post by ahoffritz on 2017-10-21
Those are all good questions. The only thing I can tell you, I setup my account and checked the box upon setup that said encrypt home folder while i was setting up my password. 

I find it odd that passphrase even comes up. Because I know I didnt set that up. Only the Home folder. 

What do I need to do from here?

---

### Post by ahoffritz on 2017-10-21
Okay, I got it! I figured out my password lol I typed it in wrong but figured it out.

---


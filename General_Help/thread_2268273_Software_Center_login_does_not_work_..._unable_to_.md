---
title: "Software Center login does not work ... unable to write review ..."
date: 2015-03-07
forum: General Help
---

### Post by kelt65 on 2015-03-07
I'd like to contribute a review to Software Center, but it appears the login is completely broken, nor does it even indicate what account it is supposed to be using.  I assume UbuntuOne, and it doesn't seem to know that I am signed in to Ubuntu One. How do you write reviews in Software Center?

---

### Post by egeezer on 2015-03-07
Have you got NoScript turned on?  I forgot to whitelist Ubuforums when I did a fresh install somewhere and couldn't access my login in UbuntuOne.  A mistake easily fixed.

---

### Post by coffeecat on 2015-03-07
Are you getting a "login failed" or "cannot access" message similar to the OP in this thread: 

[http://ubuntuforums.org/showthread.php?t=2266455](http://ubuntuforums.org/showthread.php?t=2266455)

The OP sees an error message in Italian, so I'm not sure what the exact wording would be in English. If that is what you are seeing, the fix is in my post #8 in that thread. 

To answer a couple of questions in your post: yes you login with your Ubuntu One account, and Software Centre login was not broken for me when I last did it a couple of weeks ago. Although the forums use the same Ubuntu One SSO login, the Software Centre login is entirely separate from the forum.

**Edit**: Just to add...

> **kelt65 said:**
> I assume UbuntuOne, and it doesn't seem to know that I am signed in to Ubuntu One.

Even if you are already logged into Ubuntu One, you have to sign into Software Centre using your Ubuntu One login credentials. This is because you are not signing in via a web browser. If the fix I posted in the other thread and the screenshots coldraven posted in post #5 in that thread don't help, post screenshots or details of what you are seeing when you try to log into Ubuntu One in the Software Centre.

---

### Post by jbaerboc on 2015-03-18
I have the same issue as the OP. I'm in Ubuntu GNOME Edition 14.10. I checked my keyring but nothing in there related to Ubuntu One. It's all Google Chrome stuff. Any other ideas?

---

### Post by markling on 2015-04-19
I have the same problem. It's been a problem for years.

It seems to use OpenID poorly. E.g.

I just logged in to Ubuntu Forums (UF). UF didn't even ask for a password. It just said click here to confirm your OpenID. I clicked. It logged me in.

But Software Center wanted a password. I couldn't remember password. So I did the password reset (email, click, new password form). After I submitted my new password, SF said: "Invalid OpenID transaction".

That's all it said. No ryhme nor reason. It just wouldn't let me reset my password.

That's when I logged in here, without any trouble at all.

---

### Post by markling on 2015-04-19
It's a problem with the password reset web link.

I gave ubuntuforums all permissions in NoScript.

But when I clicked on the web link in my password reset email, and changed my password, it still failed with the messge: "Invalid OpenID transaction"

But the change password/login was successful when I used the alternative reset code and pasted that into the password form in Software Center. I did this, changed my password, and am now logged in to SF, for the first time in years. Effig Chaffidge. Really.

---

### Post by pazuzuthewise on 2015-08-28
I'm having the same issue on Ubuntu Gnome 15.10 x32. The login window appears, seems to be loading something and stalls there. 
[[IMG]http://i.imgur.com/gyMWUSct.png[/IMG]]("http://imgur.com/gyMWUSc")

---


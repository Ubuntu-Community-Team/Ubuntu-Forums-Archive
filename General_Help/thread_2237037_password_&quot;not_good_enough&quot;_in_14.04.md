---
title: "password &quot;not good enough&quot; in 14.04"
date: 2014-07-30
forum: General Help
---

### Post by david12 on 2014-07-30
In the US in 1974 (or so) someone in the government decided that the use of seatbelts in cars was so important that cars should not start unless all aboard had their seatbelts fastened first.  The system to do this was called "interlock."  It didn't last long.  Well intentioned though it may have been, the public found that it was more of an imposition than a benefit.

The road to hell is paved with good intentions. -[ Saint Bernard of Clairvaux]("https://en.wikipedia.org/wiki/Bernard_of_Clairvaux")

The nanny mentality that has gripped the powers-that-be at Ubuntu is an unfortunate.  I predict the password "not good enough" restriction will be removed in time, although the advice is welcome and should remain.

**Please, does anyone know of a comprehensive guide to setting admin and user passwords that bypasses the complexity test that Ubuntu has imposed?**

I've picked up bits and pieces about the use of the "passwd" command.  This webpage [http://www.computerhope.com/unix/upasswor.htm](http://www.computerhope.com/unix/upasswor.htm) also refers to "complexity test."  What I'd like to do is to set passwords without regard to what someone else thinks is "good enough."

We could do so in previous versions.

Thanks.

---

### Post by TheFu on 2014-07-30
I've never seen this issue - guess my passwords ARE complex enough.
However, it has been a long standing solution that typing in the same password 3 times in the **passwd** tool WILL override any complexity issues. I haven't tested this recently, but would be shocked if it wasn't true still.

Don't know about any GUI password management - don't use any.  

If using ssh-keys, then password complexity doesn't matter for remote connections AND it is considered to be much more secure.

---

### Post by ian-weisser on 2014-07-30
Well, I can sure live without all the nanny-state whining. As someone who survived a very nasty car crash thanks entirely to government-mandated safety design and devices, I can happily tell you that the answer you seek is in the passwd manpage.

TheFu is right. You can set any password you wish. The password complexity metric used in the installer and the Users & Groups control panel is merely advisory.

---

### Post by uRock on 2014-07-30
You can easily apply a password to a new account using the following command,```
sudo passwd username
```Follow the prompts. I was able to apply the password **crackers** to an account with no complaints from the terminal. It looked like the following. ```
ubuntu@ubuntu:~$ sudo passwd blah
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```Do I recommend such a weak password? No, but I have done so for non-admin accounts in the past.

---

### Post by TheFu on 2014-07-30
There is NO NEED for sudo on the passwd command, if you are changing the current user's password.  This is how every user is supposed to manage their own password changes after all.

---

### Post by uRock on 2014-07-30
Too true. I was using it to set a password for a freshly made standard user account. After reading a Draios blog link you shared a few days ago, I'd never use a simple password again.

---

### Post by TheFu on 2014-07-30
We don't allow password-based logins for any network connections, only keys.  If you look through the log files, you'll see why. It is a dangerous world out there, trying REALLY HARD to get inside our networks and computers.

When it comes to [safe passwords - length matters]("http://blog.jdpfu.com/2011/08/30/easy-technique-for-secure-easy-to-type-passwords-size-matters"). It really isn't that hard to have a longer password.

---

### Post by uRock on 2014-07-30
> **TheFu said:**
> We don't allow password-based logins for any network connections, only keys.  If you look through the log files, you'll see why. It is a dangerous world out there, trying REALLY HARD to get inside our networks and computers.

When it comes to [safe passwords - length matters]("http://blog.jdpfu.com/2011/08/30/easy-technique-for-secure-easy-to-type-passwords-size-matters"). It really isn't that hard to have a longer password.

Word! Or should I say, "anti-word"?

As for the OP, If it is possible for the creators of Ubuntu to add in the restriction, then I am sure it is possible to remove the restriction, but I am not sure how, yet.

---

### Post by grahammechanical on 2014-07-30
Just the other day I saw a post on the forum where someone was complaining that Ubuntu would shut down even if he/she still had applications open. The OP wanted the confirmation dialog to report that he/she had left some applications open. Just like Windows does.

Actually, the confirmation dialog does ask if we want to shut down and close all applications. But not that we have some open. So, we complain that nanny is restrictive and then we complain that nanny didn't stop us from hurting ourselves.

Regards.

---

### Post by uRock on 2014-07-30
@ OP, The following link appears to be a great starting point for seeking out the configuration you want.

[http://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords](http://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords)

---

### Post by mc4man on 2014-07-31
"The nanny mentality that has gripped the powers-that-be at Ubuntu..."
This wasn't Ubuntu's doing, changes came from Gnome dev's.
 (- though Ubuntu hasn't helped in any way, for add. users they could implement setting password at first login which would bypass the tests & just require the default min. of 6 characters 
Actually for 1st. user (install) Ubuntu is very liberal. For that user 1 character is the min.

---


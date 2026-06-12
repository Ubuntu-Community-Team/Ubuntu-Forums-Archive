---
title: "Password"
date: 2013-01-17
forum: General Help
---

### Post by waltwin on 2013-01-17
I understand the need for a strong password. It would appear that it should contain letters, numbers, various characters. That is the easy part. 

To me, the difficult part is when it comes time to install upgrades or any time a password is required, entering that conglomeration of numbers and characters.

My question: "Is there a way to store that password so that it will be automatically inserted"?

waltwin

---

### Post by sffvba[e0rt on 2013-01-17
I do not think an overly complicated password is needed to log into your system.  As you said it can be difficut and frustrating to have to type it in every time, and if someone gains physical access to your machine they have many ways to get to your data without needing your password.


404

---

### Post by papibe on 2013-01-17
Hi waltwin.

First, I'd try to convince you that is better to request a password every time you need an admin task.

Then, take note that ***very*** long passwords are secure password, even if there's no number or symbols. For instance, this is **22**-characters password is very easy to remember:
```
idontlikelongpasswords
```
Let us know how it goes.
Regards.

---

### Post by waltwin on 2013-01-17
Thank you for your response. Actually I am retired and nobody has access to my machine. I guess I am more concerned about someone hacking my password on line.

---

### Post by papibe on 2013-01-17
If you really want to do this at your own risk, you need to educate yourself first a little bit.

Take a look at this [community help page]("https://help.ubuntu.com/community/Sudoers"), and this [old forum tutorial]("http://ubuntuforums.org/showthread.php?p=7118727#post7118727").

Once you understand what you are doing, you'lll understand this answer provided [here]("http://askubuntu.com/questions/135821/can-i-run-sudo-without-entering-a-password").

Regards.

---

### Post by snowpine on 2013-01-17
> **waltwin said:**
> Thank you for your response. Actually I am retired and nobody has access to my machine. I guess I am more concerned about someone hacking my password on line.

Unless you have opened ports, the default setup of Ubuntu does not expose your system to the world, meaning that someone online cannot hack your computer's password.

Of course this doesn't mean you are safe from, for example getting your LinkedIn or Facebook password hacked, but that is not a Linux-specific issue.

Lots of great info here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by waltwin on 2013-01-18
> **papibe said:**
> If you really want to do this at your own risk, you need to educate yourself first a little bit.

Take a look at this [community help page]("https://help.ubuntu.com/community/Sudoers"), and this [old forum tutorial]("http://ubuntuforums.org/showthread.php?p=7118727#post7118727").

Once you understand what you are doing, you'lll understand this answer provided [here]("http://askubuntu.com/questions/135821/can-i-run-sudo-without-entering-a-password").

Regards.
I understand the folly of eliminating the protection of sudo and it is something I would not consider. My problem is trying to understand ALL of the verbiage associated with Passwords and other security issues. 

I am sure that is where I read about the twenty character password and I still wonder about entering such a password when doing updates etc.. Is it not correct that when updates are required a password has to be entered?

---

### Post by alphaamanitin on 2013-01-18
I wouldn't be concerned with some one hacking into your computer, just use an easy password for you for the computer. **[color=Red] Now I would not advice that for any of your online accounts.**[/color] 

Look into something like KeePassX for password management, but in the case of your computer, if there is no physical access from anyone suspicious don't bother with a huge complex password.

AlphaA

---

### Post by Cheesemill on 2013-01-19
> **waltwin said:**
> Is it not correct that when updates are required a password has to be entered?

This isn't correct.

Since 11.10 a password has only been needed for the installation of new packages, upgrading existing packages no longer requires password confirmation.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

---


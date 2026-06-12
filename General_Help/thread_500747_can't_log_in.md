---
title: "can't log in"
date: 2007-07-14
forum: General Help
---

### Post by BashfulBud on 2007-07-14
HELP!

I installed 7.04 a few days ago and everything was working fine. Then, I think I messed up something and now I can't log in.

I set it up as a dual boot and resized my drive that was running XP Pro.

A day or two after I set it up, I was adding a user and made some changes to my original user. Don't ask me what I did because I don't remember exactly.

Anyway, I tried to run the recover option and that didn't work, I also tried the trick I read about setting up the password by editing and adding rw init=/bin/bash and that didn't seem to work since I get an error about not having ownership.

You'll have to forgive me if this sounds confusing, I'm trying to learn. How do I recover from this?

Thanks in advance.

Bud

---

### Post by Jussi Kukkonen on 2007-07-14
You'll need to provide exact error messges and try to describe how logging in actually fails, otherwise it's just not possible for anyone to help you.

---

### Post by HermanAB on 2007-07-14
You can boot into single user mode and then set the passwords.  However, you may be better off re-installing Ubuntu.  It only takes about 30 minutes anyway.

---

### Post by BashfulBud on 2007-07-14
> **HermanAB said:**
> You can boot into single user mode and then set the passwords.  However, you may be better off re-installing Ubuntu.  It only takes about 30 minutes anyway.


I'd rather do that. I'm a bit rusty with me Unix skills. I want to keep the partitions that the original install set up. Can I just format the ubuntu amd grub partitions?

---

### Post by HermanAB on 2007-07-14
Yup, always have a separate /home partition (I make a separate /export partition too).  That way you can re-install and format everything except your precious data.

---

### Post by BashfulBud on 2007-07-15
I tried to reinstall and ran into an error. It said there was an error while installing the kernel and to check the log  or check console 4. So now what?

---

### Post by BashfulBud on 2007-07-16
I was able to look at the log and saw that it failed with 'error cod 1'. Everything is fine when I reinstall up to the point of installing the kernel and then I get an error that it failed and then I can try installing a different kernel, but the same thing happens. The log didn't tell me how it failed, just that it was 'error code 1'. What does that error code mean?

---

### Post by BashfulBud on 2007-07-20
I was able to reinstall after going into disk manager in XP and deleting the partitions that Ubuntu created. I then did a fresh install selecting 'guided install using available free space on drive' or whatever that option was. XP was not touched and Ubuntu installed with no problems. Now that I think of it, I probably could/ve done all of that without going into XP. Oh well. It's working fine now.

---


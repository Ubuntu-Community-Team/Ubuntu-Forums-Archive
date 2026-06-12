---
title: "Can't login to text console, GDM does fine."
date: 2007-08-17
forum: General Help
---

### Post by Epistis on 2007-08-17
When I login to GDM with my user/pass, all goes well.

However, anytime I reach a text console (by X crash, or just selecting a TTY terminal), it says my login/pass is incorrect.

Any ideas?

:popcorn:

---

### Post by jamvegan on 2007-08-18
Hm...maybe a login shell issue?  What is the output of:
```
grep $USER /etc/passwd
```
or if you don't want to post the full output, what is after the last colon?

---

### Post by Epistis on 2007-08-18
grep $USER /etc/passwd output:

```
epistis:x:1000:1000:J.R.,,,:/home/epistis:/bin/bash
```

Thanks for the quick reply!

---

### Post by jamvegan on 2007-08-18
Well, that looks exactly like it should.

The only other thing that I can think of is that with some keyboard/terminal combinations certain characters do not register properly.  You might try typing your password in a terminal at the login prompt (rather than the password prompt) so that you can see it echoed.  If any of the characters do not appear as they should, perhaps that's the problem.

I'll keep pondering this and get back to you if anything else occurs to me.

---

### Post by Epistis on 2007-08-18
> **jamvegan said:**
> Well, that looks exactly like it should.

The only other thing that I can think of is that with some keyboard/terminal combinations certain characters do not register properly.  You might try typing your password in a terminal at the login prompt (rather than the password prompt) so that you can see it echoed.  If any of the characters do not appear as they should, perhaps that's the problem.

I'll keep pondering this and get back to you if anything else occurs to me.

Ah ha! Well, the characters display properly,  but the problem is that caps lock does not have any effect, and my password is in all caps. So, now I can login, but it's a pain to type my password, as it's got numbers mixed in, so shift-on/type/shift-off/type. You get the picture.  :)

Thanks a million for your help!

I'd still like to get this fixed, where caps lock worked, if you have any thoughts on it, but I honestly don't care anymore. It's 1:11am (it just passed 1:11:11am), and I'm just happy that I can login. :P

Thanks again!

---

### Post by jamvegan on 2007-08-18
Don't know how to fix the caps lock issue.  I did some searching a while back on the issue of num lock (also doesn't work in tty), but found no solution.

Glad you can log in, though! :-)

---

### Post by anasofiapaixao on 2007-09-06
I found this funny because I have the exact opposite issue. I can login in a terminal but not through GDM: it says the login info is incorrect. Can it have something to do with the pass having a 'special' character (underscore)?

EDIT: I found it. It appears that was the case - **GDM doesn't accept passwords with non-alphanumeric characters**. Changing to an alphanumeric password solves the problem.

---


---
title: "Edit/view user info in console"
date: 2008-01-08
forum: General Help
---

### Post by kurellajunior on 2008-01-08
Hi folks,

Sorry for this basic question.

How can I see user info in the console? Is there an equivalent to ```
/etc/group anywhere
```?
And how is the command to change user's facts (home directory, shell, etc)

Thanks, Jan

---

### Post by kurellajunior on 2008-01-08
Ok Double <TAB> showed me at least the usermod command :)

Still the question, how the info is displayed?

Jan

---

### Post by geirha on 2008-01-08
**groups *username*** will show which groups a user is a member of
**chfn** can be used by a user to change his own information, like name and phone-number
**chsh** can be used by a user to change shell
**usermod** can be used by root to change any of this for any user

Read the man-pages for these commands with ```
man command
```

Also, all the information these commands alter, are stored in /etc/passwd, /etc/shadow (the password hashes), and /etc/group

---

### Post by kurellajunior on 2008-01-08
Thanks, the [FONT="Fixedsys"]/etc/passwd[/FONT] and the [FONT="Fixedsys"]groups[/FONT] command was what I needed.

See you, Jan

---

### Post by rubicon on 2008-01-08
Also, try ```
finger *user*
```

---

### Post by kurellajunior on 2008-01-08
That's exactly what I looked for!

Great, thanks a lot

---


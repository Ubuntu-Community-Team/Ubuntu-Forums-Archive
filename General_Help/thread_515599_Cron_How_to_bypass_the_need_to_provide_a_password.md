---
title: "Cron: How to bypass the need to provide a password?"
date: 2007-08-02
forum: General Help
---

### Post by jackn on 2007-08-02
I've set up rsync in order to mutually backup two boxes of mine. 

In order to automate the backups, I'd like to create a cronjob.

Thing is, I've set up rsync to require a password.

How can I create a cronjob that will run although it requires a password and the user isn't around to provide it? How can you pass the password to cron?

I realize there are workarouinds: scrap the password requirement in rsync, or use ssh with key authentication.

But this is a general question, not about my particular situation: how do you automatically run something that requires a password? The situation arises in other contexts, too, and I'd simply like to learn a general solution for it.

This [question]("http://ubuntuforums.org/showthread.php?t=231078") has already been asked, with no answer.

---

### Post by nick_h on 2007-08-02
I think you need the *--password-file* option.

The man entry reads "This option allows you to provide a password in a file for accessing a remote rsync daemon."

---

### Post by jackn on 2007-08-03
OK, nick_h, that will do it.

Just goes to show - I was sure I had looked up the manpages for rsync looking for 'password'. Apparently not... 

Read the manual... very carefully!...

I've recently also learned about the 'credentials' flag in smbmount. So, the general solution to passing a password to an automated run would seem to be to a flag and file pair, with the file harboring the username : password combination.
Such a file, it is perhaps useful to remind, needs to have strict permissions.

Finally, I would say that while the spirit of the solution is general, whether and how it is implemented depends on the specific application.

This prompt response was very useful to me. 
Thank you, nick_h.

---

### Post by nick_h on 2007-08-03
If the man entry is long you can always pipe it to grep if you are searching for something:
```
man rsync | grep password
```
or if you prefer a GUI then use the find in yelp:
```
yelp man:rsync
```

---


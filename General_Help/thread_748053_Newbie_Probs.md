---
title: "Newbie Probs"
date: 2008-04-07
forum: General Help
---

### Post by schmengei on 2008-04-07
There are currently 190 updates available to me when I run Update Manager. When I go to install updates this is the error msg I receive. Being a noob, I have no idea where to go or how to correct the error msg. Please Help!


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
_______________________________
Peter

---

### Post by tombott on 2008-04-07
The answer is hopefully in the error message itself.

Open the Terminal and type the following:

```
sudo dpkg --configure -a
```

You will need to enter your password.

---

### Post by schmengei on 2008-04-07
tombott,
the password 13280 when typed in gives me a "sorry try again" error msg. Thnks for responding

---

### Post by forrestcupp on 2008-04-07
That command is what you need to do to fix it.  Make sure you are entering your login password correctly when it prompts you (and don't post passwords on the net if you know what's good for you).  Does your password work on anything?  

If your password just doesn't work on anything at all, you can easily reset it by following [these instructions](http://ubuntuforums.org/showpost.php?p=4624705&postcount=7).  Don't do that unless you have forgotten what your login password is.

---

### Post by The Cog on 2008-04-07
Oops - the line with 13280 in it was part of tombotts signature (it appears automatically at the bottom of every message he posts), it was not the passord that you needed to enter. You enter the command **sudo dpkg --configure -a** as tombott recommended, then when you are asked for your password, you enter your own login password. 

It's a security double-check really, to make sure it's not someone else messing at the keboard while you are away getting a coffee or something.

---

### Post by forrestcupp on 2008-04-07
> **The Cog said:**
> Oops - the line with 13280 in it was part of tombotts signature (it appears automatically at the bottom of every message he posts), it was not the passord that you needed to enter. 
Good eye.

---


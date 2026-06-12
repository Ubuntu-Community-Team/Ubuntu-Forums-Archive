---
title: "How do I use the startup items option?"
date: 2015-10-20
forum: General Help
---

### Post by michael-piziak on 2015-10-20
Trying to add Chromium Web Browser as a startup application/item, but how to do it?

screenshot below

---

### Post by deadflowr on 2015-10-20
You need to add the command to launch it.
I think the command for chromium is **chromium-browser**

---

### Post by howefield on 2015-10-20
Or 

```
chromium-browser %U
```

Put whatever you want into the comment field.

---

### Post by michael-piziak on 2015-10-20
> **howefield said:**
> Or 

```
chromium-browser %U
```

Put whatever you want into the comment field.

Yep, the first command suggested didn't work

trying chromium-browser %U   now

also, I have a family member that likes Firefox, so I would like to add it to the startup menu and have it open 2nd over top of Chromium if possible please

---

### Post by michael-piziak on 2015-10-20
> **michael-piziak said:**
> Yep, the first command suggested didn't work

trying chromium-browser %U   now

also, I have a family member that likes Firefox, so I would like to add it to the startup menu and have it open 2nd over top of Chromium if possible please


ok that worked - thanx!

Now, if I can add Firefox 2nd, it should open 2nd right?  Please tell how to.

---

### Post by howefield on 2015-10-20
> **michael-piziak said:**
> ok that worked - thanx!

Now, if I can add Firefox 2nd, it should open 2nd right?  Please tell how to.

Not sure I understand what you mean, but you can add a Firefox to the startup applications just the same as you did for chromium except the command would be

```
firefox %U
```

---

### Post by michael-piziak on 2015-10-20
> **howefield said:**
> Not sure I understand what you mean, but you can add a Firefox to the startup applications just the same as you did for chromium except the command would be

```
firefox %U
```

What I was getting at is that I wanted both Chromium Browser and Firefox Browser to be started up upon boot; however, since I have 2 family members that prefer Firefox, I wanted Firefox browser then one to be on screen when computer is started by them - as Chromium browser is what I use and may confuse them (plus I have some bookmarks and such I don't want them to see, as well as Google puts things on my Chromium screen I sometimes don't want them to see - like certain adult website(s) I visit).

Both browsers open upon startup now, but regardless if I put Chromium into the startup item(s) first or put Firefox in first, it always opens Chromium as the browser seen on screen.  I thought maybe it was an alphabetical order thing (that I put in the name field), so I named Firefox as "A Firefox Browser," and still get Chromium on screen predominately.  So there is something about Chromium naturally starting with the letter C, perhaps, and Firefox starting with F, something inside that makes Chromium always appear on screen.

Hmmm - a mystery to me!

---

### Post by howefield on 2015-10-20
> **michael-piziak said:**
> ...a mystery to me!

Not necessarily,

If each user has there own account on the machine, they will have their own set of startup applications, so have your account startup applications include Chromium and put Firefox into the other family members account startup applications.

---

### Post by michael-piziak on 2015-10-20
> **howefield said:**
> Not necessarily,

If each user has there own account on the machine, they will have their own set of startup applications, so have your account startup applications include Chromium and put Firefox into the other family members account startup applications.

Yep, but I got tired of typing my administrator password in to boot the system; and, I got rid of the maid that was secretly using my system.

Can it be set up that I choose to login without a password and have others use guest login?

---

### Post by Geoffrey_Arndt on 2015-10-20
Hmm, Michael_P,

On the standard multi-user system, you create one or more standard users (I forget the term, but they are non-admin (non-sudo) users).   But each person can login to ubuntu using their own user ID and their own specific password.   You could set up such an account or profile for the maid too, and assign her a unique password.   Remember, by default, standard users cannot access other user files or install/unistall programs (unless you elevate their rights).   Each user can turn on the PC and do a full startup and login . . . your password is not needed.

So, that seems a much simpler and safer way of running Ubuntu than just one account (which can actually be kinda bad).

---


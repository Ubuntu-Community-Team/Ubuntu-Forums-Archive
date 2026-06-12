---
title: "Password won't show in terminal"
date: 2018-06-10
forum: General Help
---

### Post by petesas on 2018-06-10
Hey!

I'm having this weird problem that I can't execute anything in the terminal because the password won't type out.
I'm running lubuntu 17.10.

I open up LX terminal and type something like sudo apt-get remove transmission
then i get asked a password: (whatever I type here shows not up)
I try to type in the password but it won't show up. the cursor does not move.
i hit enter and lubuntu says that this didn't quite work out. I fail 3 times and am back to the start.

the password is correct, the issue is that i just can't type it in.
i tried alt+ctrl f1 and I experience the same problem.
I can put in the login but the password cursor does not move.
I type in the password but it doesn't show up.

Does anyone have the same problem?

---

### Post by deadflowr on 2018-06-10
Passwords in the terminal are invisible by default.
Just type it as best you remember it and hit enter.

Edit: to Add,
Old but still useful:
[https://www.omgubuntu.co.uk/2016/08/make-sudo-password-visible-terminal]("https://www.omgubuntu.co.uk/2016/08/make-sudo-password-visible-terminal")
In case you really want to have a more visible password field.

---

### Post by QIII on 2018-06-10
Just to put things in perspective:  Having started with UNIX in the 70s, I was alarmed later the first time I encountered asterisks echoing when I was entering a password.  I thought *that* was some sort of error!  :)

---

### Post by petesas on 2018-06-10
Guys, thank you! I normally work on kubuntu and there you can at least see some asterisks. The problem is solved!

---

### Post by deadflowr on 2018-06-10
> **petesas said:**
> Guys, thank you! I normally work on kubuntu and there you can at least see some asterisks. The problem is solved!

I never seen any of the terminals from any of the Ubuntu flavors show any input for passwords.
Kubuntu included.

That said,
You can mark this thread solved for reals,
see: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by bodhin2 on 2018-06-10
QIII that is funny

deadflowr - i agree - never saw that passwords show when typed/

---

### Post by oldos2er on 2018-06-10
You can edit /etc/sudoers to show asterices when entering a password if you wish. See [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---


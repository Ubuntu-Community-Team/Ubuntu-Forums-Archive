---
title: "Security Question"
date: 2007-07-03
forum: General Help
---

### Post by waveslider on 2007-07-03
I just learned about the users program, which prints the names of currently logged in users. (duh)

It prints my username 3 times, which means I have 3 open sessions, correct?

So, I logged out and logged back in, and users now says I have 2 open sessions.

How is that possible? Does this mean that some intruder has somehow managed to login to my account?

[note: i am the only person who uses this computer (at least, I HOPE I am)]

Thanks everyone!

---

### Post by AlexenderReez on 2007-07-03
it is seems like what you thought ....you suppose only have one user session ..if you have more than that mean either you made another or somebody made it....

---

### Post by waveslider on 2007-07-03
Thanks!

What should my next step be? How can I find out who logged in and what they did?

---

### Post by AlexenderReez on 2007-07-03
ofcouse they need to know your password ..by the way...you can delete its account by entering 'user and group'  ...or change it.....they may hack/crack your system easily if you enable and using remote desktop...or ssh........

---

### Post by kuja on 2007-07-03
Check out /var/log/auth.log. Also check that you don't have any ttys logged in (they count too)

---


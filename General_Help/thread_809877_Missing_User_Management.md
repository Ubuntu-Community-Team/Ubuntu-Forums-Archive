---
title: "Missing User Management"
date: 2008-05-27
forum: General Help
---

### Post by stakh on 2008-05-27
Hello,

I installed Kubuntu 8.04, and I would like to add multiple users to my computer, but System and Settings is missing an User Management option. I also checked the Advanced tab, but no luck.

Any ideas on what's going on? How could I restore/install the User Management application? And failing that, could someone provide me an alternative solution?

---

### Post by LaRoza on 2008-05-28
> **stakh said:**
>  And failing that, could someone provide me an alternative solution?

I never use the GUI tools. You can use the command:

```

sudo adduser

```

Simple to use.

---

### Post by stakh on 2008-05-28
> **LaRoza said:**
> I never use the GUI tools. You can use the command:

```

sudo adduser

```


Thanks for the help!

For documentation purposes, here is what I did to solve the issue:
- install kduser
- in konsole, issue ```
$kdesudo kduser
``` (to enable root access)

Later on I found that User Management could also be installed via the adept installer (no clue why it's not installed by default).

---

### Post by jpuhalski on 2008-06-07
I tried using **install kduser** but it did not work, said Invalid operation kduser.  I also searched for it from the add/remove program and could not find it.  you said it could be installed via the adept installer but could not find it there either...I found out for anyone that wants to know that it is case sensitive.  in the add/remove programs search for **KUser** and it will come up.  check it and apply.

thanks
john

---

### Post by dancapp on 2013-04-14
What I don't get is - where has the old User Management application gone? I don't like KUser and I'd rather have the old one as part of my SystemSettings. There doesn't seem to be any information about how to achieve this out there at all. It seems like such a big and obvious problem.

---

### Post by overdrank on 2013-04-14
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


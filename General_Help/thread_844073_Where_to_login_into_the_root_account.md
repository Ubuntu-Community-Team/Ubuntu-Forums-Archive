---
title: "Where to login into the root account?"
date: 2008-06-29
forum: General Help
---

### Post by Nothingpp on 2008-06-29
Well, title says it.

I tried the login screen, said that the system admin account can't be logged in from this login screen.

help? 

Tyvm.

---

### Post by sdennie on 2008-06-29
It's against forum policy to give a tutorial on how to enable the root account: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by wormser on 2008-06-29
With Ubuntu you do not log into root.  Instead Ubuntu uses sudo and gksudo to give you root privileges.  More [here]("https://wiki.ubuntu.com/RootSudo").

```
sudo command
```

---

### Post by marshall.robert on 2008-06-29
check your inbox

---

### Post by ilrudie on 2008-06-30
> **vor said:**
> It's against forum policy to give a tutorial on how to enable the root account: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Is this true?  You aren't allowed to tell someone how to enable root in the forums?

---

### Post by lisati on 2008-06-30
> **ilrudie said:**
> Is this true?  You aren't allowed to tell someone how to enable root in the forums?
It's a safety feature.......it's too easy to make a mess of things from "root", which is why we have sudo & gksudo which ask for a password, kinda like "are you sure?"

---

### Post by ilrudie on 2008-06-30
I understand the purpose of sudo but i did not know it was against forum rules to explain to someone how to enable the root account as #2 claims.  Thats all I was wondering.  After all this whole GNU/Linux thing is about freedom and in my opinion freedom includes the right to enable root, login as root, and learn by breaking/fixing if you so choose.  No big deal though.  I'm sure a quick google search will allow anyone so inclined to enable root.

Also does this restriction include explaining how to get a root shell and/or how to switch to the root user from the command line?

---

### Post by Gunman1982 on 2008-06-30
If you read the forum thread/policy why such tutorials are not allowed it gives some good reasons. And you still have the freedom to do it.

---

### Post by WRDN on 2008-06-30
Just because Ubuntu allows for the user to have the freedom to configure their system to their own liking, doesn't mean this should be done at the expense of security.

The reason Windows often gets viruses is because, by default, a user is given administrator privileges. This means, any program can run, without permission. In stark contrast, in Ubuntu the user must give permission by usinig the root password if they wish to change the system files themselves. This means that, a program in Ubuntu could potentially destroy your own files and user folder, but it cannot affect the workings of the system itself.

I agree that its good to have freedom, but there must be rules for a users own protection.

---

### Post by ilrudie on 2008-06-30
> **Gunman1982 said:**
> If you read the forum thread/policy why such tutorials are not allowed it gives some good reasons. And you still have the freedom to do it.

Where is this?  Can you link to it.  I have read the code of conduct and did not see anything about this?

Is this like an implied rule that comes from the directive to assume users on the forums are green?

---

### Post by aysiu on 2008-06-30
It's all in the link in post #2.

---


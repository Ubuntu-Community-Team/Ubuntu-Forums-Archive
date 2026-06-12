---
title: "sudo chown -R doesn't work. I'm going slightly mad..."
date: 2021-03-08
forum: General Help
---

### Post by GhX6GZMB on 2021-03-08
New Lubuntu install on a machine. New sudo/admin user works perfectly.
Adding two new users also work as they should.

Decided to clone my sudo admin user to one of the new users by copying /home/"sudousername" (including hidden files/dirs) to that user's /home directory.
Also no problem.
But changing the ownership of the new /home/... files/dirs is not possible. "chown" simply doesn't work,
```
sudo chown -R newuser:newuser /home/newuser/*
```

I'm tearing my hairs out here. I can manually change every file's ownership in PCManFM-Qt, but that's no end tedious.
Any ideas?

Thanks.

---

### Post by ajgreeny on 2021-03-08
I am not quite following what you're doing nor why but what is the final /* in your command; it is not needed às far as I can see?

Using the -R option makes the command recursive and if there is a space between the /home/newuser and the following /*, which there appears to be, you are pointing at the root folder as well as that home folder, a very dangerous thing to do.

---

### Post by GhX6GZMB on 2021-03-08
There's no space. Apparently [CODE] makes it look that way.

---

### Post by ajgreeny on 2021-03-08
OK, but I still don't think it's needed as the -R option means everything in /home/newuser will change, or should change ownership without that final /*.

Perhaps that is what is stopping the change from happening.

---

### Post by HermanAB on 2021-03-08
This should work:
$ sudo chown -R newuser: /home/newuser

unless you have AppArmor enabled.

(If you are wondering about the syntax, the : implies the same user and group)

---

### Post by GhX6GZMB on 2021-03-08
Interesting.
I'll try with
```
sudo chown -R /home/newuser
```

---

### Post by ajgreeny on 2021-03-09
That won't work; you must have the ***newuser***: for the command to know who the user is to be changed to.
Without that information nothing will change.

---

### Post by The Cog on 2021-03-09
To be specific - like this:
```
sudo chown -R newuser:newuser /home/newuser
```
An extra gotcha using /home/newuser/* is that the * only expands to be all visible files, and would not include hidden items like .config or .bashrc.

---

### Post by ActionParsnip on 2021-03-09
Why is this being ran at all? Seems weird............

---

### Post by ajgreeny on 2021-03-09
> **ActionParsnip said:**
> Why is this being ran at all? Seems weird............
Agreed; hence my post #2 asking what it was all for.

---

### Post by GhX6GZMB on 2021-03-09
> **The Cog said:**
> 
An extra gotcha using /home/newuser/* is that the * only expands to be all visible files, and would not include hidden items like .config or .bashrc.

VERY interesting. Seems this is the source of my problems, as the hidden files didn't get changed.

EDIT:
Brilliant:
```
sudo chown -R newuser:newuser /home/newuser
```
worked perfectly.

Thanks.

---

### Post by GhX6GZMB on 2021-03-09
> **ActionParsnip said:**
> Why is this being ran at all? Seems weird............

Explained in my OP. I'm cloning a user. If you have a better way, please chime in.

---

### Post by The Cog on 2021-03-10
Beware you are also cloning the user's settings, such as stored browser bookmarks, history and passwords, ssh keys and so on - all personal settings and information.

---

### Post by GhX6GZMB on 2021-03-10
> **The Cog said:**
> Beware you are also cloning the user's settings, such as stored browser bookmarks, history and passwords, ssh keys and so on - all personal settings and information.

Thanks. I'm aware of that, but this is a virgin install.

---


---
title: "hard drive is running hot after the Load Cycle ugly fix"
date: 2008-04-19
forum: General Help
---

### Post by turned2black on 2008-04-19
Hello,

I had the hard drive cycle load bug and used the ugly fix, which worked:) However, the hard drive now runs hot (50-60C after a couple of hours browsing the Net). I understand that I need to change the value from 254 to around 220 or so, but I go to edit the file and it won't let me save the changes because of permissions.

What to I need to do to edit the file from the terminal?

I'm sorry I'm such a newbie.

Cheers,
T2B

---

### Post by LaRoza on 2008-04-19
> **turned2black said:**
> Hello,

I had the hard drive cycle load bug and used the ugly fix, which worked:) However, the hard drive now runs hot (50-60C after a couple of hours browsing the Net). I understand that I need to change the value from 254 to around 220 or so, but I go to edit the file and it won't let me save the changes because of permissions.

What to I need to do to edit the file from the terminal?

I'm sorry I'm such a newbie.

Cheers,
T2B
Not sure what file you need to edit, but this command will open the text editor so you can edit any file. Make sure you keep a backup of the old file in case something goes wrong.

```

gksudo gedit

```

If you put the path to the file you want to edit after, it will open it.

---

### Post by turned2black on 2008-04-21
Many thanks!

---


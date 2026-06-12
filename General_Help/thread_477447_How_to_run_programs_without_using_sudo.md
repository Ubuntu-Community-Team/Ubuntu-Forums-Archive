---
title: "How to run programs without using sudo?"
date: 2007-06-18
forum: General Help
---

### Post by glave on 2007-06-18
I was told once before to make sure that I am part of the sudo and admin groups to avoid doing sudo for every command I want. I have recently came back from Windows, but I'm finding that this doesn't work any more for me.

I'm already a member of the admin group, but sudo didn't exist. I created it and joined it, but still being requested to sudo anytime I do anything. I know I'm missing something simple...!

---

### Post by energiya on 2007-06-18
> **glave said:**
> 
I'm already a member of the admin group, but sudo didn't exist. I created it and joined it, but still being requested to sudo anytime I do anything. I know I'm missing something simple...!

You should sudo only when an app needs root to run, so I don't understand the "sudo anytime I do anything" part. Anyway, I think you're talking about the sudoers file?

I understand that you don't want to be asked for password?
```

sudo visudo

```
and add
```

<USER> <YOUR IP>( if static, or ) ALL = (ALL) ALL

```

**NOTE: DOEING THIS IS VERY UNSAFE !!!**

---

### Post by dreadlord_chris on 2007-06-18
> **glave said:**
> I was told once before to make sure that I am part of the sudo and admin groups to avoid doing sudo for every command I want. I have recently came back from Windows, but I'm finding that this doesn't work any more for me.

I'm already a member of the admin group, but sudo didn't exist. I created it and joined it, but still being requested to sudo anytime I do anything. I know I'm missing something simple...!

I do beleive that what you want to do is edit the **sudoers** file:
```

man sudoers

```
will explain things for you....

---

### Post by glave on 2007-06-18
Mmmm, not really not be prompted for a password when doing a sudo, but not having to do sudo at all. That's more of the desired behavior I'm after.

---

### Post by cookies on 2007-06-18
> **glave said:**
> Mmmm, not really not be prompted for a password when doing a sudo, but not having to do sudo at all. That's more of the desired behavior I'm after.

Erm.... not gonna happen. The apps requiring sudo do it as a security feature, since they are usually doing things in sensitive system folders.

---

### Post by MKdx on 2007-06-18
I am not sure if this is what you want.
But there's something called Root Terminal in System Tools in the Main Applications menu.

You can add it if you don't have it, the command to start it:
```
gksu /usr/bin/x-terminal-emulator
```

---


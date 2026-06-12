---
title: "Password problems"
date: 2012-12-24
forum: General Help
---

### Post by phrauk777 on 2012-12-24
Hello,  I recently forgot my password to log in to my Gazelle professional laptop.  I opened the recovery menu after startup by holding the left shift to drop the root shell i typed passwd $$$, since my username is $$$.  however, i get a line back that says, "passwd: user '2665$' does not exist".  Is the fact that my username is a group of 3 symbols confusing the shell?

---

### Post by steeldriver on 2012-12-24
probably, yes - $$ has a special meaning in the shell (it is the shell PID)

you could try escaping it

```
$ echo $$$
3067$
$ echo \$\$\$
$$$

```I'd recommend changing to something alphanumeric though

---

### Post by phrauk777 on 2012-12-24
Thank you dearly for your response.  Using your commands didn't change anything though.  $$$ still appears to be read as 2665$

---

### Post by steeldriver on 2012-12-24
Hmm.. are you sure your actual username (not just the display name) is set to $$$? I'm kind of surprised the system would let you do that

If escapes don't work, you could try single quotes '$$$'

---

### Post by phrauk777 on 2012-12-24
I've tried past usernames to no avail

---


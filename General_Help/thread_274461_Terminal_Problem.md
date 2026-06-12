---
title: "Terminal Problem"
date: 2006-10-09
forum: General Help
---

### Post by ricanelite on 2006-10-09
I'm having a problem, I'm trying to download Java Version 5 and when I open up my Terminal and type su and try to enter my password it does not accept it, Now what can be the problem with that. Because I know I am entering it correctly. What can I do? Being that I'm new to Linux, what options do I have?

---

### Post by kidders on 2006-10-09
Hi there,

What do you mean by "does not accept it"? What message do you get?

Ordinarily, this problem arises (a) if you're not a member of a group that's allowed to sudo, or (b) if you're not typing your password correctly.

Since you've covered (b), I wonder if (a) is the answer. Are you in the "admin" group?

---

### Post by ricanelite on 2006-10-09
Sorry it says:

su: Authentication Failure
Sorry.

---

### Post by qamelian on 2006-10-09
> **ricanelite said:**
> Sorry it says:

su: Authentication Failure
Sorry.
Use sudo instead of su.

---

### Post by CatKiller on 2006-10-09
**su** will only work if you have a "proper" root password, seperate from your own. You should just use **sudo <command>** or, if you're really impatient, **sudo -i**.

---

### Post by ricanelite on 2006-10-09
okay when I type in 'sudo' i get a bunch of usage, What I'm trying to do is install 

jre-1_5_0_06-linux-i586-rpm.bin

Could you help me out?

---

### Post by mcduck on 2006-10-10
you don't use sudo on it's own, but instead you put it in the beginning of commands that need root privileges. Like in 'sudo apt-get update' :)

---


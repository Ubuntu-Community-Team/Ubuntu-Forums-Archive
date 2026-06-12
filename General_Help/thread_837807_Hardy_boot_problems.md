---
title: "Hardy boot problems"
date: 2008-06-22
forum: General Help
---

### Post by carl99fan on 2008-06-22
I just Installed 8.04 on an old unit 2 days ago.

Everything was going fine.

I was installing various different programs and such and had been all day.

I restarted the unit and now I am in the terminal or something.
Says something about Ubuntu has no warranty and says to visit help.ubuntu.com

I have restarted 3 times now and I keep getting the same thing.

Anything I can do?:confused:

---

### Post by macaholic on 2008-06-22
Are you prompted with a command line login? Does anything happen when you type Ctrl + Alt + F7? Are there any error messages that are visable?

---

### Post by carl99fan on 2008-06-22
> **macaholic said:**
> Are you prompted with a command line login? Does anything happen when you type Ctrl + Alt + F7? Are there any error messages that are visable?

no just like opening terminal 

name@name-desktop:~$

---

### Post by macaholic on 2008-06-22
What happens if you type and enter```
/etc/init.d/gdm start
```

---

### Post by carl99fan on 2008-06-22
> **macaholic said:**
> What happens if you type and enter```
/etc/init.d/gdm start
```

-bash: /ect/init.d/gdm: no such file or directory

---

### Post by carl99fan on 2008-06-22
This is bad huh!?:(

---

### Post by carl99fan on 2008-06-22
I can still apt-get 

strange

I can't start programs though
Says Error no display specified

---

### Post by carl99fan on 2008-06-22
When I first boot it up it looks just fine, the Ubuntu loading screen comes up in full color and then when the bar gets to teh end I get:

kinit: trying to resume from /dev/disk/by-uuid/100956bf-114-4e76-b949-453b8a46b545
Knit No resume image, doing normal boot...
Ubuntu 8.04 Name-desktop ttyl
name-desktop login

---

### Post by macaholic on 2008-06-22
Are you on gnome kde or xfce?

---

### Post by carl99fan on 2008-06-22
> **macaholic said:**
> Are you on gnome kde or xfce?

gnome

---

### Post by macaholic on 2008-06-22
What is the output of "dpkg -l | grep gdm"?

---

### Post by carl99fan on 2008-06-22
I think I am entering it wrong.

dpkg -l | grep gdm 
I get unknown option..

---

### Post by macaholic on 2008-06-22
I can't imagine what you could be mistyping, it's an 'L' after grep (not capital), and then the straight up line (shift backslash).

---

### Post by carl99fan on 2008-06-22
WOW I have tried it a lot and one time a got
Desired/unknown?install?config-unpacked/failed-cfg/half-inst/t-await?tT-pend? Err?=(none)?Hols?reinst-required?X=both Problems (Status, Err: uppercase=bad)
/Name: Version Description
pn gdm none (no description available)
II grep 2.5.3~dfsg-3   GNU grep, egrep and fgrep
NO packages found matching /.

but most of the comands I have tried I get command not found

---

### Post by carl99fan on 2008-06-22
OK...
I typed:
apt-get install gdm

Now I am having some type of java problem

I need jdk-6-doc.zip

should be owned by root.root and copied to /temp

I don't even know what that means! :(

I will hit "no"

---

### Post by macaholic on 2008-06-23
What do can you login now graphically? Because java should not have any effect on your ability to login.

---


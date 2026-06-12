---
title: "Parental Control (keylogger)"
date: 2007-05-21
forum: General Help
---

### Post by nami on 2007-05-21
Anyone know how to setup a keylogger on my system?  I want to make it clear to the younger members of my family that there is a keylogger on this computer so they should be careful of what they do.

Any suggestions on how to get a keylogger to work?

---

### Post by earobinson on 2007-05-21
searching synaptic finds this: > lkl
userspace keylogger for x86 architecture I like this one [http://www.thinkgeek.com/gadgets/security/7af2/](http://www.thinkgeek.com/gadgets/security/7af2/)

---

### Post by nami on 2007-05-21
Thanks

---

### Post by earobinson on 2007-05-21
np, also you can do as much as you like, but if your kids want to get around your security they will.

---

### Post by nami on 2007-05-21
Thats true unfortunately.

I seem to be having a problem with lkl

I typed the following to get it to work

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l

but its giving me an error

Segmentation fault (core dumped)

I am using a us_km keymaps file, but I have a uk keyboard.  it seems that a uk keymaps file does not exist in /usr/share/lkl/keymaps/

---

### Post by nami on 2007-05-21
It works even with us_km but I get the following error when I move the mouse

Segmentation fault (core dumped)

Any idea where I can get a uk keymaps file and why I get the segmentation fault error when I move the mouse?

---

### Post by Arisna on 2007-05-21
The keylogger is probably trying to interpret and log the input event of mouse movement.  Apparently it does not know how to do this.  Can you find any configuration where you can exclude certain input actions?  It would probably be a text file found under /etc.

---

### Post by nami on 2007-05-22
I can't seem to find the file.

---

### Post by Mika1860 on 2007-05-23
Hi nami,
I seem to have exactly the same problem.
So please contact me, when you solved it, would be great.
thanks,
Micha

---

### Post by LaRoza on 2007-05-23
If these younger members do not respect your rules, don't let them on-line. Any security measure can be by passed.

---

### Post by earobinson on 2007-05-23
> **Mika1860 said:**
> Hi nami,
I seem to have exactly the same problem.
So please contact me, when you solved it, would be great.
thanks,
MichaYou can always subscribe to this thread, even getting auto emails when new posts are made

> **LaRoza said:**
> If these younger members do not respect your rules, don't let them on-line. Any security measure can be by passed.I don't think thats quite the solution, yes all security can be bypassed epically with physical access to the machine, but there is nothing wrong with making it a bit harder for his children to access inappropriate content.

Back to topic I know a lot of ISP's will provide a nanny lock for you on the ISP side, that way you dont have to worry about your box. Try contacting your ISP see what they say.

---

### Post by nami on 2007-05-31
ok question, how does the us_keymap file work?  i would like to make my own uk_keymap file.  I don't have a usa keyboard so I can't compare the keyboard with the us_keymap file.

---

### Post by lix on 2007-12-12
...any security measure can be by passed......if they want to get around security they will.....

Security & internet filter methods are age-dependent. Generally speaking, the average 8-9 year old boy isn't going to be as "computer savvy" as a 17-18 year old boy. One has raging hormones & the other doesn't.  
 
What's the point of having something that's designed to be bypassed?
Bsafe on Windows OS is a better hedge against wee ones bypassing internet filters.

---

### Post by nami on 2007-12-19
how is that possible?

how can you stop a process if you have no rights on the computer you are using?

i.e the keylogger process

---

### Post by lswest on 2007-12-19
you can pretty easily change having permissions or not, and (well this is me, a 16 year old computer-addicted kid) most keyloggers can be disabled by either disabling it before boot, or gaining access to the file, and getting a password for the admin account, changing accounts and disabling it, etc.  generally just block "inappropriate" content in your router's firewall. less work & not as easy to reverse.

---

### Post by waspinator on 2008-04-16
> **lswest said:**
> you can pretty easily change having permissions or not, and (well this is me, a 16 year old computer-addicted kid) most keyloggers can be disabled by either disabling it before boot, or gaining access to the file, and getting a password for the admin account, changing accounts and disabling it, etc.  generally just block "inappropriate" content in your router's firewall. less work & not as easy to reverse.

Most kids talk sh*t like this, but when it comes down to it, as secured system is very difficult to break into.
("getting a password for the admin account"  ? - come on ... )

---

### Post by wobbiebobbie on 2008-04-16
do like i do when I go to work and my daughter is grounded I just take my DSL modem to work with me. No modem no internet (THE END)

---

### Post by nami on 2008-04-25
Not always practical if you have 2 kids and only 1 of them is grounded...

---


---
title: "How to boot directly to console?"
date: 2008-05-29
forum: General Help
---

### Post by vashwood on 2008-05-29
How do I boot directly into the console?  And if I ever want to get into GDM how would I get access to it?

Do I have to do anything special if I just wanted to use Putty from a windows machine to access the console?

Sorry, I was looking for a newbie section but I couldnt find one.:confused:

---

### Post by WRDN on 2008-05-29
The easiest way to access the terminal directly is to boot into recovery mode (unless you edited the file, it will be an option at the GRUB menu).

You could also boot in the graphical mode, click "Options" on the login screen, then select "Select Session". Finally, click "Failsafe Terminal".

---

### Post by vashwood on 2008-05-29
Anyway to do this w/ a headless computer?  I installed the server edition but I also added GDM so I can use the GUI every now and then.  I just want it to boot into the console directly each time.

---

### Post by WRDN on 2008-05-29
> **vashwood said:**
> Anyway to do this w/ a headless computer?  I installed the server edition but I also added GDM so I can use the GUI every now and then.  I just want it to boot into the console directly each time.

In that case, login at the GUI, select System > Administration > Services and uncheck the box next to the "Graphical login manager" service.

---

### Post by kaiju on 2008-05-29
how about completely removing gdm and using startx to, well, start x whenever you wanna get graphical?

---

### Post by mrowth on 2008-05-29
Totally related question: Would there be anything wrong with stopping rather than starting gdm at runlevel 2, and doing an init 3 when you want the GUI? I did that for a while to boot into console, it seemed quite unproblematic.

---

### Post by Oldsoldier2003 on 2008-05-29
> **mrowth said:**
> Totally related question: Would there be anything wrong with stopping rather than starting gdm at runlevel 2, and doing an init 3 when you want the GUI? I did that for a while to boot into console, it seemed quite unproblematic.

Theres nothing wrong with that- it is a very valid use of runlevels. As long as you make sure your change of runlevels doesn't interfere with important services I say carry on.

---

### Post by vashwood on 2008-05-29
Thanks.  I'll try out changing the init levels.  Will that speed up the booting time?

---

### Post by Artemis3 on 2008-05-29
> **vashwood said:**
> Do I have to do anything special if I just wanted to use Putty from a windows machine to access the console?

Yes, you need to install the package **openssh-server**.

---

### Post by vashwood on 2008-05-30
Quick question.  How do I start gdm at run level 2?

---

### Post by LaRoza on 2008-05-30
> **vashwood said:**
> How do I boot directly into the console?  And if I ever want to get into GDM how would I get access to it?

Do I have to do anything special if I just wanted to use Putty from a windows machine to access the console?

Sorry, I was looking for a newbie section but I couldnt find one.:confused:

You mean instead of a GUI? 

```

sudo mv /etc/init.d/gdm ~/gdm

```

This will cause gdm startup script to be in your home directory. It will not start with the computer, but you can manually start it. (Run it from the terminal, or type "startx")

You need openssh-server and your router enabled for port forwarding.

(This is the appropriate sections, but the "newbie" section is the Absolute Beginners Talk)

---


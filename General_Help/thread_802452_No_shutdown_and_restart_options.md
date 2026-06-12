---
title: "No shutdown and restart options"
date: 2008-05-21
forum: General Help
---

### Post by FFighter on 2008-05-21
Hello,

When I click the finish session icon in the upper-right corner of the screen I get a dialog with the following buttons/options:

 * Close Session
 * Block Screen
 * Switch User
 * Suspend
 * Hibernate

I wonder where Shutdown and Restart go ? They are not there. Does anyone know why ? 

If I want to restart or shutdown I need to do it from console...

---

### Post by N.N. on 2008-05-21
Go to "System" > "Administration" > "Login screen", click the "local" tab, and make sure that "Show action menu" is checked in the section called "Menu line".

I translated these titles from Danish, so they might vary from the exact wording of your install. Hope you get the gist of it, though.

EDIT: If my instructions aren't adequate, see the attached image.

---

### Post by ~E3016~ on 2008-05-24
> **FFighter said:**
> Hello,

When I click the finish session icon in the upper-right corner of the screen I get a dialog with the following buttons/options:

 * Close Session
 * Block Screen
 * Switch User
 * Suspend
 * Hibernate

I wonder where Shutdown and Restart go ? They are not there. Does anyone know why ? 

If I want to restart or shutdown I need to do it from console...

your problem is exactly mine too...

in the end, i force it by sudo shutdown -P 1 :(

but still i need the icon

---

### Post by Troll_the_Great on 2008-06-05
Open a terminal and run gdm from there.Use sudo gdm.I had the same problem and that fixed it.

---

### Post by cariboo on 2008-06-05
That really doesn't fix the problem, you're shutting it down as root. your problem is still there.

Jim

---


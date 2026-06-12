---
title: "Changing cursor speed always reverts back after reboot. (xset)"
date: 2013-08-15
forum: General Help
---

### Post by leafhound2 on 2013-08-15
I know how to change cursor speed

```
xset m 1 1
```

but it resets to default speed after rebooing, I wonder if we couls make a startup script where would we place this?

---

### Post by leafhound2 on 2013-08-15
Getting closer to the solution.

My apple mac has a perfect curor speed so ubuntu feels too fast and scitish

i am searching a start up script that runs a command

```
xset m 1 1
```

searching google is bringing me closer.

---

### Post by leafhound2 on 2013-08-16
It is too fast and skitish.

I made it more like my mac and slowed it down.

Open "Dash" (Alt + F2 and type startup apllications
Press "Add" and make you script with this command so it runs at startup
```
xset m 1 1
```

---

### Post by coffeecat on 2013-08-17
I've merged your cafe post into this thread as it was not a Cafe type post.

---

### Post by cessanfrancisco on 2013-11-22
Hey!  Thanks!  That really helped!

I'm pretty new to writing scripts, but I am assuming if I change the numbers in your script that will increase/decrease the cursor speed.  Correct?

---


---
title: "Ubuntu on Advent 9415 Laptop"
date: 2008-04-07
forum: General Help
---

### Post by g45uk2 on 2008-04-07
ok first of all im fairly new to Linux, i was given a copy of ubuntu by a tutor and was eager to get it going on my laptop, but when i tried to run it, it froze, after searching on the net for a fix without any luck i found the cure myself:
1) when you get to the boot screen press esc
2) enter the following: live generic.all_generic_ide=1 noapic acpi=off
3) press return/enter

it should now load.
hope this is helpful for people with model :)

---

### Post by Splendidmonkey on 2009-01-04
> **g45uk2 said:**
> ok first of all im fairly new to Linux, i was given a copy of ubuntu by a tutor and was eager to get it going on my laptop, but when i tried to run it, it froze, after searching on the net for a fix without any luck i found the cure myself:
1) when you get to the boot screen press esc
2) enter the following: live generic.all_generic_ide=1 noapic acpi=off
3) press return/enter

it should now load.
hope this is helpful for people with model :)

Hi there I'm trying to do a Vista / Linux dual boot have you had any luck with this as my install just froze after selecting install I tried adding the noapic acpi=off info to the install string and had no luck

---

### Post by mcrluver80 on 2009-02-01
> **g45uk2 said:**
> ok first of all im fairly new to Linux, i was given a copy of ubuntu by a tutor and was eager to get it going on my laptop, but when i tried to run it, it froze, after searching on the net for a fix without any luck i found the cure myself:
1) when you get to the boot screen press esc
2) enter the following: live generic.all_generic_ide=1 noapic acpi=off
3) press return/enter

it should now load.
hope this is helpful for people with model :)

1 question for you
im installing ubuntu 8.10 and i have a computer (custom built) that will load the cd and get to the loading screen loads that but then it returns to a black screen 
after that it seems like it powered down my dvd-rom and just kinda pause there forever but u can still type into that black screen
i was just wondering if u had any possible solutions and if maybe if "1) when you get to the boot screen press esc
2) enter the following: live generic.all_generic_ide=1 noapic acpi=off
3) press return/enter" that would work on a custom built desktop...

---


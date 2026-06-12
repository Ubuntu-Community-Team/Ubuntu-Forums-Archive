---
title: "Hibernate Issue"
date: 2007-06-03
forum: General Help
---

### Post by Snakiej on 2007-06-03
Hiya, 

I've got a ASUS M2N-e with a 8800GTS 320, and two gigs of RAM, running Ubuntu Feisty, kernel 2.6.21.3 (self compiled).

I run the latest nVidia drivers (self compiled), and beryl, and it all works like a charm :)

But, I don't have the hibernate button @ shutdown :( 

also opening a terminal, and enterting this:
```
snake@DESKTOP-SNAKE:~$ sudo hibernate
hibernate: No suitable suspend methods were found on your machine.
hibernate: You need to install a kernel with support for suspending to
hibernate: disk or RAM and reboot, then try again.

```

My full version is:
```

Linux DESKTOP-SNAKE 2.6.21.3 #1 SMP PREEMPT Sun May 27 16:42:50 CEST 2007 i686 GNU/Linux

```

**What did I tried myself:**
```
sudo killall beryl
```
But that does not solves the trick.



Anyone got a suggestion for me? :)

A box of :popcorn: for those who fixes my problem ;)

---

### Post by Snakiej on 2007-06-04
Bump ;)

You still get :popcorn: when you help me solve it ;)

---

### Post by Dylnuge on 2007-06-04
Do you have standby?

Are you using GNOME or KDE?

Pretty sure Hibernate is hideable on computers, and some computers hide it automaticly. Can't find info on Google, so I will need to wait till I get home to help you.

Also, do you have Hibernate as an option in Windows?

---

### Post by Snakiej on 2007-06-04
> **Dylnuge said:**
> Do you have standby?
 Nopz, no standby button
> 
Are you using GNOME or KDE?

I use Gnome :)
> 
Pretty sure Hibernate is hideable on computers, and some computers hide it automaticly. Can't find info on Google, so I will need to wait till I get home to help you.

Also, do you have Hibernate as an option in Windows?
Yea, hibernate works like a charm on Windows, suspend also works perfect.

---

### Post by Dylnuge on 2007-06-04
OK,

I know how to fix this on KDE, trying to figure it out for GNOME. In the meantime, go into System -> Preferences -> Power Management. Check if Suspend or Hibernate is on any of the drop down lists in there.

---

### Post by Snakiej on 2007-06-05
> **Dylnuge said:**
> OK,

I know how to fix this on KDE, trying to figure it out for GNOME. In the meantime, go into System -> Preferences -> Power Management. Check if Suspend or Hibernate is on any of the drop down lists in there.

Nope, only 'Ask me' and 'Shutdown' :(

---

### Post by Dylnuge on 2007-06-05
Odd. Looks like Standby is disabled, as is Hibernate. I am going to look into this.

---

### Post by Dylnuge on 2007-06-05
Ok, may have thought of something. Standby and hibernate are both ACPI components, meaning if ACPI is disabled, then standby could be too. The only way to check this is complicated, and requires that you follow these steps exactly:

1. Open the Terminal (Applications -> Accessories -> Terminal)
2. Enter "cd /usr/src/" without the quotes.
3. Enter "ls" without the quotes.
4. A list will come up. Names will begin with linux-headers and then have a bunch of numbers. For the next step, use the one with the highest number. If there is more then one with the same number, use the one with "-generic" or "-i386" next to it.
5. Enter "cd " followed by the directory you are using (see above).
6. Enter "make menuconfig" without the quotes.
7. You will now be in the kernel configuration menu. Navigate through these menus:
```
  Power Management Options
    [*]  Power Management support
      ACPI (Advanced Configuration and Power Interface) Support
        [*]  ACPI Support
```
8. See if ACPI support is enabled. If it is, see if Sleep States is enabled. If either of these are not enabled, **do not enable them** at this point.
9. Post the results here.

---

### Post by Snakiej on 2007-06-06
> **Dylnuge said:**
> Ok, may have thought of something. Standby and hibernate are both ACPI components, meaning if ACPI is disabled, then standby could be too. The only way to check this is complicated, and requires that you follow these steps exactly:

1. Open the Terminal (Applications -> Accessories -> Terminal)
2. Enter "cd /usr/src/" without the quotes.
3. Enter "ls" without the quotes.
4. A list will come up. Names will begin with linux-headers and then have a bunch of numbers. For the next step, use the one with the highest number. If there is more then one with the same number, use the one with "-generic" or "-i386" next to it.
5. Enter "cd " followed by the directory you are using (see above).
6. Enter "make menuconfig" without the quotes.
7. You will now be in the kernel configuration menu. Navigate through these menus:
```
  Power Management Options
    [*]  Power Management support
      ACPI (Advanced Configuration and Power Interface) Support
        [*]  ACPI Support
```
8. See if ACPI support is enabled. If it is, see if Sleep States is enabled. If either of these are not enabled, **do not enable them** at this point.
9. Post the results here.
First of all mate, I ain't a linux noob, so please, don't waste your time on 'without the quotes' text ;) But thanks anyway.

As I said, I recompile my kernel myself, but unfortunatly my /usr/src is empty, because it was quite big.
But I will, on the next update (2.6.21.4) look at this, and check that that they ARE enabled, and recompile my total kernel.

---

### Post by Snakiej on 2007-06-06
I just checked, and I noticed IDE ... something is off. And that was needed on modern systems to support the S3 stuff. Is that what I need?

---

### Post by Dylnuge on 2007-06-08
First off, sorry for the delayed response. And I am sorry for making usless comments like without the quotes, but commonly people who have never even seen the terminal assume that that is what is necessiary. Better to have a pro who needs to read a few extra words then a newbie who posts a hundred times asking where, what, and why the terminal is (by why, I mean such posts as "On Windows its not like this," to which my response is usually, "On Windows, if you had this problem, since you have no way of changing the OS, you would be screwed.").

I don't think it could hurt enabling and re-compiling. Good Luck :).

---

### Post by Snakiej on 2007-06-09
> **Dylnuge said:**
> First off, sorry for the delayed response. And I am sorry for making usless comments like without the quotes, but commonly people who have never even seen the terminal assume that that is what is necessiary. Better to have a pro who needs to read a few extra words then a newbie who posts a hundred times asking where, what, and why the terminal is (by why, I mean such posts as "On Windows its not like this," to which my response is usually, "On Windows, if you had this problem, since you have no way of changing the OS, you would be screwed.").

I don't think it could hurt enabling and re-compiling. Good Luck :).

Sorry for my delayed response too. I am going to recompile my kernel NOW :) and I'll get back to you :)

---

### Post by Snakiej on 2007-06-09
Ok, kernel is recompiled, 2.6.22.4 now.

Sleep states are off (thats what you wanted to know).
IDE suspend is on (or somethin' like that).

But still no hibernate options. When I log out, there is the option to hibernate in my loginwindow, but no luck, that does not work, I get a blinking cursor for 5 seconds, and then it it goes back to the loginwindow.

I guess the problem lies somewhere else. Maybe because I'm using SATA drivers? Or that I use Beryl? I don't know, the system works like a charm, fast as a ...

:(

---

### Post by Dylnuge on 2007-06-10
Ahh... sleep states are off? Turn them on and tyr recompiling (again :(). Good luck.

PS: I use SATA drives and Beryl, and I have sleep states regardless (although I never use them-).

---

### Post by Snakiej on 2007-06-10
Sleep states says it might potentially break my system, but I'll give it a shot.

Don't worry about me having AGAIN to recompile, I got enough time, and I appreciate ur help :)

---

### Post by Snakiej on 2007-06-10
Yea!!!!!!!

It works!!!!

Thanks m8 ;)

A box of :popcorn: for you ;)

---


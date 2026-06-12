---
title: "[SOLVED] Keyboard stopped working.  (KDE User)"
date: 2007-10-28
forum: General Help
---

### Post by ubuntu27 on 2007-10-28
Hello fellow Ubunteros!  (Ubuntu users) and Debian users if there is any.

My whole keyboard works except the NumberPad part. Where there are keys like 

"Num Lock,  \  *  -
7  8  9
                   +
4  5  6
1  2  3
0     .           Enter



Nome of those keys work anymore.  I been searching with google but couldn't find any answers so I am posting here :)


Maybe here is a clue.

There was two users. Me and my sisters, each with our own user account. For both of us the Number pad doesn't work.

Yesterday, I created a new account for my father [Because Windows became too slow that is unusable]. Oddly enough, in this new account, the keyboard does work. It works perfectly.

There must be a difference between my fathers new account and my user account. Not sure what.

Thank you in advance!

---

### Post by ubuntu27 on 2007-10-30
*BUMP*

I humbly request your help guys. I always use google to look for the answer to my problems and I only create a thread when I cannot find any answer.

I really need your help in this.  

Thank you very much.

---

### Post by hvbakel on 2007-10-30
Perhaps you could take a look at the keyboard layout in the kde control center (kcontrol) and see if there are any differences between the user accounts. Perhaps you could try to enable a keyboard layout here and see if it helps.

A more drastic approach would be to start with a fresh kde profile. Make a new folder in your home disk labeled 'backup' and execute the following command in a terminal:
> mv ~/.kde backup. After that, log out of kde and log in again. Note that you will loose all your custom configurations for kde programs, but you can always copy settings for individual from the old profile in the backup dir. Hope this helps.

---

### Post by ubuntu27 on 2007-11-04
> **hvbakel said:**
> Perhaps you could take a look at the keyboard layout in the kde control center (kcontrol) and see if there are any differences between the user accounts. Perhaps you could try to enable a keyboard layout here and see if it helps.

A more drastic approach would be to start with a fresh kde profile. Make a new folder in your home disk labeled 'backup' and execute the following command in a terminal:
. After that, log out of kde and log in again. Note that you will loose all your custom configurations for kde programs, but you can always copy settings for individual from the old profile in the backup dir. Hope this helps.

Thank you hvbakel. Yes, I took a look at Keyboard Layout and Keyboard in Peripherals.  Both seems to be configured the same way. 


Anyway, I was able to solve this by creating a new user, and moving all my personal files to this new user account and deleted the old one.  THe new one works quite nicely. 

HMm. I see that the original account created when installing the Operating System (which was my default, the one that I had problem with keyboard) has an UID of 1000, my sisters has UID of 1001, 
and my dad's which his keyboad works has UID of 500.


My new user account that I just created has an UID of 501


My dads has three digits, and mine has four digits.  

Hmm. No, i don't whink it had soemthing to do with it... could it be?

Well, time to put this thread as solved.

---


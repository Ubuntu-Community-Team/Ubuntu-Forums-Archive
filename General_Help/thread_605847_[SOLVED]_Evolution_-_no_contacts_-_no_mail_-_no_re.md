---
title: "[SOLVED] Evolution - no contacts - no mail - no replies - half the menu gone"
date: 2007-11-07
forum: General Help
---

### Post by _sluimers_ on 2007-11-07
Here's a screenshot of what's wrong...

[IMG]http://www.spelmakers.com/images/Screenshot.png[/IMG]

I updated Ubuntu from 7.04 to 7.10.

And now a lot of menu options dissappeared in evolution.
Plus I get to see this error message everytime I start it.
I'm confused, what happened here? :confused:

---

### Post by _sluimers_ on 2007-11-10
Weird, I did nothing.:confused:, but the problem solved itself the next day  :)

---

### Post by _sluimers_ on 2007-11-15
Okay, so it didn't. Evolution turns to normal when I try to send mail, using firefox.

[EDIT]

The cause seems to be not having libsnn3 installed. However, I cannot install libsnn3 without removing firefox :( 

[/EDIT]

---

### Post by erginemr on 2007-11-15
Hello,

Trivial maybe, but is still worth a try. 

1. Odds are that your settings may be screwed. You can try to copy your hidden ".evolution" folder in your home directory, and try to reopen evolution if this corrects the situation. In your home folder:
cp .evolution .evolution_bak

If it does not work, you can recover your settings (mails, addresses, etc.) easily with
mv .evolution_bak .evolution

2. Secondly, you may try uninstalling and reinstalling Evolution.

---

### Post by _sluimers_ on 2007-11-15
Thanks for the help, but I already solved it by installing libnss3 and then reinstalled firefox.

---


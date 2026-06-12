---
title: "Control key is stuck"
date: 2013-05-01
forum: General Help
---

### Post by _Martin_ on 2013-05-01
Hi,

since yesterday the control key on my notebook-keyboard is stuck. Using xev, I found out that it is the left control key that is causing the problem.
At the moment I disabled the key by applying ```
xmodmap -e "keycode 37 = NoSymbol"
```.
This problem appeared sporadically in the past and always quickly went away by pressing a few buttons or rebooting (I can't remember). So my feeling is that it is a software problem rather than with the key itself. I browsed through various threads where similar problems with the control key were discribed and some of them were a couple of years old but I found no solution.

This problem is extremely annoying. Does anyone have a solution?

I'm using the 32 bit version of Ubuntu 12.04.

---

### Post by dino99 on 2013-05-01
check that its not a physical key problem (in case you are used to eat/drink/... while continuing your pc stuff); maybe some reverse keyboard can help

---

### Post by _Martin_ on 2013-05-01
Thanks for the quick reply, dino.
I have seen some terribly sticky keyboards myself and can say that mine is really clean and I never spilled anything over it. The feeling of the troublesome button is not different from the others so it does not look or feel suspicious at all.
Is there any way to find out if it is physically stuck by using some tool that is somehow closer to the hardware?

---


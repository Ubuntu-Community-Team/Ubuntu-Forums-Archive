---
title: "Computer not shuting down."
date: 2006-12-08
forum: General Help
---

### Post by umanzor on 2006-12-08
Hi,

I have a problem with 6.10. My computer doesn't shut down or reboot automatically, I have to manually shut if off or press the reset button. Is there a way to fix this??

---

### Post by bodhi.zazen on 2006-12-08
> **umanzor said:**
> Hi,

I have a problem with 6.10. My computer doesn't shut down or reboot automatically, I have to manually shut if off or press the reset button. Is there a way to fix this??

what happens when in a terminal you type one of these:

shutdown:
sudo shutdown -h now

or

sudo init 0

Reboot:
sudo reboot

or

sudo init 6

---

### Post by umanzor on 2006-12-08
"sudo shutdown -h now"

It worked. Automatically turned my system off.

The problem is that when I shut down from the menu, it stops at the end (when the bar is empty), but the computer is still on and showing the Ubuntu logo. Same with rebooting.

How can I solve it?

---


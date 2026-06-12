---
title: "is &quot;sudo reboot&quot; &amp; &quot;sudo poweroff&quot; use different path at boot process???"
date: 2020-10-02
forum: General Help
---

### Post by mail2rst on 2020-10-02
Just genetic linux query for intel Celeron NUC. Everything works well on  ubantu server O/S. but when I gave the &#8220;sudo reboot&#8221; command system  shutdown & while restarting hang at motherboard display page &  stand there for unlimited time. While I give &#8220;sudo poweroff&#8221; command then  computer completely shut down & I have to press the button on actual  hardware to start NUC system & this process working well. So in the  end &#8220; sudo reboot&#8221; command not works & hang in middle way but &#8220;sudo poweroff&#8221; command works correctly. is these two commands use separate  paths at the time of rebooting? Is any body idea where I need to fine  tune something to make &#8220;sudo reboot&#8221; command  workable to me? screen shot as below:-

[https://ibb.co/v3DXpWt](https://ibb.co/v3DXpWt)

---

### Post by CelticWarrior on 2020-10-02
Welcome.

The problem actually has nothing to do with reboot but with the splash screen that in the current release has problems in some systems, and intermittently.

---

### Post by mail2rst on 2020-10-02
Thanks CelticWarrior, is any solution for this or i it will stay as it? is anything i can do from my side to overcome this problem?

---

### Post by CelticWarrior on 2020-10-02
You can try removing "quiet splash" in /etc/default/grub

---


---
title: "Ubuntu 14.04 - How do I get UK keyboard on boot-up"
date: 2014-05-03
forum: General Help
---

### Post by dagicouk on 2014-05-03
Hi all,

I'm relatively new to Unbuntu.

Having recently upgraded to version 14.04, my Ubuntu session defaults to US keyboard layout on boot-up (I'm running Ubuntu as a VM in Windows 8.1).

In my previous version of Ubuntu, the Keyboard Layout option in settings allowed me to change the default layout to UK. The Keyboard Layout settings appears to have disapperared in 14.04

I realise that I can change the layout manually by typing "setxkbmap gb" in Term, but I'd rather this was done automatically.

I've read that amending the file /etc/default/keyboard may resolve the problem, I've tried this but I can't save the file because I don't have permissions.

Any suggestions and help would be much appreciated.

Thank you.

David.

---

### Post by wallaroo on 2014-05-03
I believe the following will change the keyboard layout - it's just well hidden.

1. Select 'System Settings' -> 'Keyboard'
2. You should see tucked away at the bottom of the 'Typing' tab a link that says 'Text Entry', select it.
3. This should bring up the 'Input Sources', here you can add 'English (UK)' and remove 'English (US)' if you desire.

---

### Post by dagicouk on 2014-05-04
Thank you very much.

Your solution has worked.

As you say, it is well hidden and in my view is a backward step from how keyboard layouts were handled in version 12.

David.

---

### Post by m.ferenczi on 2014-06-28
Many thanks

---


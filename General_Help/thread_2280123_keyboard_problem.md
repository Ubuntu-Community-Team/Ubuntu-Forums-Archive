---
title: "keyboard problem"
date: 2015-05-28
forum: General Help
---

### Post by okkadiroglu on 2015-05-28
Hi,

When I installed Ubuntu many releases ago, I had Turkish Q keyboard. Then, I changed by keyboard to Turkish F keyboard and used it without any problems. When I upgraded to 15.04 the boot keyboard is still Turkish Q and after the login it changes to Turkish F keyboard. How can I change the keyboard for all the users. There must be a file that I can modify. 

Many thanks

---

### Post by grahammechanical on 2015-05-28
Ubuntu 15.04 puts a keyboard layout indicator in the top panel even if we only have one keyboard layout installed. There should also be a keyboard indicator at the login screen that should allow us to change keyboard layouts.

At the desktop we can click the keyboard indicator and select Text Entry Settings. The dialog will show a list of keyboard layouts. Drag the Turkish F keyboard layout to the top of the list. That may work.

If you have different users then I think that each user would have to set up their own selection of keyboard layouts as these changes from the default would be stored in each users /home folder.

I do not know what else to suggest.

Regards.

---

### Post by btindie on 2015-05-28
Try:
```
sudo dpkg-reconfigure keyboard-configuration
```
which should update /etc/default/keyboard and create a new /etc/console-setup/cached.kmap.gz

---

### Post by okkadiroglu on 2015-05-29
Thank you very much, it worked and now I do not have keyboard problem any more.

---

### Post by okkadiroglu on 2015-05-29
Thank you very much for your help. I could not find a keyboard indicator on my desktop. So, I used btindie solution and it worked.

---


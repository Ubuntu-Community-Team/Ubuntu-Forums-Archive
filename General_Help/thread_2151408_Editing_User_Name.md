---
title: "Editing User Name"
date: 2013-06-04
forum: General Help
---

### Post by Chris62 on 2013-06-04
Hi,

I have just installed the 64-bit version of Ubuntu on my computer and was distracted by something when I was filling in my name, at the beginning of the installation, and miss-spelled it. Although this is not really a problem, I was wondering if it is possible to edit my user name. Can anyone help, please?

---

### Post by MidnightGrey on 2013-06-04
Since you just installed ubuntu, the easiest would be to create a new user. You can do this under Settings > User Accounts, and then deleting the old user.
Be sure to backup any files in your HOME directory as that would be lost when you delete your old user.

---

### Post by steeldriver on 2013-06-04
If it's your actual login name (i.e. what gets displayed when you do 'whoami' in a terminal), you can use the usermod command to change it - but iirc it will not automatically change your home directory name, you would need to do that manually - look at the man page ('man usermod') for details and be careful

OTOH if you want to change the display name you can use the chfn command - that's simple as it has no side-effects afaik, you can even do that from the User Accounts GUI

---

### Post by Chris62 on 2013-06-05
Many thanks for your replies. Because it was a new, clean installation I took the easy route and followed MidnightGrey's suggestion. However, I have learnt three new commands - whoami, usermod and chfn - so thanks steeldriver

---


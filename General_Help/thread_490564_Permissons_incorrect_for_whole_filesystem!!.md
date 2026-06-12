---
title: "Permissons incorrect for whole filesystem!!"
date: 2007-07-02
forum: General Help
---

### Post by benbooth on 2007-07-02
Please don't ask why I've done this but I ran **chown -R root:root /**
I cannot login now as a user. Only root.
I tried to correct it but it's going wrong.

Someone please help me restore the permissions on my filesytem.

Regards.

---

### Post by reckless2k2 on 2007-07-02
i think the easiest way you're going to be able to login to your GUI would be do the following:

chown -R yourusername:yourusername /home/youruserhomefolder

---

### Post by benbooth on 2007-07-02
I tried that but it I get an X error and get desktop background but no Gnome!
Could there be permissions incorrect in /usr?

No idea how to set it correctly

---

### Post by reckless2k2 on 2007-07-02
yes. uummm...not really qualified to answer the best way. i would say you'd have to use chmod at least the /usr directory. someone else will chime in with the particulars. i don't want to mess you up worse. haha.

---

### Post by benbooth on 2007-07-02
Thanks.
I hope someone can help me out. Didn't mount /home to seperate partition. Could be a costly reinstall.

---

### Post by reckless2k2 on 2007-07-02
nah...it won't be hard to fix that if you need to reinstall. there's a bunch of info of how to handle that in these forums.

---

### Post by bodhi.zazen on 2007-07-02
As painful as it sounds I think you need to reinstall.

---


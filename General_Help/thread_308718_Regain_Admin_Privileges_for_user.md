---
title: "Regain Admin Privileges for user"
date: 2006-11-28
forum: General Help
---

### Post by acesabe on 2006-11-28
Just set my mum up with Ubuntu - she likes it, but in my efforts to prevent her from accidentally doing any damage (like when prompted for password when an admin app is launched) - i disabled admin capibillities for her account - seems now no user can do admin tasks (including myself) and there is no root login to enable me to sort this problem out. I guess the group 'users' now cannot do admin tasks. So how is this little problem sorted out?

---

### Post by taurus on 2006-11-28
Just add the you or whoever you want to run sudo back into groups adm & admin.  Boot to recovery mode from GRUB menu and at the prompt, run

```
addgroup adm,admin acesabe
(assuming acesabe is your login name...)
```

---

### Post by acesabe on 2006-11-28
OK - i'll have to manually edit grub as i hid the extra boot options - no biggie - thnx for that info.

What about enabling root - i remember doing it ages ago in one of my Ubuntu installs - whats the opinion of doing this in the Ubuntu community these days (i'm generally not a gnome/Ubuntu user so am out of touch a bit)

---

### Post by aysiu on 2006-11-28
Full instructions here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by acesabe on 2006-11-28
Thnx - i'm all for making computing easier (su/sudoor root)- thats what they are there for init! But was a bit surprised at how easy it was to 'lock myself out'- without any warning of the consequences of clicking those boxes would be!....no matter

---


---
title: "Ubuntu One asks for keyring password"
date: 2013-05-16
forum: General Help
---

### Post by garyzw on 2013-05-16
I am using 13.04 and Ubuntu One keeps asking for keyring password everytime I boot. Anyway to stop this?

---

### Post by mcduck on 2013-05-16
If you are using normal login, with your password, make sure the keyring password is set to same as your login password.

And if you are using automatic login, or login without password, set the keyring password to empty one. You'll loose the security benefits of the keyring, but on a password-free login that probably dosn't make much difference to you anyway.

---

### Post by garyzw on 2013-05-16
The password is the same and I use automatic login. How do I set the keyring password to empty one?

---

### Post by mcduck on 2013-05-17
Open the "Passwords and Keys" tool from the Dash menu, and then on the left side panel under "Passwords" header you should see a keyring called "Login". Right-click on it and select "Change Password".

---

### Post by garyzw on 2013-05-17
Thanks it works great!

---

### Post by chaiman on 2013-11-02
For those, like me, that didn't have the "left side panel" that mcduck mentioned, you can display it by clicking "By Keyring" in the "View" menu

---


---
title: "Disable Keyring Authentication?"
date: 2022-01-21
forum: General Help
---

### Post by Daveski17 on 2022-01-21
[ATTACH=CONFIG]289860[/ATTACH]

Hello, I have automatic login enabled (Ubuntu 20.04 LTS). When I open Firefox and most other applications I don’t need login keyring authentication. I ran the snap of the Opera browser for a while and that would open like Firefox without the need to type my password into a dialogue box.

[ATTACH=CONFIG]289861[/ATTACH]

However, when I open Brave or other browsers like Chrome I need to authenticate by typing my password into a pop-up. Is there a way to disable this pop-up?  Thanks.

---

### Post by vanadium on 2022-01-22
Set your Login keyring password to blank in "Passwords and Keys". Right-click the "Login" folder and select "Change Password" there. My guess is that Firefox nor Opera are using that mechanism, but Chrome and Chromium do.

---

### Post by Daveski17 on 2022-01-22
> **vanadium said:**
> Set your Login keyring password to blank in "Passwords and Keys". Right-click the "Login" folder and select "Change Password" there. My guess is that Firefox nor Opera are using that mechanism, but Chrome and Chromium do.

Thanks but I'm not sure this an be achieved in 20.04.

---

### Post by Daveski17 on 2022-01-22
> **vanadium said:**
> Set your Login keyring password to blank in "Passwords and Keys". Right-click the "Login" folder and select "Change Password" there. My guess is that Firefox nor Opera are using that mechanism, but Chrome and Chromium do.

Sorry, you were right. It works. :guitar:

---


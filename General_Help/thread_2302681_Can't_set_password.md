---
title: "Can't set password"
date: 2015-11-12
forum: General Help
---

### Post by mike-rosen on 2015-11-12
Hi guys, I recently took off my login password and now I try to set in back on and it doesn't work. It shows as if it worked but then when I go to the login screen it doesn't ask for a password. Can someone help me set it back? I really need it. Thx

---

### Post by Habitual on 2015-11-12
Did you reboot or merely logout?

---

### Post by mike-rosen on 2015-11-12
i did both, neither of them worked :(

---

### Post by steeldriver on 2015-11-12
Whether you are required to supply a password at the login screen is dependent on membership of the nopasswdlogin group, I think

Open a terminal (Ctrl-Alt-T) and type

```

getent group nopasswdlogin

```

If your username appears in the list, you should be able to remove it using

```

sudo gpasswd --delete *username *nopasswdlogin

```

---

### Post by mike-rosen on 2015-11-19
oh thx that was exactly what i needed actually

---


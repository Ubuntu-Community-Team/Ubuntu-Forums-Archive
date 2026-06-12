---
title: "SSH pre login message with RSA"
date: 2008-04-21
forum: General Help
---

### Post by txapelgorri on 2008-04-21
Hi there:

I'm trying to show a pre-login message to any user who tries to start a SSH session. I've read that I could achieve this by adding "Banner" directive to "sshd_config" file. It works fine for normal authentication (password), but I would like to do the same thing for key authentication (RSA). Any tip about this?.

Cheers, txapelgorri.

---

### Post by brian_p on 2008-04-21
> **txapelgorri said:**
> Hi there:

I'm trying to show a pre-login message to any user who tries to start a SSH session. I've read that I could achieve this by adding "Banner" directive to "sshd_config" file. It works fine for normal authentication (password), but I would like to do the same thing for key authentication (RSA). Any tip about this?.

Cheers, txapelgorri.

Works for me with the Banner option and suitable text in /etc/issue.net. The text displays first and the passphrase is then asked for.

---

### Post by txapelgorri on 2008-04-21
Thanks brian_p!

I didn't gave all the information...I use seahorse on client side and the pop up window that claims you for the password doesn't get noticed about the message. If I omit that window, then yes, you are completely right, it works like a charm. Maybe a seahorse issue, right?.

Cheers, txapelgorri

---

### Post by brian_p on 2008-04-21
> **txapelgorri said:**
> Thanks brian_p!

I didn't gave all the information...I use seahorse on client side and the pop up window that claims you for the password doesn't get noticed about the message. If I omit that window, then yes, you are completely right, it works like a charm. Maybe a seahorse issue, right?.

Cheers, txapelgorri

I do not use seahorse but I think you are correct - it is the issue here.

---

### Post by txapelgorri on 2008-04-22
Hi Brian:

It seems so. I'm going to do a little research on this and I'll post results here. I hope doing it soon ;)

---


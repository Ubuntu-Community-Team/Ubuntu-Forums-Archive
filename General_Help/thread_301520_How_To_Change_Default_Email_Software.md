---
title: "How To Change Default Email Software"
date: 2006-11-17
forum: General Help
---

### Post by JustDon on 2006-11-17
I am running 6.06 LTS and have downloaded and installed Mozilla Thunderbird as my email software, how can I change the default to Thunderbird so that when I click on a "send email" link or click "send mail" from the "Tools" tab of Firefox - Thunderbird comes up instead of Evolution?

---

### Post by mitch.c on 2006-11-17
> **JustDon said:**
> I am running 6.06 LTS and have downloaded and installed Mozilla Thunderbird as my email software, how can I change the default to Thunderbird so that when I click on a "send email" link or click "send mail" from the "Tools" tab of Firefox - Thunderbird comes up instead of Evolution?
In Gnome, try System -> Preferences -> Preferred Applications.

You might also need to add the following to user.js in your Firefox profile:
```
user_pref("network.protocol-handler.app.mailto", "/usr/bin/mozilla-thunderbird");
```

---

### Post by JustDon on 2006-11-17
> **mitch.c said:**
> In Gnome, try System -> Preferences -> Preferred Applications.

Thanks - Perfect! Worked like a charm.:)

---

### Post by galleonway on 2006-12-02
KDE> **mitch.c said:**
> In Gnome, try System -> Preferences -> Preferred Applications.

You might also need to add the following to user.js in your Firefox profile:
```
user_pref("network.protocol-handler.app.mailto", "/usr/bin/mozilla-thunderbird");
```

How would I do this using KDE? I.ve tried changing Default Applications using System Settings with no effect. Programs still look for Kmail even though I uninstalled it. Kmail won't connect to my SMTP server and Thunderbird w3ill.

---


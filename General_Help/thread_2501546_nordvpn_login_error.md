---
title: "nordvpn login error"
date: 2024-10-12
forum: General Help
---

### Post by rhman91 on 2024-10-12
Hi, whenever i type ( nordvpn login ) this error pup up 

> Post "https://api.nordvpn.com/v1/users/oauth/login?challenge=d0db4ee3ff1ad99ca19c8a86d59a66c4ee133b432ea1fcf91f46c8f6e4652d00&preferred_flow=login&redirect_flow=default": net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers).


any help.

---

### Post by Rubi1200 on 2024-10-13
Try restarting the nordvpn service as well as updating it if needs be.

Contacting their customer support might also be a good idea.

---

### Post by rhman91 on 2024-10-14
i have done it already but still nothing have changed . btw i did  contact .em their AI answered me back. with nonsense sentences....................

---

### Post by Rubi1200 on 2024-10-14
Have you tried uninstalling and reinstalling?

---

### Post by rhman91 on 2024-10-20
tried everything dude . i use nordvpn on firfox its better working now .

---

### Post by 1fallen on 2024-10-20
Nord has kind of lost it's way lately. :(

Did you ever try
```

nordvpn login --legacy
## Or
nordvpn login --username username --password password
```
I don't know what you mean or did when you say "tried everything dude"

EDIT: There's a better way and it supports MFA, which you should have anyway.

After you do the normal login on the browser after following the link on the CLI after doing nordvpn login, cancel out of the "Open with" popup, and copy the link that is assigned to the "Continue" link, under the message saying "You've successfully logged in" (should be a nordvpn:// link).

Then do nordvpn login --callback "nordvpn://link" and it should log you in.

NordVPN should document this on the callback page, place the callback URL in visible text, with a copy button, etc... like most other OAuth workflows.

---


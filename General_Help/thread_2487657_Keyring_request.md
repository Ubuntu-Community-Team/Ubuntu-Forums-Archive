---
title: "Keyring request"
date: 2023-06-11
forum: General Help
---

### Post by grey1beard on 2023-06-11
Is there a way to identify which program asking for a keyring to be opened ?
A pop-up keeps appearing asking for it after I leave the computer inactive for a short time, perhaps 10 minutes or so.

---

### Post by #&amp;thj^% on 2023-06-11
First make sure that your account has auto-login feature off. Auto-login may cause this.
 
If not check:
```
journalctl -b | grep keyring

```
Then find anything related with:
```

sudo lsof -n | grep keyring
```

---


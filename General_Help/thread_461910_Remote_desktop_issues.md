---
title: "Remote desktop issues"
date: 2007-06-02
forum: General Help
---

### Post by griffithc on 2007-06-02
I have a couple of quick questions about the standard remote desktop client. First, how do I get music /sounds to play on the computer accessing the Ubuntu host, rather than the host? Secondly, can I change the port 5900 to something else? Many thanks.

---

### Post by Ek0nomik on 2007-06-04
Open a terminal and type:

```
gconf-editor
```

Navigate to:  /desktop/gnome/remote_access

Find:  keys alternative_port and use_alternative_port

---


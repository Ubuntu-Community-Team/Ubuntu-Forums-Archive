---
title: "Pulseaudio not starting automatically?"
date: 2014-12-19
forum: General Help
---

### Post by Furbybrain on 2014-12-19
Hi

SInce I upgraded to Unicorn I have had to manually start Pulseaudio every time I boot up with "pulseaudio --start". I did a clean install on my Dell Inspiron laptop, any idea what could be the problem?

Thanks

UPDATE: Solution is to change /home/furby/.pulse/client.conf to say

```
autospawn = yes
```

---

### Post by Yellow Pasque on 2014-12-19
Sometimes, it helps to delete the user's old pulse configuration, which forces a fresh one to be generated:
```
rm -rf ~/.config/pulse*
pulseaudio -k
```

---


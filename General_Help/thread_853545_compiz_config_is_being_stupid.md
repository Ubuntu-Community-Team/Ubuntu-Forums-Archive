---
title: "compiz config is being stupid"
date: 2008-07-08
forum: General Help
---

### Post by munkyinvasion on 2008-07-08
OK, so every time i boot, all my compiz settings reset. Annoying, so i reset all of them and they get all choppy because in Appearance, the visual settings has gone down to normal. So i switch it up to Extra. Now all my settings are reset again. How can i fix this? I read another thread about making the defaults.ini file un-writable, but i dont know how to change permissions.

---

### Post by overdrank on 2008-07-08
> **munkyinvasion said:**
> OK, so every time i boot, all my compiz settings reset. Annoying, so i reset all of them and they get all choppy because in Appearance, the visual settings has gone down to normal. So i switch it up to Extra. Now all my settings are reset again. How can i fix this? I read another thread about making the defaults.ini file un-writable, but i dont know how to change permissions.

HI and could you give us some specs on the system?

---

### Post by sayakb on 2008-07-09
Open CCSM and click **Preferences** and click **Reset to Defaults** button. Then again set up customized settings of youre own.
If you don't have CCSM:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Saint Angeles on 2008-07-09
once CCSM is configured, close it and then restart compiz and see if it kept your settings.

---


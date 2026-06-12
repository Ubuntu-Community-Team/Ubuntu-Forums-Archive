---
title: "How to bind key to switch between windows"
date: 2015-01-27
forum: General Help
---

### Post by CkDGTAT on 2015-01-27
Hi,

I used the following syntax in ~/.screenrc

```
bindkey "^k" focus up
```

But cannot make it work.

Can you please help?

---

### Post by TheFu on 2015-01-27
The setting is controlled by the Window Manager, so find that resource file and add it there with the binding you want.
For openbox, it is:
```
  <keybind key="A-Tab">
      <action name="NextWindow"/>
   </keybind>
    <keybind key="A-S-Tab">
      <action name="PreviousWindow"/>
    </keybind>
```

in the rc file passed into the openbox startup process. Here's the process:
openbox --config-file /export/home/thefu/.config/openbox/rc.xml

---

### Post by HermanAB on 2015-01-27
Do try Autokey also.

---


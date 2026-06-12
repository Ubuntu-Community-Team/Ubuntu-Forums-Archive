---
title: "Mozilla Question??"
date: 2008-01-11
forum: General Help
---

### Post by ameba on 2008-01-11
How do i stop mozilla from disclosing the type of OS i'm using????

---

### Post by p_quarles on 2008-01-11
Type this in the address bar:
```
about:config
```
In the "filter" bar, type "user." 

Now, change any string that refers to your OS to a blank entry.

---

### Post by ameba on 2008-01-11
that's Awesome!!!!!

Thank u

---

### Post by ameba on 2008-01-11
HMMMMM??   

Any Suggestions????

---

### Post by p_quarles on 2008-01-11
I guess it's probably stored in Chrome somewhere. Anyway, this works: install the User Agent Switcher extension:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Restart Firefox so it takes effect. Now, go to "Tools" >> "User Agent Switcher" >> "Options" >> "User Agents." Click on "View Default," and delete the line about the OS, or change it to something else.

---


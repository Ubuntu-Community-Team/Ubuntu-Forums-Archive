---
title: "Evolution mail refuses to open links in chromium-browser"
date: 2018-01-22
forum: General Help
---

### Post by Stefan_Grnberg on 2018-01-22
I just installed latest Kubuntu.
I have been googling around trying all kinds of commands.
all points to chromium as default browser, and yet, evolution refuses to open links with chromium and it pops up firefox instead.

I have checked default application and set chromium there.
have changed mime types with gio to be set at chromium, i have done update alternatives and set chromium as default.
Have rebooted, and yet evolution opens links in firefox.

WHERE do evolution get firefox!?

---

### Post by Stefan_Grnberg on 2018-01-23
Nobody knows how to fix this brokeness in Evolution mail?

---

### Post by howefield on 2018-01-23
Are you able to run and provide the output for the following command ?

```
gio mime x-scheme-handler/http
```

---

### Post by Stefan_Grnberg on 2018-01-23
```
:~$ gio mime x-scheme-handler/http
Default application for &#8220;x-scheme-handler/http&#8221;: firefox.desktop
Registered applications:
        chromium-browser.desktop
        firefox.desktop
Recommended applications:
        chromium-browser.desktop
        firefox.desktop

:~$ gio mime x-scheme-handler/https
Default application for &#8220;x-scheme-handler/https&#8221;: firefox.desktop
Registered applications:
        chromium-browser.desktop
        firefox.desktop
Recommended applications:
        chromium-browser.desktop
        firefox.desktop


```

Seems like changing to chromium didnt "stick" i see now it says firefox.

---

### Post by howefield on 2018-01-23
Does..
```
gio mime x-scheme-handler/http chromium-browser.desktop
```

help ?

---

### Post by Stefan_Grnberg on 2018-01-23
Yes it helped, thank you.
I did the same for /https too, and restarted evolution mail, and now it works as i want.

---

### Post by howefield on 2018-01-23
> **Stefan_Grnberg said:**
> Yes it helped, thank you...

Cool, glad to hear it and thanks for marking the thread as solved.

---


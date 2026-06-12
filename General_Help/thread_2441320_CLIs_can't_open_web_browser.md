---
title: "CLIs can't open web browser"
date: 2020-04-22
forum: General Help
---

### Post by Daniel_Rosehill on 2020-04-22
Hi folks,

I've been having this problem for the past year probably but it's now come to a head as it's preventing me from installing google-drive-ocamlfuse.

Whenever a CLI attempts to open a browser tab I get an error message and it appears as if my home directory is being automatically prefixed to the URL &#8212; so the command fails.

E.g. when I run google-drive-ocamlfuse in a terminal the program should open by default web browser (Chrome) and bring me to the login screen.

Instead I get:

[https://i.imgur.com/wlT9fkR.png](https://i.imgur.com/wlT9fkR.png)

> /home/myuser/https:/accounts.google.com/o/oauth2/auth?client_id=111111111111111.apps.googleusercontent.com&redirect_uri=https%3A%2F%2Fgd-ocaml-auth.appspot.com%2Foauth2callback&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fdrive&response_type=code&access_type=offline&approval_prompt=force&state=454545454545454545454: No such file or directory

Does anybody know what might be causing this and what I need to change for CLIs to be able to open links again?

**ETA:**The bug appears to be LXDE-specific. After logging out and using GNOME xde-open [https://www.url.com](https://www.url.com) works as expected and opens the link in my default browser (Chrome).

**ETA 2: **As this seems to be an LXDE-specific bug I've opened a thread in the DEs forum (didn't realize I couldn't delete the original!).

---

### Post by ActionParsnip on 2020-04-22
Does this work OK
[https://vitux.com/how-to-access-your-google-drive-account-in-ubuntu](https://vitux.com/how-to-access-your-google-drive-account-in-ubuntu)

---

### Post by Daniel_Rosehill on 2020-04-22
> **ActionParsnip said:**
> Does this work OK
[https://vitux.com/how-to-access-your-google-drive-account-in-ubuntu](https://vitux.com/how-to-access-your-google-drive-account-in-ubuntu)

I was able to get google-drive-ocamlfuse working just by logging under GNOME and following the setup procedure.An easy workaround but not ideal. So this is an LXDE specific bug. But it does have quite far reaching implications: I can't open links from Discord, Zoom, Slack, among others without manually copying and pasting into a browser.

---


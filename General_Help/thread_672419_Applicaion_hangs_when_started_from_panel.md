---
title: "Applicaion hangs when started from panel"
date: 2008-01-19
forum: General Help
---

### Post by johann_p on 2008-01-19
This is extremely odd: I have a script that stars [this Java application]("http://www.geocities.com/ramix_info/passwordmanager.html")

```

#!/bin/bash
cd <where_app_is_installed>
java -jar passwordmanager.jar 

```
When I start this script from a terminal, everything works OK.
When I start the same script from an application launcher in the panel, the starting window of the app is shown but locks up. 

Is there any sensible explanation for this? :confused:

---

### Post by skulda on 2008-01-19
Have you tried 'run in terminal' in the settings of the application launcher?

---

### Post by johann_p on 2008-01-19
> **skulda said:**
> Have you tried 'run in terminal' in the settings of the application launcher?

Yes, that does not change anything and the app still hangs. The terminal does not show anything either. I can terminate the app by pressing Ctrl-C within that terminal (without a terminal I have to click the close icon of the window, wait for the "application does not respond" message and then choose terminate)

---


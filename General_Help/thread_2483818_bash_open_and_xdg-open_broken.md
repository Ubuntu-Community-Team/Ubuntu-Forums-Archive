---
title: "bash open and xdg-open broken?"
date: 2023-02-09
forum: General Help
---

### Post by lrPrentice on 2023-02-09
I'm striving to open a URL from a bash script:

#!/bin/bash

open [https://ubuntuforums.org/](https://ubuntuforums.org/)

But when executed, the script displays cruft:

$ Gtk-Message: 12:34:33.855: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

Since my shell script is called by other scripts, the cruft breaks the flow.

I'm running Firefox on Ubuntu 22.04.1

Extensive Google search tells me that this problem has been around for several years. But search as I may, I have not been able to find a fix.

Can it be fixed? 

If so, how can I fix it or do a runaround?

Many thanks,

LRP

---

### Post by philhughes on 2023-02-09
Workaround - redirect the error message:

```
xdg-open "https://ubuntuforums.org/" 2> /dev/null
```

---

### Post by Holger_Gehrke on 2023-02-09
On my XUbuntu 22.04 xdg-open is a shell script. So unless your xdg-open  is different, the GTK-Warning you're getting can't be printed by  xdg-open itself but by a program called by xdg-open. Might be Firefox  itself since that does use GTK.

If I do an 'xdg-open [https://ubuntuforums.org/](https://ubuntuforums.org/)' while ff is already running I don't get any messages. If I do it when ff is not running I get 'ATTENTION: default value of option mesa_glthread overridden by environment.' repeated four times. Unless you're doing something with the error output of xdg-open you could just send it to /dev/null with '2>/dev/null'.

Holger

---

### Post by #&amp;thj^% on 2023-02-09
> **lrPrentice said:**
> I'm striving to open a URL from a bash script:

#!/bin/bash

open [https://ubuntuforums.org/](https://ubuntuforums.org/)

But when executed, the script displays cruft:

$ Gtk-Message: 12:34:33.855: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.


I'm not sure this will fix yours but a similar annoyance crept up on my end a year or so ago, check if these are installed:
```
>> apt policy libatk-adaptor:i386 libgail-common:i386
libatk-adaptor:i386:
  Installed: (none)
  Candidate: 2.46.0-5
  Version table:
     2.46.0-5 500
        500 http://archive.ubuntu.com/ubuntu devel/main i386 Packages
libgail-common:i386:
  Installed: (none)
  Candidate: 2.24.33-2ubuntu2
  Version table:
     2.24.33-2ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu devel/main i386 Packages


me on Thu Feb 09 at 02:24 PM in ~ branch: (HEAD) 
>> apt policy libatk-adaptor libgail-common
libatk-adaptor:
  Installed: (none)
  Candidate: 2.46.0-5
  Version table:
     2.46.0-5 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
libgail-common:
  Installed: 2.24.33-2ubuntu2
  Candidate: 2.24.33-2ubuntu2
  Version table:
 *** 2.24.33-2ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status



``` 
But I find the same out come as Holger_Gehrke with those commands.

---

### Post by lrPrentice on 2023-02-09
Thanks to all for responses&#8212;philhughes, your solution did the trick!

LRP

---

### Post by MAFoElffen on 2023-02-10
> **lrPrentice said:**
> I'm striving to open a URL from a bash script:

#!/bin/bash

open [https://ubuntuforums.org/](https://ubuntuforums.org/)

But when executed...

I'm running Firefox on Ubuntu 22.04.1

The above code would be for MAC OSx...

For Linux. shouldn't it be
```

#!/bin/bash

# Direct start specific browser with url
firefox https://www.ubuntuforums.org

# Use the default configured browser
xdg-open https://www.ubunuforums.org

# Cross platform
python3 -m webbrowser http:/www.ubuntu.org

```

---


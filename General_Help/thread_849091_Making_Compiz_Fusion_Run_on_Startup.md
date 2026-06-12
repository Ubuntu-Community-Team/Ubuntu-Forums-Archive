---
title: "Making Compiz Fusion Run on Startup"
date: 2008-07-04
forum: General Help
---

### Post by TheSeb on 2008-07-04
What is the "Command" I need to put in @ Sessions. I can't figure it out, and the solutions I find w/ google don't work :(

---

### Post by iaculallad on 2008-07-04
Go to System->Preferences->Session.

Under "Startup Program" tab, Click on the "Add Button"

Name: **Compiz Startup**
Command: **compiz --replace -c emerald &**

and click on OK.

---

### Post by TheSeb on 2008-07-04
> **iaculallad said:**
> Go to System->Preferences->Session.

Under "Startup Program" tab, Click on the "Add Button"

Name: **Compiz Startup**
Command: **compiz --replace -c emerald &**

and click on OK.

Didn't work, any other ideas?

---

### Post by iaculallad on 2008-07-04
Let's try to place it in script:

Create the compiz_start.sh file in /usr/local/bin directory:

```
gksudo gedit /usr/local/bin/compiz_start.sh
```

Code should be:

```
    #!/bin/bash
    #
    # Start compiz-fusion with compiz --replace
    #

    sleep 15
    compiz --replace -c emerald &
```

Save and close file.

Change the file permission:

```
sudo chmod a+x /usr/local/bin/compiz_start.sh
```

And add the compiz_start.sh script to startup: Navigate to System->Preferences->Session,
Create new startup, and point the command to /usr/local/bin/compiz_start.sh

EDIT: Try to logout then log back in..

---

### Post by TheSeb on 2008-07-04
yay, this method worked. Only problem (or maybe not much of a problem) is that although compiz works the blue icon that shows up in the top right corner (next to tomboy) is no longer there. That is, I have to turn on compiz manualy for it to appear.

Is that a problem? it doesn't really bother me that it isn't there visually.

---


---
title: "Auto-runing Commands at Startup?"
date: 2008-05-04
forum: General Help
---

### Post by MasterNetra on 2008-05-04
Is it possible to have Kubuntu 8.04 run a series of custom terminal based commands at the start of a user's session? With a lack of other Touchpad configuration controls I am stuck using only synclient commands which only last for the session they are used in. So how would I go about setting it up to where it will automatically run it for me?  (ex. "synclient MaxTapTime=0")

---

### Post by Zorael on 2008-05-04
Sure, make a script with the commands you want to run, make it executable and place it in ~/.kde/Autostart/.

```
#!/bin/bash

synclient MaxTapTime=0
```
```
$ chmod +x ~/.kde/Autostart/*filename-of-script*
```

---

### Post by MasterNetra on 2008-05-04
Ok... So how do i go about creating the script? I never made one before.

---

### Post by foosean010 on 2008-05-04
You can create a new text document in the folder mentioned above, ~/.kde/Autostart.  Enter the information in the code box and save the file with a .sh extension.  Then run the command listed above, but I hade to use "chmod +x /home/**username**/~/.kde/Autostart/**nameoffile.sh**"

That should get it working for ya.

---

### Post by ghost_ryder35 on 2008-05-04
my fav script
```

#!/bin/bash
top

```
love that little guy :)

---

### Post by MasterNetra on 2008-05-04
> **ghost_ryder35 said:**
> my fav script
```

#!/bin/bash
top

```
love that little guy :)
What exactly is #!/bin/bash doing and how do you use it?

---

### Post by ghost_ryder35 on 2008-05-04
> **MasterNetra said:**
> What exactly is #!/bin/bash doing and how do you use it?
it is a shebang (cant spell)
it tells the script where something is located, in this example it is locating the bash (your terminal).  If you were going to do perl or something it might look like
#!/usr/bin/perl

---

### Post by ghost_ryder35 on 2008-05-04
check this out for a very clear explanation
[http://en.wikipedia.org/wiki/Shebang_(Unix)#Example_shebang_lines](http://en.wikipedia.org/wiki/Shebang_(Unix)#Example_shebang_lines)

---

### Post by MasterNetra on 2008-05-04
> **foosean010 said:**
> You can create a new text document in the folder mentioned above, ~/.kde/Autostart.  Enter the information in the code box and save the file with a .sh extension.  Then run the command listed above, but I hade to use "chmod +x /home/**username**/~/.kde/Autostart/**nameoffile.sh**"

That should get it working for ya.

It worked! Ty :) minus the ~/ in the chmod part but yea :p

---

### Post by Zorael on 2008-05-04
Yes, **~** is the same as **/home/*<username>***, so assuming that your username is joe, **~/Desktop** is the same as **/home/joe/Desktop**. :>

---

### Post by MasterNetra on 2008-05-04
Yea... It confused me at first. :)

---


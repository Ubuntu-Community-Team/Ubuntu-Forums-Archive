---
title: "Can somebody explain me how to make a script with terminal instructions."
date: 2017-02-15
forum: General Help
---

### Post by bask185 on 2017-02-15
I have a panel PC who's touchscreen needs to be started and calibrated every time after a reboot. I need to have a script which performs certain terminal commands. At this point I am not yet interested in how to start this script automatically after a reboot. I have read similar topics about it and I have read about bashscripting, but non of these explain in clear detail what I actually have to do.

I also have a program which I want to start upon a reboot. To start the program I need to open the CLI and type  $"processing-3.3/processing". And this one line launches the program 'processing'. But now I want a shell script which does exactly that. And I want that shellscript to be an executable so I can click on it. <- this is no problem, already fixed. So I want to double click on a certain shell file which then performs CLI commands for me.

So right now I have a shellscript called Init.sh and in it there is:

#!/bin/bash

/processing-3.3/processing

But this does not do anything. What exactly must I do in order to get this to work?

---

### Post by The Cog on 2017-02-15
> To start the program I need to open the CLI and type $"processing-3.3/processing"
This is probably happening in your home directory. use the command **pwd** to print which directory this is. Assuming it is /home/bask185 then the full path to the processing app is /home/bask185/processing-3.3/processing. Your script should either contain the command **processing-3.3/processing** in which case it will only work if launched by a process that is already in /home/bask185, or it should be **/home/bask185/processing-3.3/processing** which should run from anywhere provided the user has rights to see and run things in that user's directory.

In brief, I think your problem is the leading / in your existing script.

---

### Post by iamjiwjr on 2017-02-15
[https://www.maketecheasier.com/beginners-guide-scripting-linux/](https://www.maketecheasier.com/beginners-guide-scripting-linux/)

---

### Post by bask185 on 2017-02-15
Thank you for you reply. I changed the text to:
#1/bin/bash

/home/user/processing-3.3/processing

But there is still noting happening. Must I add something more to the .sh?

EDIT. I now can launch processing if I open the .sh via the command line. But even tough I made it an executable I still cannot open processing by clicking on the .sh. And this has to be a program which starts automatically. Regardless I think I can take the next step to try let it run opon reboot.

---

### Post by Keith_Helms on 2017-02-15
> **bask185 said:**
> Thank you for you reply. I changed the text to:
#1/bin/bash

/home/user/processing-3.3/processing

But there is still noting happening. Must I add something more to the .sh?

That should be an exclamation point, not a 1:
```
#!/bin/bash
```

---

### Post by bask185 on 2017-02-15
yeah I know I mis-typed it here on the forum ;)

---

### Post by The Cog on 2017-02-16
I don't think it is normal to launch an executable simply by double-clicking it.

To make the script run at boot, I would probably add it to the end of /etc/rc.local, which is a file that's there for doing just that.

---

### Post by Keith_Helms on 2017-02-16
> **The Cog said:**
> I don't think it is normal to launch an executable simply by double-clicking it.

To make the script run at boot, I would probably add it to the end of /etc/rc.local, which is a file that's there for doing just that.

It all depends on what needs to be running for the script to work.  For example, I tried putting a command to disable power management for my wifi in rc.local and it turned out to run too early.  I ended up putting the script in the system crontab AND had to add a sleep 20 to it.
```
@reboot /etc/pm/power.d/wireless 
```

If the script requires xwindows to be running, it may need to be executed at login and not boot and you may have to put it somewhere like "session and startup" in Xubuntu or whatever the Ubuntu equivalent is named.  That's where my script to configure my touchpad goes.

---


---
title: "Force Quit launcher"
date: 2007-08-02
forum: General Help
---

### Post by Optimaximal on 2007-08-02
How do I go about creating a Force Quit launcher?

Basically, i'd like to insert Force Kill into Applications underneath Add/Remove Programs and it won't let me add it like you add apps to Panels.

I'm new to this lark and i'm probably missing the blatantly obvious, so all help is appreciated.  I don't know where the Force Quit app is hidden.

---

### Post by Incense on 2007-08-02
If you right click on one of you panels, click Add to Panel. From the window that opens you will find the "killall" launcher that you can add to your panel. If you have your deault icon set it will look like a broken window. Once you add it to your panel, you just need to click on it, your cursor changes to a skull I think, and you click on the program window you want to kill. 

Hope that helps. :)

---

### Post by Optimaximal on 2007-08-02
Thanks for the reply, but this isn't what I want.  I can easily add it to the Top Panel, but I wish to add it to the Applications Menu.  This involves creating a Launcher and I don't know where the Force Quit executable is or how its called.

---

### Post by lynxus on 2007-08-02
i think its just called xkill

using teh command xkill in a terminal gives me the skull. So maybe just tell the launcher to run "xkill"

---

### Post by strabes on 2007-08-02
Just make a launcher with command "xkill"

I just use the key combination Win+X. The only applications I really ever have to kill are firefox and amarok.

---

### Post by Optimaximal on 2007-08-02
I was under the impression Xkill just killed the Xsession, not the process.  

This still doesn't answer my question and I don't want a work-around...  Sorry if i'm sounding like a git, but can anyone tell me how Force Quit works?

---

### Post by nightcap79 on 2007-09-10
xkill works for sure to close any stack windows or programs.
right click on upper panel for example and choose Add New Item, from the windows choose Launcher, in the command type xkill. the name and description, you choose what do u want.
close the window.
then, when a window is stacked, click on the xkill launcher which we made before and select the stacked window, seconds the window is disappeared. if you selected the background picture, the session will be killed the same what happened with a friend.

---

### Post by oomingmak on 2007-12-25
> **Optimaximal said:**
> I was under the impression Xkill just killed the Xsession, not the process.  

This still doesn't answer my question and I don't want a work-around.
I'd like to know this too.

Xkill is not the same as Force Quit. I'd like to know what the terminal command is for **Force Quit** (which is also what the OP was asking).

---

### Post by lynxus on 2007-12-26
Xkill should kill the process aswel ( It has done for me )

Via a terminal:
Do a 
moo@moo# ps ax

once ya found process ID

do
mooo@moo#kill -9 PID

---

### Post by Islington on 2007-12-26
[http://ubuntuforums.org/showthread.php?t=21463](http://ubuntuforums.org/showthread.php?t=21463)

thread may prove useful

---

### Post by oomingmak on 2007-12-26
I can now see why Optimaximal just gave up on this thread.  ](*,)

Let me try again.

I already know about XKill (as does the OP), but we are [SIZE=3]_**not**_[/SIZE] asking about XKill, we're asking about how to invoke the the '**Force Quit**' panel applet from the command line.

As I said previously:

> **oomingmak said:**
> Xkill is not the same as Force Quit.


Any help is much appreciated. Thanks.

---

### Post by Islington on 2007-12-26
> **oomingmak said:**
> I can now see why Optimaximal just gave up on this thread.  ](*,)

Let me try again.

I already know about XKill (as does the OP), but we are [SIZE=3]_**not**_[/SIZE] asking about XKill, we're asking about how to invoke the the '**Force Quit**' panel applet from the command line.

As I said previously:




Any help is much appreciated. Thanks.

#-o
Honestly this problem has popped up several times, and I have never seen a solution..

also popped up here:[http://ubuntuforums.org/showthread.php?t=385981n&page=90](http://ubuntuforums.org/showthread.php?t=385981n&page=90)

from post #892 onwards

---


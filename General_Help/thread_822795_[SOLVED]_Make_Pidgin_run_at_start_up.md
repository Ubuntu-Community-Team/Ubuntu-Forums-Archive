---
title: "[SOLVED] Make Pidgin run at start up?"
date: 2008-06-08
forum: General Help
---

### Post by mparker81 on 2008-06-08
how do i make pidgin run at start up, and also while it is minimized and in the tool bar, i see the green status dot but there is a chat bubble behind it what does that mean?

---

### Post by forestpixie on 2008-06-08
Not sure of the bubble thing as I don't use it but to run a program at at start add it to your sessions/ styartup program list - in System > Preferences menu

---

### Post by mparker81 on 2008-06-08
yeah i tried that but i was sure what to type in the differant fields...

---

### Post by dje on 2008-06-08
Type anything you want in name and comment but in command just put:
```
pidgin
```

hope that helps,
dje

---

### Post by drs305 on 2008-06-08
> **mparker81 said:**
> yeah i tried that but i was sure what to type in the differant fields...

System, Preferences, Sessions, Startup Programs, Add:

name it what you want, I suggest: pidgin ;-)
pidgin
remarks.

---

### Post by ajgreeny on 2008-06-08
You may also want to install **pidgin-extprefs** to let you set pidgin starting as a system tray icon and not showing buddies list.  You will need to right click the sys-tray icon, select plugins and find extended preferences in the list, from where you can configure it as you want.

---

### Post by olaoni on 2008-08-18
> **ajgreeny said:**
> You may also want to install **pidgin-extprefs** to let you set pidgin starting as a system tray icon and not showing buddies list.  You will need to right click the sys-tray icon, select plugins and find extended preferences in the list, from where you can configure it as you want.
I just installed **pidgin-extprefs** as advised. When I click on the plugin I can see the Extended Preference dialog box. I then enable the check box with the title *Hide buddy list at startup* but when the system restarts the buddy list still shows. 
I am running ubuntu Hardy on a hp-tc1100 tablet.

Many thanks in advance.

Regards
Ola On

---

### Post by drs305 on 2008-08-18
> **olaoni said:**
> I just installed **pidgin-extprefs** as advised. When I click on the plugin I can see the Extended Preference dialog box. I then enable the check box with the title *Hide buddy list at startup* but when the system restarts the buddy list still shows. 
I am running ubuntu Hardy on a hp-tc1100 tablet.

Many thanks in advance.

Regards
Ola On

*Edit - Added: The following hasn't worked for some users. There is an alternate solution in post #12 with one user reporting on his computer he needed to increase the timeout to 20 seconds.*

When I started using pidgin I got the same results. I unticked all the options in that section EXCEPT the "Hide buddy list at startup" and then it hid the list on start up. If I had more than the one box ticked in that section, the Buddy window appeared.

---

### Post by olaoni on 2008-08-18
> **drs305 said:**
> When I started using pidgin I got the same results. I unticked all the options in that section EXCEPT the "Hide buddy list at startup" and then it hid the list on start up. If I had more than the one box ticked in that section, the Buddy window appeared.
Hi Drs305 thanks for the reply. However I still can't get the Pidgin dialog box to hide on startup. I unchecked all the check boxes as advised in your post but does not seem to make any difference.
Just for the record I am running version 2.4.1

Regards.

---

### Post by drs305 on 2008-08-18
> **olaoni said:**
> Just for the record I am running version 2.4.1
Regards.

2.4.3 is in the repositories and is what I'm running. It might make a difference. Synaptic shows i've installed pidgin, pidgin-data, pidgin-extprefs and pidgin-otr.

---

### Post by olaoni on 2008-08-19
> **drs305 said:**
> 2.4.3 is in the repositories and is what I'm running. It might make a difference. Synaptic shows i've installed pidgin, pidgin-data, pidgin-extprefs and pidgin-otr.
I downloaded and installed the latest version 2.4.3 of pidgin. But things are still the same. I have all the files mentioned above with the exception of pidgin-otr.
Reading the description from Synaptic Package Manager I am sure that this program should have nothing to do with the iconizing the buddy list window.

I am very new to Ubuntu\Linux. I can't recall what I did to make pidgin start up in the first place. All I know when I restart ubuntu both skype and pidgin starts up.

Skype gets iconize but pidgin doesn't.

What file is responsible for invoking pidgin after a system reboot.

Regards

---

### Post by drs305 on 2008-08-19
olaoni,

Here is a solution that will probably work for you. 

Create a script in a text editor and name it *something*.sh:
```

#!/bin/bash
sleep 10
/usr/bin/pidgin

```

Make the file exectuable:
```
chmod a+x *something*.sh

```
Add an entry to Sessions:
System, Preferences, Sessions > Startup Programs > +Add.
Name: Pidgin (or whatever)
Command: /path.to.script/*something*.sh

Pidgin should start with an icon in panel (if you have it set up that way) but without the Buddy List screen.

*(Credit to AncientPC for the example)*

---

### Post by olaoni on 2008-08-19
Thanks drs305 I finally got pidgin to start up iconized.
I had to modify the script as follows:-

#!/bin/bash
sleep 20
/usr/bin/pidgin

Once again Many thanks for your endless support.

Regards

---

### Post by Neffscape on 2008-09-28
> I just installed pidgin-extprefs as advised. When I click on the plugin I can see the Extended Preference dialog box. I then enable the check box with the title Hide buddy list at startup but when the system restarts the buddy list still shows. 

Same problem here, pidgin version 2.5.1 on Ubuntu Hardy Heron....

---

### Post by jerremy-tamlin on 2008-11-20
Just in case this helps anyone.

When I go to Tools->Plugins I get a big list of plugins
Close to the top is **Buddy List Options** 2.0.0
If I select this and configure it there is an option to "Hide Buddy List when it is created"

THIS DOESN'T WORK ON MY SYSTEM! It works when pidgin is started manually but not when it is started at startup.

--HOWEVER!!--

Further down the list of plugins is... **Extended Prefferences** 0.7 !!
This also has an option "Hide buddy list at startup"

Extended Prefferences sounds much more in keeping with the package everyone says needs to be installed, **pidgin-extprefs**

I'm betting that when I restart my computer pidgin will not show the buddy list.

---

### Post by jerremy-tamlin on 2008-11-20
Bummer! it diddn't work :(

I made a script like you suggested but that doesn't work either.:confused:

It's stupid that the plugin's don't work. It must be something about the way gnome starts things on startup.
Guess I'll just have to find out where/how that is configured.

---

### Post by jerremy-tamlin on 2008-11-21
Here's a new bit of info. At uni where the network connection is slower than pigion to startup, the buddy list starts hidden.

Also at home when I log out and log back in (without restarting my PC) the buddy list is already hidden.

I might mark this thread as unsolved because it isn't for me, and it makes more sense to have all the solutions in one place, than for me to start another thread.

Cheers


[I]Oh I guess I can't do that not being the one who started it. So I'll start a new thread and put a link to here.
The new follow on thread is [http://ubuntuforums.org/showthread.php?t=989722](http://ubuntuforums.org/showthread.php?t=989722)[/I]

---

### Post by The Real Dave on 2009-05-27
*bump* 

Thanks for the info, I couldn't quite find how to make it run at startup :)

---


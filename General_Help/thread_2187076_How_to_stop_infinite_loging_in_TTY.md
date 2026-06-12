---
title: "How to stop infinite loging in TTY"
date: 2013-11-10
forum: General Help
---

### Post by juditk on 2013-11-10
After startup and with Ctrl + Alt + F1 go to Terminal, the following message appears: 
usb 3-4: device not accepting address xxx error -71
The  message keeps repeating with different numbers, and is filling up the  screen and because of this I can't even type commands propperly because I  can't see what I'm typing. 


Before Unity froze and I coudn't start it up again, after multiple restarts, I am completeley unable to start anything. 

Any ideas : 
1. how to stop the log from being loaded, so I can type commands at least :( ? 
2. how to start Unity again? 

Thanks.

---

### Post by bapoumba on 2013-11-10
Looking around for that error, looks like a bad usb drive or connector.
When you say "after startup", what do you mean ? Do you boot from a hard drive or from usb ? Next question, why going to a tty to get a terminal ?

---

### Post by steeldriver on 2013-11-10
Have you tried a different tty? i.e. Ctrl-Alt-F2 / Ctrl-Alt-F3 / ... / Ctrl-Alt-F6

---

### Post by juditk on 2013-11-11
I found a solution in the meantime. 

By "after startup" I meant after booting from the hard disk and logging in. 
The guilty party was a usb hard disk that was connected at the time the laptop was booted. It didn't always happen, for ex. when a usb mouse was connected it didn't come up.

The combinations Ctrl+Alt etc. didn't help at the time, hence the post. 

"why going to a tty to get a terminal ?"
Because Unity froze before and I couldn't start the Terminal any other way.  
 To give in commands, because since unity froze the only way to give in commands was Ctrl+Alt+F1 and starting tty that way. 


The solution was, for future reference:
unity --reload, but I had to reinstall Unity first using:
 sudo apt-get install unity


 I also had to reset the Unity configuration. I found a link for that, but I didn't bookmark it sorry.  
 
When I disconnected all usb devices and did a reebot it was possible to do a normal start. 


 Luckily I had a Drawer app that allowed me to start Chromium and the terminal.
----------------------------------------------------------------------
I still don't know how to stop the infinite log, which is shown in the tty (Ctrl+Alt+F1-F5), so if someone knows why that happens and how to stop it, please let me know. 
It is annoying because I can't type any commands because I can't see what I'm typing.

---

### Post by bapoumba on 2013-11-11
Thanks for the info.
I'm not sure how to stop the logs on the fly as it seems to me that the kernel is unhappy with your usb HD. Good to see it does not happen with other usb devices, that means the connectors are fine.

Here is an old bug that still has recent input : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746)
There are some workarounds, sorry lots of reading :)

---


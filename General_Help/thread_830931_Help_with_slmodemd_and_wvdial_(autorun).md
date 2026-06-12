---
title: "Help with slmodemd and wvdial (autorun)"
date: 2008-06-16
forum: General Help
---

### Post by LeGollemux on 2008-06-16
I have slmodemd configured and it works, sees the modem etc. Wvdial works and dials out to my ISP. 

But in order for the above to work I need to manually run slmodemd and then wvdial. I have created launchers for them (in teminal).

I would like to know it there is a way to make slmodemd load automatically at startup, and run in the background.

any help is appreciated.

I am running ubuntu 8.04

---

### Post by rraj.be on 2008-06-16
You can make a small script and make it to be owned by you.


Then just place that in Syatem --> prefernces -->sesions.

You can add any such program to be started by default by adding it here.

---

### Post by LeGollemux on 2008-06-17
Thanks for the reply. totally makes sense.
One thing. any chance you can give me an example of how to do the script thing?

---

### Post by rraj.be on 2008-06-17
> **LeGollemux said:**
> Thanks for the reply. totally makes sense.
One thing. any chance you can give me an example of how to do the script thing?

A script is nothing but a collection of shell commands in a file saved with extension  .sh.


An example script

```
#!/bin/sh
 wvdial

```

```
#!/bin/sh
 wget -r -c www.someweb.com

```
you can find more details her.

Larazo have a great guide for the beginners.

```
[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")
```



Further than going to these scripting you can go with GUI like session window that i have quoted above.

Just in the start up tab of the session window click the ADD button at the right.

It will pop up you a window.

like asking for command name and then command and then prescription as given in thumbnail.

You can fill it to make a very simple startup script Click ok and now you have added a startup script to dial up internet through a modem.

Now each time when you boot up this command wvdial will be run.

like that you can add your custom startup commands

---


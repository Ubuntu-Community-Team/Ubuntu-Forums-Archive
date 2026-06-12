---
title: "[SOLVED] Java Error with vncviewer"
date: 2008-04-15
forum: General Help
---

### Post by renli on 2008-04-15
Hello.

I am running 7.10 on a desktop machine with remote desktop enabled.
I am trying to access it from a laptop running the 8.04 Beta.

I run vncviewer and after I enter in the password to access the desktop vncviewer crashes.  Here is the command and the output:

```
will@hermes:~$ vncviewer odin:0
odin 5900
RFB server supports protocol version 3.7
VNC authentication succeeded
sending client init
Desktop name is will@odin
Desktop size is 1280 x 1024
java.lang.IllegalStateException: Old input was not completely processed
   at java.util.zip.StreamManipulator.setInput (StreamManipulator.java:193)
   at java.util.zip.Inflater.setInput (Inflater.java:428)
   at vncCanvas.drawTightRect (vncCanvas.java:496)
   at vncCanvas.processNormalProtocol (vncCanvas.java:291)
   at vncviewer.run (vncviewer.java:145)
   at java.lang.Thread.run (Thread.java:710)
   at java.lang.VMThread.callRun (VMThread.java:124)
   at java.lang.Thread.callRun (Thread.java:398)
   at java.lang.VirtualMachine.runThread (VirtualMachine.java:137)
java.lang.IllegalStateException: Old input was not completely processed
will@hermes:~$ 
```

Before it crashes I get a small TightVNC window with a black screen and then it crashes after a few seconds.

Is this a problem with java itself I am having or a problem with vncviewer?  And how would I go about fixing it?

Thank you.

---

### Post by renli on 2008-04-21
Well, just to update my own question.  I sat down beside my desktop on which vncviewer worked and compared all installed packages that had anything what soever to do with java.  There were some packages containing java headers not installed on the Laptop that were installed on the desktop.  I installed those and now vncviewer is working.

---


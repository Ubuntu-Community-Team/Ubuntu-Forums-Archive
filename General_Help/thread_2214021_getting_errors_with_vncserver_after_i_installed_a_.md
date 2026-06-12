---
title: "getting errors with vncserver after i installed a new video card"
date: 2014-03-30
forum: General Help
---

### Post by skrite on 2014-03-30
hey there all. I recently installed an nvidia video card in that machine, and now x11vnc server does not work any more. when i try:```
x11vnc --usepw --forever --shared
```i get this:```
X11 MIT Shared Memory Attach failed:  Is your DISPLAY=localhost:11.0 on a remote machine?  Note:   DISPLAY=localhost:N suggests a SSH X11 redir to a remote machine.  Suggestion, use: x11vnc -display :0 ... for local display :0caught X11 error:29/03/2014 23:39:28 deleted 120 tile_row polling images.X Error of failed request:  BadAccess (attempt to access private resource denied)  Major opcode of failed request:  142 (MIT-SHM)  Minor opcode of failed request:  1 (X_ShmAttach)  Serial number of failed request:  50  Current serial number in output stream:  172
```any ideas?

---

### Post by steeldriver on 2014-03-30
Are you connected via ssh when you run this command? Are you adding -X or -Y to the ssh command line when you do so (or if you are using PuTTY from Windows, do you have the "Allow X forwarding" box checked?)

---

### Post by skrite on 2014-03-30
yes, using ssh and using the -X flag with the command. thanks.

---

### Post by steeldriver on 2014-03-30
So try it without the -X flag 

Or if you really need to forward individual X clients as well as relaying the whole desktop via VNC, you could try telling x11vnc to use the remote X server explicitly (i.e. overriding the ssh -X local DISPLAY variable)

```
x11vnc **-display :0 **--usepw --forever --shared
```

---

### Post by skrite on 2014-03-30
> **steeldriver said:**
> So try it without the -X flag Or if you really need to forward individual X clients as well as relaying the whole desktop via VNC, you could try telling x11vnc to use the remote X server explicitly (i.e. overriding the ssh -X local DISPLAY variable)```
x11vnc **-display :0 **--usepw --forever --shared
```dude, winner! that worked, thanks very much!

---


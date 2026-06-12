---
title: "[SOLVED] Trouble connecting from xp to Ubuntu via RealVNC"
date: 2008-01-25
forum: General Help
---

### Post by tbrminsanity on 2008-01-25
Ever since I put Compiz on my computer I have not been able to connect to it via RealVNC.  I still have access via OpenSSH but sometimes I like to view the desktop.  I usually connect with my WinXP (work) laptop over the internet.  My computer is set up for remote desktop and I didn't change any settings since I originally set up the remote desktop.  Any suggestions?

---

### Post by b0rka7a on 2008-01-25
Did you enabled the VNC server?
```
vino-preferences
```

---

### Post by tbrminsanity on 2008-01-25
Yeah they are setup properly.  When I try to connect via vncviewer it hangs on the following line:

 CConn:       connected to host ****.*****.***** port 5900

---

### Post by tbrminsanity on 2008-02-08
Ok now I can attempt to log into my computer but the authentication always fails.  This almost seems like a firewall problem.  Any ideas?

---

### Post by PinkFloyd102489 on 2008-02-08
You also need to tell it which display to use.

Example:

```

192.168.1.2**:0**

```

---

### Post by tbrminsanity on 2008-03-02
I got bigger problems now that my second computer is completely FUBAR.  I will have to try again when my second computer is fixed.

---

### Post by tbrminsanity on 2008-03-11
I've wiped Windows from my work computer so this is no longer a problem.

---


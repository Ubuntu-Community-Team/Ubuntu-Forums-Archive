---
title: "Echo to the Monitor from SSH"
date: 2008-01-26
forum: General Help
---

### Post by h0ax on 2008-01-26
Is there any way to connect to a box via SSH, then using some command have some output spit out on the monitor of the box you connected to?

We have just moved an old iMac into the kitchen and want to be able to post messages on the screen.

Opening the CD-rom, playing MP3s from ssh from afar are cool.

Anyone have any ideas?
Thanks in advance!

---

### Post by PinkFloyd102489 on 2008-01-26
Is this old iMac running Ubuntu?

---

### Post by Shootfast on 2008-01-26
Run a VNC server on the iMac and tunnel it through SSH?

---

### Post by PinkFloyd102489 on 2008-01-26
There's a way you can do it over SSH, provided that the program or command will auto break so that you gain control of the terminal back after executing the command.


```

export DISPLAY=:0 && /some/command/here

```



For example:
```

export DISPLAY-:0 && xmms /home/me/funkytune.mp3

```

That command will run XMMS on the GUI of the remote machine with the desired song.

---

### Post by h0ax on 2008-01-26
yes, the iMac is running Ubuntu 6.06 (:

---

### Post by nemilar on 2008-01-26
You could use the above recommendations; or you could keep a terminal open on the mac, and use either

```
echo "stuff" | wall 
```

or the

```
write
```

Command to write things to the person at the mac's console.

---


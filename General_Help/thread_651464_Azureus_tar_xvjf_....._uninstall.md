---
title: "Azureus tar xvjf ..... uninstall?"
date: 2007-12-27
forum: General Help
---

### Post by Kalidor on 2007-12-27
I just installed Azureus as described here: [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)

 I think i prefer deluge after all and want to uninstall it. How do i completely remove it?
Notice that no make install was involved in the procedure, so the checkinstall strategy is useless, as far as I can see. Thing is I can't see far... so I ask for your help.
I'm using Ubuntu 7.10 64 bit version.

---

### Post by taurus on 2007-12-27
You can remove the whole directory, azureus, where you installed it.  Then, you probably need to remove the ~/.azureus as well.

---

### Post by PinkFloyd102489 on 2007-12-27
tar xvjf would uncompress a tar.bz2 file, by the way.

---

### Post by Kalidor on 2007-12-27
> **taurus said:**
> You can remove the whole directory, azureus, where you installed it.  Then, you probably need to remove the ~/.azureus as well.

And where is that?

---

### Post by WearZeeP on 2007-12-27
```
whereis azureus
``` 
would probably (most likely) tell you that, if not, try 
```
locate azureus
```
and you would get all the files/folders containing the word "azureus".

---

### Post by taurus on 2007-12-27
> **Kalidor said:**
> And where is that?

Did you remember where you unpacked it?  How did you run azureus anyway?

---

### Post by Kalidor on 2007-12-27
I used the commands you suggested. Didn't find ~/.azureus

---

### Post by taurus on 2007-12-27
If you want to find ~/.azureus, look at the output of this command, especially near the top.

```
ls -la ~
```
So, you don't remember how you start the program.  Can you post the output of this then?

```
sudo find / -name azureus -print
```

---


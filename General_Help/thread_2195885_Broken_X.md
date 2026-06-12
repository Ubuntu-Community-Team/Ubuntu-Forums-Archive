---
title: "Broken X"
date: 2013-12-26
forum: General Help
---

### Post by jason13 on 2013-12-26
My desktop will only boot into CL here are the results of ```
sudo startx
``` ```
[COLOR=#000000][FONT=Ubuntu Mono]NVIDIA: API mismatch: the NVIDIA kernel module ahs version 304.88, but this NVIDIA driver component has version 304.108. Please make sure that the kernel module and all NVIDIA river components have the same version.[/FONT][/COLOR]
Fatal server error:
no screens found
(EE)
...

server terminated with error (1). Closing log file
... [COLOR=#000000][FONT=Ubuntu Mono]xinit: unable to connect to X server: No such file or directory[/FONT][/COLOR]
```
ellipsis are mine to eliminate unnecessary info. How should I continue diagnosing or repairing the system?

---

### Post by mikewhatever on 2013-12-27
You could try removing the Nvidia driver with jockey-text. Run **jockey-text --list** to show available drivers and their status, and **jockey-text --help** for more info.

---

### Post by travis-falkenberg on 2013-12-27
It may be that you have upgraded the NVidia driver on a kernel which does not support that version of the driver. I think you may have to completely purge the NVidia driver and reinstall nvidia-current.

Which version of Ubuntu are you running and which kernel? 

This link might help with repairing your installation. 

[http://askubuntu.com/questions/342664/nvidia-driver-updated-mixed-versions-of-304-88-and-319-32](http://askubuntu.com/questions/342664/nvidia-driver-updated-mixed-versions-of-304-88-and-319-32)

---

### Post by jason13 on 2013-12-28
> **travis-falkenberg said:**
> It may be that you have upgraded the NVidia driver on a kernel which does not support that version of the driver. I think you may have to completely purge the NVidia driver and reinstall nvidia-current.

Which version of Ubuntu are you running and which kernel? 

This link might help with repairing your installation. 

[http://askubuntu.com/questions/342664/nvidia-driver-updated-mixed-versions-of-304-88-and-319-32](http://askubuntu.com/questions/342664/nvidia-driver-updated-mixed-versions-of-304-88-and-319-32)

Thank you, seems to be working after the steps in the thread

edit: login screen comes up, can't log in, it just cycles back to the same screen

---

### Post by steeldriver on 2013-12-28
That's likely because you ran startx with SUDO, which has left a root-owned .Xauthority file in your home dir - this prevents your session from subsequently starting as a normal user. Log in via one of the non-GUI virtual terminals (Ctrl-Alt-F1 etc.) and remove the $HOME/.Xauthority file then return to the GUI login screen via Ctrl-Alt-F7 and try again.

---

### Post by jason13 on 2013-12-28
> **steeldriver said:**
> That's likely because you ran startx with SUDO, which has left a root-owned .Xauthority file in your home dir - this prevents your session from subsequently starting as a normal user. Log in via one of the non-GUI virtual terminals (Ctrl-Alt-F1 etc.) and remove the $HOME/.Xauthority file then return to the GUI login screen via Ctrl-Alt-F7 and try again.

Okay, when do I use ctrl-alt-F1? A little help with the right commands to remove the proper file would be appreciated.

---

### Post by steeldriver on 2013-12-28
Ctrl-Alt-F1 will switch you out of the screen where the GUI is running into a text-only 'virtual terminal' - you will be presented with a login prompt where you will need to enter your regular username and password (the password won't be echoed back - not even as asterisks)

Then you can check if ownership of either of the 2 files is a problem by typing

```
ls -l ~/.{ICE,X}authority
```

If you see something like

```
-rw------- 1 **root root**
```

then remove the file(s) e.g.

```
rm -f ~/.Xauthority
```

When you're done, you can type

```
exit
```

then use Ctrl-Alt-F7 to get back to the GUI, where you can try again to log in

---

### Post by jason13 on 2013-12-30
perfect, solved

---


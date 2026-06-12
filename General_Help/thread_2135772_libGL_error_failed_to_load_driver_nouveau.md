---
title: "libGL error: failed to load driver: nouveau"
date: 2013-04-15
forum: General Help
---

### Post by limurphy on 2013-04-15
[FONT=Arial]Dear Ubuntu/VESTA users,[/FONT][FONT=Arial]I just downloaded VESTA-x86_64 (a crystal visualization software) on my Ubuntu 12.10 64 bit machine. After extracted the files according 
to the manual, I ran "./VESTA", but resulted in the following error:[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]libGL error: failed to load driver: nouveau[/FONT]
[FONT=Arial]libGL error: Try again with LIBGL_DEBUG=verbose for more details.[/FONT]
[FONT=Arial]libGL error: failed to load driver: swrast[/FONT]
[FONT=Arial]libGL error: Try again with LIBGL_DEBUG=verbose for more details.[/FONT]
[FONT=Arial]The program 'VESTA' received an X Window System error.
[/FONT]
[FONT=Arial]...[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]And I just ran "LIBGL_DEBUG=verbose ./VESTA", then it came out:[/FONT]
[FONT=Arial]libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/nouveau_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so
libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/nouveau_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/nouveau_dri.so
libGL error: dlopen ${ORIGIN}/dri/nouveau_dri.so failed (${ORIGIN}/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/nouveau_dri.so
libGL: OpenDriver: trying /usr/lib/dri/nouveau_dri.so
libGL error: dlopen /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: nouveau_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: nouveau
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/swrast_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/swrast_dri.so
libGL error: dlopen ${ORIGIN}/dri/swrast_dri.so failed (${ORIGIN}/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
The program 'VESTA' received an X Window System error.
[/FONT]
[FONT=Arial]...[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]After a long time of googling, I know that this is something related to the library path, but still I do not know how to solve it.[/FONT]
[FONT=Arial]Does anyone know how the answer?[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thanks in advance,[/FONT]
[FONT=Arial]Murphy[/FONT]

---

### Post by efflandt on 2013-04-15
They should be there (I also have 32-bit libs for 32-bit Steam):
```
efflandt@XPS8100-1204:~$ locate nouveau_dri.so
/usr/lib/i386-linux-gnu/dri/nouveau_dri.so
/usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so
efflandt@XPS8100-1204:~$ locate swrast_dri.so
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
``` Oops thought it was 12.04. But see if **locate** can find those files on your system, or maybe there is an issue with the changed graphics in 12.10.

Are you using default nouveau driver or proprietary nvidia driver, and if latter, did you install from **Additional Drivers** or some other method?

---

### Post by limurphy on 2013-04-16
Thank you, efflandt!

My apology that it is actually 12.04 LTS in my desktop. 
And there are a lot of results from **locate ****nouveau**, but I only have nouveau_drv.so, which is located in
/usr/lib/xorg/modules/drivers/  
May I also ask what is the difference between nouveau_dri.so and nouveau_drv.so?
And no resultfrom** locate swrast****_dri.so**! Therefore I do not have this file...

By the way, I found that I can use VESTA in my laptop, which equipped with Intel graphic card. 

But my desktop is getting worse. This morning it can not enter graphical interface anymore!
At the beginning, it showed [COLOR=#ff0000]"could not write byte:broken pipe"[/COLOR]. 
Then after searchhig a bit in the threads, I did 
**sudo apt-get update**
[B]sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current-updates
sudo reboot
[/B]But it only replies me with a black screen. 
I am now using my laptop and do not know how to fix my desktop...

Urgent help needed, thank you all!

---

### Post by limurphy on 2013-04-16
By virtue of the following thread, I just removed comletely my Nvidia driver and re-install it again, then everything works now!
Even VESTA can be run on my desktop.[URL="http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely"]
http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely[/URL]

Thank you all for the replies and previous threads. Hopefully my experience can be a help to others as well.

---


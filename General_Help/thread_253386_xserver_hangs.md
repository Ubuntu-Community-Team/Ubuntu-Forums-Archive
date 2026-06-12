---
title: "xserver hangs"
date: 2006-09-08
forum: General Help
---

### Post by kosa on 2006-09-08
Hi,


My x-server hangs after some time (0,5 to 1 hour). I have no idea what is happening. There is no errors in /var/log/Xorg.0.log and only one warning: The directory "/usr/share/X11/fonts/cyrillic" does not exist (which I think is not important).

I run x-server on brand new GeForce 7600 GS. 

I have installed nvidia graphic drivers using Envy. 

I have no other problems with x-server.

I have ubuntu dapper with all fresh updates.

Could you suggest me what I should check?

---

### Post by Ocxic on 2006-09-08
check your screensaver and power managment options, maybe it's doing something thats is causeing problemes??

---

### Post by kosa on 2006-09-15
Hi, thanks for suggestions.

Inspired by [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) I found that it is AGP problem. Setting ```

Option "NvAGP" "0" 
``` in my xorg.cong solves the problem.

---


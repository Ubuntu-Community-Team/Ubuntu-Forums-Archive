---
title: "Log out script"
date: 2008-03-12
forum: General Help
---

### Post by StrikerZeroX on 2008-03-12
Hi everyone.

I have been searching for an answer for this for days. But have turned up nothing that actually works so here it goes.

I am using Ubuntu 7.10. I am trying to find the script or scripts that gets executed when you press the log out button in gnome. I tried /etc/rc.local but that only works when i shutdown the computer and I also tried /etc/init.d/rc.local. I got the same result.

I tested these files but put this into the script.
```
echo "script was run" > /home/rick/scripttest.log
```

So. If anyone knows what scripts get run when I press logout please let me know. I am at wits end here...

Thanks in advance.

---

### Post by koenn on 2008-03-12
This depends on how  you login.
I assume you're doing a GUI login. In that case it still depends on what desktop manager / desktop environment you use.
Assuming Ubuntu with gnome and gdm :

```
k@ix:~$ cd /etc/X11/gdm/
Init/        modules/     PostLogin/   PostSession/ PreSession/
```
You can put scripts in these directories, and they'll be executed at the corresponding moment. Eg in your case, I guess scripts in PostSession would probably work, but it also depends a bit on exactly what you want the script to do. 
The scripts run as root and know environment vars such as $USER.

---

### Post by StrikerZeroX on 2008-03-12
Thank you so much. 

The PostSession/ Directory worked.

I just edited the script that was named Default in that directory. Is it better to write a separate script, or does it not matter?

---

### Post by koenn on 2008-03-12
Cool.
Personally, In most cases  I'd keep a copy of Default for future reference / fallback, and then modify the original.

---

### Post by StrikerZeroX on 2008-03-12
Thats a good idea. I'll create a backup. Thanks again.

---


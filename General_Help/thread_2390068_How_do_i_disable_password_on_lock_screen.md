---
title: "How do i disable password on lock screen?"
date: 2018-04-25
forum: General Help
---

### Post by rudokf on 2018-04-25
Hi all,

I run Ubuntu 17.10 and, once computer is woken up from power-save (sleep) mode,I am getting lock screen with request for password.
I really want this disabled.

in Settings->Privacy, "Screen Lock" is off. Am I missing another setting somewhere?

Thanks,
Rudolf

---

### Post by DuckHook on 2018-04-25
AFAIK it is not possible to disable this "feature". However, you can bypass the password prompt simply by hitting the <Enter> key. I now simply hit that key to wake the screen and the lock overlay page is gone by the time the screen wakes.

---

### Post by kerry_s on 2018-04-25
run this command in terminal:
```

gsettings set org.gnome.desktop.lockdown disable-lock-screen true

```

---

### Post by DuckHook on 2018-04-26
> **kerry_s said:**
> run this command in terminal…
This command does not work on my install of vanilla Ubuntu Artful. I might be wrong, but my understanding is that the login screen overlay is now hard baked into the resume subsystem and cannot be disabled through gsettings.

---

### Post by kerry_s on 2018-04-26
so the changed it already.

install dconf-editor, click the search in the upper right, type "lock", your looking for "ubuntu lock screen" i think it was to be.

i'm on a different distro(solus) so i can't look up the exact command for you.

---

### Post by mc4man on 2018-04-26
You should be able to get away from a password, how depends on whether you have  a laptop or Desktop machine. 

For laptops there are 5 separate options & variations for ac or battery 
(- dim screen, time to dim screen, sleep-inactive timeout & type,  whether to lock on suspend & action on laptop close. 
Desktops probably get the 1st 3 above with no additional battery options.

All can be set to not go to a lockscreen/password.
(- though there were some reports that the use of nvidia drivers could interfere is some cases.

---

### Post by danthonyd on 2018-06-08
Disable screen lock after suspend by installing dconf-editor 
  ```
sudo apt install dconf-editor
```  
then navigate to **org/gnome/desktop/screensaver** and turn off **ubuntu-lock-on-suspend**.


[IMG]https://i.stack.imgur.com/P5c72.png[/IMG]

---


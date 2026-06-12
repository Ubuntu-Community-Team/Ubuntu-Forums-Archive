---
title: "permissions involving /usr/lib"
date: 2014-01-11
forum: General Help
---

### Post by ss8087 on 2014-01-11
I was messing around with VirtualBox and got some permissions error with something located in /usr/lib, and I mistakenly ran a chmod -R 777 on /usr/lib, which was a very bad idea. The first issue was wrecking /usr/lib/sudo/sudoers.so, where afterwards I no longer had access to sudo. I couldn't even shutdown or restart, so I had to hard shutdown with the power button. I wasn't able to get into recovery mode using shift (just breezes on by into the login screen), no matter whether I held shift or pressed it repeatedly. So I booted into ubuntu through liveusb and tried ubuntu without installing, then I mounted my root filesystem in the terminal and saw all of my files after using sudo chroot /mnt. I ran only two commands, which were: chown root:root /usr/lib/sudo/sudoers.so, and chmod 644 /usr/lib/sudo/sudoers.so, then rebooted. I have access to sudo again, and the permissions are -rw-r--r-- 1 root root for /usr/lib/sudo/sudoers.so only. 

Now onto the remaining problem, the rest of my /usr/lib folder is still fully open, and I think it is causing some other issues. My window graphics for certain programs look different (similar to a classic linux/windows layout for example), such as with firefox, chrome, compiz, nvidia settings, etc. Things in general are running a bit sluggish at times, along with some other strange problems. I get a few error boxes when I first login to my desktop, and I also noticed it doesn't show me as logged into my normal account even though I am. When I click shut down, it wants me to log out for example. It used to just shut down directly. I should be clear that I am on my user account however, and it shows in the terminal. 

Should I remove permissions on the entire /usr/lib directory just as I did with sudoers.so? I wasn't sure if that would be an equally bad idea, especially if it shouldn't be set to root only. I basically want to change back the initial cause of all of this, which was chmod -R 777 on /usr/lib.

Thanks

---

### Post by ss8087 on 2014-01-11
Small update, changed the permissions of sudoers.so, sudo_noexec.so, and sesh to -rwxr-xr-x instead of -[COLOR=#000000]rw-r--r--.
 
Edit- Set /usr/lib/ permissions to rwxr-xr-x with sudo chmod -R 755 /usr/lib/. I also had to set dbus to [/COLOR]-rwsr-xr-- 1 root messagebus, with the command sudo chmod 4754 /usr/lib/dbus-1.0/dbus-daemon-launch-helper. I have fixed almost everything I think, minus that some programs are still showing me the classic theme/layout window, such as my browsers or nvidia settings. Maybe a restart will fix it, not sure yet.

---

### Post by Impavidus on 2014-01-11
According to```
$ ls -Rl /lib | grep  "^d" | grep -v drwxr-xr-x
(no output)
```all directories in /lib have permissions set to 0755, at least on my system.

According to```
$ ls -Rl /lib | grep -ce -rw-r--r--
8461
```many files in /lib have permissions 0644, but according to```
$ ls -Rl /lib | grep -ce -rwxr-xr-x
73
```73 files on my system have permissions 0755. Giving more permissions than necessary usually doesn't break your system, although it can be a security problem and therefore a reason for sudo &co to refuse working. Apart from the 73 files with permissions 0755 (I may be able to give you a list from my system, but your system may differ), there are also 2 files with permissions 0640:```
$ ls -l /lib/ufw
totaal 28
-rwxr-xr-x 1 root root  1853 apr  5  2012 ufw-init
-rwxr-xr-x 1 root root 15409 apr  5  2012 ufw-init-functions
-rw-r----- 1 root root  1030 jun 11  2012 user6.rules
-rw-r----- 1 root root  1263 jun 11  2012 user.rules
```So, do you want to fix all of them or do you just want to reinstall? That's usually the quickest solution when people mess up ownership or permissions of system files.

---

### Post by ss8087 on 2014-01-11
> **Impavidus said:**
> According to```
$ ls -Rl /lib | grep  "^d" | grep -v drwxr-xr-x
(no output)
```all directories in /lib have permissions set to 0755, at least on my system.

According to```
$ ls -Rl /lib | grep -ce -rw-r--r--
8461
```many files in /lib have permissions 0644, but according to```
$ ls -Rl /lib | grep -ce -rwxr-xr-x
73
```73 files on my system have permissions 0755. Giving more permissions than necessary usually doesn't break your system, although it can be a security problem and therefore a reason for sudo &co to refuse working. Apart from the 73 files with permissions 0755 (I may be able to give you a list from my system, but your system may differ), there are also 2 files with permissions 0640:```
$ ls -l /lib/ufw
totaal 28
-rwxr-xr-x 1 root root  1853 apr  5  2012 ufw-init
-rwxr-xr-x 1 root root 15409 apr  5  2012 ufw-init-functions
-rw-r----- 1 root root  1030 jun 11  2012 user6.rules
-rw-r----- 1 root root  1263 jun 11  2012 user.rules
```So, do you want to fix all of them or do you just want to reinstall? That's usually the quickest solution when people mess up ownership or permissions of system files.

Thanks for your reply Impavidus, as of a restart every issue that I had is pretty much fixed. Also, were you referring to root /lib or /usr/lib? I only messed with permissions for the latter, though I am not sure if it may have affected any symlinks. There may be a few files I might have to adjust permissions with over time, but nothing I need right now it seems. This thread can be closed or removed, or left up to show others to be very careful with permissions when involving system directories. Common knowledge for many, I know.

---

### Post by Impavidus on 2014-01-12
Good catch, this was /lib. In /usr/lib the numbers are 0 directories with other permissions than 0755, 15324 files with permissions 0644 and 1071 files with other permissions. That's definitely too much to fix manually. If you want to fix it, reinstall. 9 files on my system in /usr/lib have either the setUID or setGID bit set, so these may give you trouble if not repaired. With excess permissions on some files your system may be less secure too.

Threads aren't deleted here (unless there is good reason to do so), but you may mark the thread as solved. Click Tread tools at the top of the screen.

---


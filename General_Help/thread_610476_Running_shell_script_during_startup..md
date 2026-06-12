---
title: "Running shell script during startup."
date: 2007-11-12
forum: General Help
---

### Post by amitabhishek on 2007-11-12
I want to run a shell script file automatically during start up.I am on Ubuntu 7.04. Where do I make changes?

---

### Post by avik on 2007-11-12
Go to System->Preferences->Sessions.  Add your script to the startup programs.

---

### Post by bingoUV on 2007-11-12
> **avik said:**
> Go to System->Preferences->Sessions.  Add your script to the startup programs.

Do this if you mean to run the script every time you log in.

If you want to make it run once during system startup, and not when you log out and log in again, call your script from /etc/rc.local. This is a file that is run during boot time after all requisite initialization is complete.

---

### Post by Jittoku on 2007-11-13
Is there a way to make a script run automatically when you shut down?

---

### Post by bingoUV on 2007-11-13
Read system shutdown and startup policy at 
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by amitabhishek on 2007-11-13
Thanks Guys. I want to run my broadband client (a bin file) using this script every time I login, this requires root level access. Do you think this also possible...

---

### Post by bingoUV on 2007-11-14
> **amitabhishek said:**
> Thanks Guys. I want to run my broadband client (a bin file) using this script every time I login, this requires root level access. Do you think this also possible...

It is possible. You will have to edit the sudoers file as root to give permission to your username(say amit) to run a particular script as root without giving password. In a terminal, run 
```

sudo visudo

```

This will open the sudoers file in vi editor, and it will let you edit it. It will stop you if you make inappropriate changes. Now, towards the bottom of the file you will find a line like
```

root    ALL=(ALL) ALL

```

Below this line, add the following lines (take cursor to this line and press 'o' key, then type the following)
```

Cmnd_Alias BROADBAND=<full path to your script>
amit ALL=NOPASSWD: BROADBAND

```

Exit the editor by <ESC>, :wq <ENTER>. If amit is not your real username, replace it. Now when you do 
```

sudo <full path to your script>

```
it will run as root but not ask for any password. Add this to your System->Preferences->Sessions.

---


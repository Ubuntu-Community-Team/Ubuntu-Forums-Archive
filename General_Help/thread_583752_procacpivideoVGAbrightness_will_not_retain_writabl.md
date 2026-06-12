---
title: "/proc/acpi/video/VGA/brightness will not retain writable permissions"
date: 2007-10-20
forum: General Help
---

### Post by lucidapparition on 2007-10-20
I have been trying to create a fix for the brightness keys on my laptop. I found that "echo (somevalue) > /proc/acpi/video/VGA/brightness" will set the lcd brightness on my laptop. At first this wouldn't work, because brightness permissions are set to 700 so I sudo chmod 777'ed the file. Then it worked, YAY! So, I whipped up a shell script that I call with my brightness keys to adjust the levels. So far so good.

But after a reboot the file is set back to 700. I believe this is because proc files are virtual files created by the kernel. So, how then would I retain the world writable permission?

---

### Post by DagMan on 2007-10-20
Yeah indeed, the files there aren't created until you turn on the machine.
you need to do it automatically either in a script in /etc/init.d or in the gnome startup in which case you need use sudo on startup but without it asking for a password
I do this by editing the sudo file to allow the execution of a script without a password.
To open that file for editing do this
```
sudo visudo
```
then using the example of a script that is in /usr/local/bin and not that you want to provide the full path and not just the name of the script or program, you would add the script to the file you just opened.
IF you want all users to have access without a password then it would look like this:
```
ALL ALL=NOPASSWD: /usr/local/bin/some-script-to-use
```
and if it was just for one user
```
username ALL=NOPASSWD: /usr/local/bin/some-script-to-use
```
Then hit ctrl-x hit y to save, hit enter and that's done.

The command will still have to be called with sudo, it just will execute without needing a password, so you can either have a script that changes file permission at boot, and put the full path to it in the thing above as shown or you can just make the script that echo's the value into the section of /proc you need ecexute with sudo and the command the script runs would be 
```
su root -c "echo value > /proc/place/to/put/the/value"
```

I never thought about changing the file permissions in /proc when doing this.  I wonder if works still after a suspend.  If not you could put it in the resume part. assuming you do it via file permission.

---

### Post by lucidapparition on 2007-10-21
Thank you for your help. I got it working now! 
8-)

---


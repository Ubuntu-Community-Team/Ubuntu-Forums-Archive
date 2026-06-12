---
title: "X wont start not usuall problem"
date: 2007-10-27
forum: General Help
---

### Post by jasonpeinko on 2007-10-27
So my computer was working fine last night, i turn it on this morning and i get an error saying that

 "could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. in the meantime this display will be disabled please restard gdm when the problem is corrected."

so i push ok

and i go to the root terminal i dont know how to fix so i restart and then i get a new error:

"Automatic file system cehck (fsck) of root.....
The root filesystem is currently mounted in read-only mode.
maintenance shell will now  be started.
fater maintenance, press CONTROL-D"
goes on to say that apt-get is not installed and i can fix it by typing apt-get install apt !?!?!

---

### Post by jasonpeinko on 2007-10-27
anyone?

---

### Post by dayvy on 2007-10-27
It would be helpful to post your Xorg.0.log file. 

tail -50 /var/log/Xorg.0.log

The above will display the last 50 lines in this file.

d.

---

### Post by jasonpeinko on 2007-10-27
is there a way to copy it to a flash drive? i have no idea how to do that from the command line. and i really  dont want to type that much.

---

### Post by dayvy on 2007-10-29
cat /var/log/Xorg.0.log > /media/name_of_flash_drive_mount/xorg.log

This will create a text file on your flash drive named xorg.log with the contents of Xorg.0.log. I'm assuming your flash drive is mounted already. You need to provide the right mount point for it in the above command.

d.

---

### Post by ukripper on 2007-10-29
This thread may help :
[http://ubuntuforums.org/showthread.php?t=591664](http://ubuntuforums.org/showthread.php?t=591664)

---

### Post by PmDematagoda on 2007-10-29
> The root filesystem is currently mounted in read-only mode.

This means that ownership/permissions is messed up on your system.

Try this:-
```

sudo chown root:yourgroup /
```

and

```

sudo chown yourusername:yourgroup /home/nameofyourhome
```

---


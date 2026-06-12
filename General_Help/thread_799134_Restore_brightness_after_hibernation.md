---
title: "Restore brightness after hibernation"
date: 2008-05-18
forum: General Help
---

### Post by piiotr on 2008-05-18
After I start from hibernation the brightness settings restore to there default values. I'm using the nvidia xserver.
In order to set them to the ones specified in the xserver I have to manually run nvidia-settings -l in the console. 

I tried adding a simple script to the /etc/acpi/restore.d:
#!/bin/bash
nvidia-settings -l

but this didn't have any effect.

Is there a way to fix that?

I'm using Ubuntu 7.1

---

### Post by piiotr on 2008-05-18
Ok I think I've got it fixed. I added nvidia-settings -l in the sessions>startup and changed it's order to 20.

Still don't know why that script didn't work though ..

---

### Post by sdennie on 2008-05-18
In Hardy, /etc/acpi/resume.d no longer works (it's even more confusing because /etc/acpi/ac.d and /etc/acpi/battery.d do still work).  The equivalent of /etc/acpi/resume.d in Hardy is /usr/lib/pm-utils/sleep.d.  However, that's a generic sleep/hibernate/resume directory and, if you script needs to know if it's resuming or going down (which, in your case, it won't matter), you have to do some special stuff to detect that (yes, it's suboptimal, no, I have no idea why pm-utils was included in Hardy).

---

### Post by sdennie on 2008-05-18
Actually, I just noticed that you were using Ubuntu 7.10 so you can ignore my rant about pm-utils.  The reason /etc/acpi/resume.d isn't working for you is because the script is being run as root and so nvidia-settings doesn't know which X display to use.  Something like this should work for you:

```

#!/bin/bash

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"

        su $user -c "nvidia-settings -l"
    fi
done

```

---


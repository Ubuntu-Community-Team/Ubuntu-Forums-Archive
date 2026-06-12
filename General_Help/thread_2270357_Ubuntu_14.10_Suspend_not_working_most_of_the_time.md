---
title: "Ubuntu 14.10 Suspend not working most of the time"
date: 2015-03-22
forum: General Help
---

### Post by austin30 on 2015-03-22
I installed 14.10 in my Toshiba click 2 pro.
Everything else seems just fine. But the suspend has some issues. It suspends fine one time after a reboot. But then on if I suspend it immediately comes back up. 
Because of my SSD space limitation and having 8 GB ram, I just gave only 2 GB swap partition. Is that a problem or is this a problem with Ubuntu? Please help. I badly need suspend but fairly new to Ubuntu to solve this problem on my own.

---

### Post by entropy1 on 2015-03-22
After reading post #19 in [http://ubuntuforums.org/showthread.php?t=1444822&page=2]("http://ubuntuforums.org/showthread.php?t=1444822&page=2") and creating the suggested file, in the file I changed _hcd to -pci everywhere, motivated by my observation that in /sys/bus/pci/drivers, there is no folder ehci_hcd, but only ehci-pci.  First
```
cd /etc/pm/sleep.d/
```
In this folder, create the file

20_custom-ehci-pci

with the contents:
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci-pci".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci-pci/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ehci-pci for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci-pci/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci-pci for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci-pci/bind
    done
    rm $TMPLIST
        ;;
esac
```
Make the file executable with
```
sudo chmod 755 20_custom-ehci-pci
```
Note that after creating this file, mouse movement no longer wakes from suspend.  You must use the power button.

---

### Post by austin30 on 2015-03-22
I tried with the -pci name and contents just as you gave. Didn't work.
Tried the _hcd and the chmod fails saying no such file even though the file and contents are just fine there. 
Any idea?

---

### Post by entropy1 on 2015-03-22
To show what you've done so far, post the output of the commands
```

cd /etc/pm/sleep.d
ls -l *
more 20_custom*

```

---

### Post by entropy1 on 2015-03-22
To show what you've done so far, post the output of the commands
```

cd /etc/pm/sleep.d
ls -l *
more 20_custom*

```

---

### Post by entropy1 on 2015-03-22
To show what you've done so far, post the output of the commands
```

cd /etc/pm/sleep.d
ls -l *
more 20_custom*

```

---

### Post by austin30 on 2015-03-22
here is it:
austin@Austin-Toshiba:~$ cd /etc/pm/sleep.d
austin@Austin-Toshiba:/etc/pm/sleep.d$ ls -l *
-rwxr-xr-x 1 root root  210 Oct 16 05:48 10_grub-common
-rwxr-xr-x 1 root root  660 Feb 25  2014 10_unattended-upgrades-hibernate
-rw-r--r-- 1 root root  663 Mar 22 22:01 20_custom_ehci_hcd
-rwxr-xr-x 1 root root  663 Mar 22 21:20 20_custom-ehci-pci
-rwxr-xr-x 1 root root 1260 May 22  2012 novatel_3g_suspend
austin@Austin-Toshiba:/etc/pm/sleep.d$ more 20_custom*
::::::::::::::
20_custom_ehci_hcd
::::::::::::::
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list


case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci_hcd/ | egrep '[0-9a-z]+\:[0-9a-
z]+\:.*$'`; do
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac
::::::::::::::
20_custom-ehci-pci
::::::::::::::
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci-pci".
TMPLIST=/tmp/ehci-dev-list


case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci-pci/ | egrep '[0-9a-z]+\:[0-9a-
z]+\:.*$'`; do
              # Unbind ehci-pci for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci-pci/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci-pci for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci-pci/bind
    done
    rm $TMPLIST
        ;;
esac
austin@Austin-Toshiba:/etc/pm/sleep.d$

---

### Post by entropy1 on 2015-03-23
Two things to notice about

```
-rw-r--r-- 1 root root 663 Mar 22 22:01 20_custom_ehci_hcd
```

First, the permissions should be -rwx-r-xr-x.  You can accomplish this with the command
```
sudo chmod 755 20_custom_ehci_hcd
```

The second thing to notice is that you might try changing the file name with
```
sudo mv 20_custom_ehci_hcd 20_custom-ehci_hcd
```

Notice the change of underscore to hyphen.

Finally, you now have both files 20_custom-ehci_hcd and 20_custom-ehci-pci

You probably want to see what happens when only one of these two files is available.  One way to do this is with
```
sudo mv 20_custom-ehci_hcd save20_custom-ehci_hcd
```

Try rebooting to see if you can suspend.

If that doen't help, try changing the name of the -pci file and restoring the name of the _hcd file; reboot and see if you can suspend.

Finally, if nothing works, try unplugging all USB connections before trying to suspend.

---

### Post by austin30 on 2015-03-23
I renamed it to <hyphen>ehci_hcd and did chmod. It's working fine now.
Thanks a lot entropy1.
I think the pci file didn't work for me. Because I did just as you told in your first reply and rebooted which didn't work.
And hcd when I corrected the name it just worked after the restart.
Thanks again. 
I will close this thread.

---

### Post by entropy1 on 2015-03-23
Glad I could help.  I think you mean that you will mark the thread as Solved.

---

### Post by austin30 on 2015-03-23
Suddenly that stopped working again.
I got an update today. Does that matter?

---

### Post by entropy1 on 2015-03-23
See if the file you created yesterday has been changed or deleted by the update.

---

### Post by austin30 on 2015-03-23
Suddenly it stopped working again.
I did an update today. Does that matter?

---

### Post by austin30 on 2015-03-23
The File seems to be intact.

---

### Post by entropy1 on 2015-03-23
Maybe the permissions or something changed.  Post the results of
```

cd /etc/pm/sleep.d
ls -l *

```

---

### Post by austin30 on 2015-03-23
here is it:

austin@Austin-Toshiba:/etc/pm/sleep.d$ ls -l *
-rwxr-xr-x 1 root root  210 Oct 16 05:48 10_grub-common
-rwxr-xr-x 1 root root  660 Feb 25  2014 10_unattended-upgrades-hibernate
-rwxr-xr-x 1 root root  663 Mar 22 22:01 20_custom-ehci_hcd
-rwxr-xr-x 1 root root  663 Mar 22 21:20 20_custom-ehci-pci
-rwxr-xr-x 1 root root 1260 May 22  2012 novatel_3g_suspend
austin@Austin-Toshiba:/etc/pm/sleep.d$

---

### Post by entropy1 on 2015-03-23
Notice that you have two files that begin with "20".  Change one of them to, for example, "save20...".  Try suspending.  If that doesn't help. Try rebooting and then suspending.  If suspend doesn't work, undo the name change and change the name of the other "20" file.  Try suspending.  If that doesn't work, try rebooting and then suspending.  After that, I am out of ideas.

By the way, did you try unplugging all USB connections (e.g., external keyboard and mice) before suspending, and were you then able to suspend?  It's not a great solution, but it might enable you to suspend.

---

### Post by austin30 on 2015-03-24
tried with only one file with both files as you told. even tried without any file. none works..
I dont have any usb devices connected, other than the keypad being a dock type for this model.

Any one else facing this issue? Any help?

---

### Post by austin30 on 2015-03-24
It worked again. This time after some normal restarts, and with both file renamed to a non-functional name.
I think the issue is random. Any one faced this and have a permanent fix?

---


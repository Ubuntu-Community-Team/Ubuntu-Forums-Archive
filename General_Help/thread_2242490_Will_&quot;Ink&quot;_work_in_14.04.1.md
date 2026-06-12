---
title: "Will &quot;Ink&quot; work in 14.04.1?"
date: 2014-09-02
forum: General Help
---

### Post by 2CV67 on 2014-09-02
I am trying to get an ink-level indicator for my Canon iP4300 printer.

I just installed "Ink" via Synapt, which also pulled in "libinklevel5".

But when I run "ink -p usb" I get:

```
chris@Acer-TC:~$ ink -p usb
Could not access '/dev/usb/lp0' or '/dev/usblp0'.
Could not get ink level.
chris@Acer-TC:~$ 
```

All suggestions welcome.

Thanks!

---

### Post by speartip on 2014-09-02
Works fine for me. You may need root. Try:
```
sudo ink -p usb
```
or if your printer is in a usb port I use:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo ink -d /dev/usb/lp0[/SIZE][/FONT][/COLOR]  
```
Hope this helps.

---

### Post by btindie on 2014-09-02
It's because your user account won't have permission to access the device node. Did you take a look at the documentation? 'man ink' 
>        /dev/usb/lpX and /dev/parportX and /dev/lpX              Devices used to read ink level.  Ink NEEDS read and write access to these devices.


What's the output of
```
ls -l /dev/usb/ 2>/dev/null
ls -l /dev/lp* 2>/dev/null
```

I think UDEV may set the group ownership of the device node to 'lp', so it may just be the case of adding your user account to that group.

---

### Post by 2CV67 on 2014-09-02
Thanks for 2 rapid answers!

Sudo didn't crack it (see below).

No - I must admit I did not look at the man page :oops:
But to be honest, I am more confused after reading it than before...

```
/dev/usb/lpX and /dev/parportX and /dev/lpX
              Devices used to read ink level.  Ink NEEDS read and write access
              to these devices.
```

Hmmm.
I do have a file /dev/usb/lp1 which has r&w for group lp.
I don't have the other items at all.

I have not yet found how to handle users & groups since Unity.
But I will start digging now.

Here are the results so far:
```
chris@Acer-TC:~$ sudo ink -p usb
[sudo] password for chris: 
Could not access '/dev/usb/lp0' or '/dev/usblp0'.
Could not get ink level.
chris@Acer-TC:~$ sudo ink -d /dev/usb/lp0
Could not access custom usb device '/dev/usb/lp0'.
Could not get ink level.
chris@Acer-TC:~$ ls -l /dev/usb/ 2>/dev/null
total 0
crw-rw---- 1 root lp 180, 1 Sep  2 11:14 lp1
chris@Acer-TC:~$ ls -l /dev/lp* 2>/dev/null
chris@Acer-TC:~$ 
```

Thanks again for your help!

---

### Post by btindie on 2014-09-02
Ok, so it's using lp1 and not lp0 which is what that command defaults to.

So first you need to add your user to the lp group, simple ->
```
sudo adduser chris lp
```
You'll then need to log out and back in again for it to take effect.

Then run the command as
```
ink -p usb -n 1
```
or
```
ink -d /dev/usb/lp1
```

---

### Post by 2CV67 on 2014-09-02
OK!

That is now working perfectly.

Thank you VERY much for your clear instructions! :D

Now I need to dig deeper for a GUI access to users/groups.
Looks like gnome-system-tools?.....

---


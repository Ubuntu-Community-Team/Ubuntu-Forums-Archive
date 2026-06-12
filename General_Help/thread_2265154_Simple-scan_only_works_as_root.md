---
title: "Simple-scan only works as root"
date: 2015-02-13
forum: General Help
---

### Post by satimis on 2015-02-13
Hi all.

Ubuntu 12.04
Epson Perfection 3490 Photo

I must start Simple-scan in following way otherwise "simple-scan" only works as root;

On Terminal
1) sudo simple-scan
2) exit
3) simple-scan

Then it works as user

$ cat /etc/group | grep usb```

usb:x:satimis
```

cat /etc/group | grep scanner```

scanner:x:107:satimis
```

I have been searching a while on Internet and couldn't solve the problem.  Please help.

Thanks in advance.

Regards
satimis

---

### Post by bab1 on 2015-02-13
> **satimis said:**
> Hi all.

Ubuntu 12.04
Epson Perfection 3490 Photo

I must start Simple-scan in following way otherwise "simple-scan" only works as root;

On Terminal
1) sudo simple-scan
2) exit
3) simple-scan

Then it works as user

$ cat /etc/group | grep usb```

usb:x:satimis
```

cat /etc/group | grep scanner```

scanner:x:107:satimis
```

I have been searching a while on Internet and couldn't solve the problem.  Please help.

Thanks in advance.

Regards
satimis

The app *simple-scan *is normally executable by all users.  What is the output of this```
ls -l /usr/bin/simple-scan
```

Have you modified any of the permissions in the /usr directory tree?

---

### Post by satimis on 2015-02-13
> **bab1 said:**
> The app *simple-scan *is normally executable by all users.  What is the output of this```
ls -l /usr/bin/simple-scan
```

Have you modified any of the permissions in the /usr directory tree?

Hi,

No.

$ ls -l /usr/bin/simple-scan```

-rwxr-xr-x 1 root root 254824 May  2  2014 /usr/bin/simple-scan

```

$ ls -al /dev/usb```

total 0
drwxr-xr-x  2 root root      80 Feb 13 15:49 .
drwxr-xr-x 18 root root    4720 Feb 13 15:49 ..
crw-------  1 root root 180, 96 Feb 13 15:49 hiddev0
crw-------  1 root root 180, 97 Feb 13 15:49 hiddev1

```

$ ls -ald /usr/```

drwxr-xr-x 10 root root 4096 Jan  3  2013 /usr/

```

$ ls -al /usr/```

total 172
drwxr-xr-x  10 root root  4096 Jan  3  2013 .
drwxr-xr-x  25 root root  4096 Feb  6 22:31 ..
drwxr-xr-x   2 root root 69632 Feb  6 22:29 bin
drwxr-xr-x   2 root root  4096 Jan 23  2013 games
drwxr-xr-x  42 root root 16384 Jan 29 17:53 include
drwxr-xr-x 209 root root 36864 Feb  6 22:29 lib
drwxr-xr-x  10 root root  4096 Jan  3  2013 local
drwxr-xr-x   2 root root 12288 Feb  6 22:29 sbin
drwxr-xr-x 332 root root 12288 Sep 30 22:45 share
drwxr-xr-x  36 root root  4096 Feb  6 22:31 src

```

Thanks

Regards
satimis

---

### Post by bab1 on 2015-02-13
What error code do you get when simple-scan does not work?

What happens when you use the command from the CLI?

---

### Post by satimis on 2015-02-13
> **bab1 said:**
> What error code do you get when simple-scan does not work?

What happens when you use the command from the CLI?
$ simple-scan```

[snapscan] Cannot open firmware file /etc/sane.d/Esfw52.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.

** (simple-scan:12458): WARNING **: scanner.vala:818: Unable to get open device: Invalid argument

```

$ ls -al /etc/sane.d/Esfw52.bin ```

-rwxr-x--- 1 root root 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

$ cat /etc/sane.d/snapscan.conf | grep scanner```

# firmware upload is needed by the scanner
# For USB scanners also specify bus=usb, e.g.
/dev/usb/scanner0 bus=usb
# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
#-------------------------- SCSI scanners ----------------------------------
#--------------------------- USB scanners -----------------------------------

```

satimis

---

### Post by bab1 on 2015-02-13
It looks like simpe-scan is working.  The problem appears to be the configuration of the scanner itself,

I just looked in my*** /etc/sane.d*** directory and see that every default scanner conf has rw-r--r-- root: root.  Your listing does not allow all users read permissions.  I'd see if changing the permissions helps the situation.  I'm only guessing here as I don't know anything about your scanners configuration.

My scanner is an old MicroTek and it looks like this```
-rw-r--r-- 1 root root 268 Dec  4  2011 /etc/sane.d/microtek2.conf
```

The code inside is obviously different than what you showed.

I've not had to manually configure a scanner in a long time and really can't remember how to do that on a newer Ubuntu disto.

[COLOR="#0000FF"]Edit:  I do see that there is a snapscan.conf file but I don't have any idea on how to set the config parameters.
I do see that there is a man page for snapscan.  

See[/COLOR]```
man sane-snapscan
... and 

man sane-scsi


```

---

### Post by satimis on 2015-02-13
> **bab1 said:**
> It looks like simpe-scan is working.  The problem appears to be the configuration of the scanner itself,

I just looked in my*** /etc/sane.d*** directory and see that every default scanner conf has rw-r--r-- root: root.  Your listing does not allow all users read permissions.  I'd see if changing the permissions helps the situation.  I'm only guessing here as I don't know anything about your scanners configuration.

My scanner is an old MicroTek and it looks like this```
-rw-r--r-- 1 root root 268 Dec  4  2011 /etc/sane.d/microtek2.conf
```

The code inside is obviously different than what you showed.

I've not had to manually configure a scanner in a long time and really can't remember how to do that on a newer Ubuntu disto.

[COLOR="#0000FF"]Edit:  I do see that there is a snapscan.conf file but I don't have any idea on how to set the config parameters.
I do see that there is a man page for snapscan.  

See[/COLOR]```
man sane-snapscan
... and 

man sane-scsi


```

Performed following steps:

$ sudo chown satimis:satimis /etc/sane.d/Esfw52.bin 

$ ls -al /etc/sane.d/Esfw52.bin```

-rwxr-x--- 1 satimis satimis 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

Rebooted PC

$ ls -al /etc/sane.d/Esfw52.bin ```

-rwxr-x--- 1 satimis satimis 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

$ simple-scan

This time simple-scan works as user.

Thanks

Edit:
If without running "sudo chown ..." is there an alternative?

Regards
satimis

---

### Post by ajgreeny on 2015-02-13
I wonder why you have a .bin file in the folder /etc/sane.d; I am not aware that a .bin would normally reside there.

How did you install the scanner, if you did need to install it, or did it just work out of the box?

---

### Post by satimis on 2015-02-13
> **ajgreeny said:**
> I wonder why you have a .bin file in the folder /etc/sane.d; I am not aware that a .bin would normally reside there.

How did you install the scanner, if you did need to install it, or did it just work out of the box?
Sorry I couldn't recall exactly.  I downloaded the bin tarball on Epson website.  It has been installed on this box sometime ago.  Seldomly I scan doc/photo.

satimis

---

### Post by bab1 on 2015-02-13
> **satimis said:**
> Performed following steps:

$ sudo chown satimis:satimis /etc/sane.d/Esfw52.bin 

$ ls -al /etc/sane.d/Esfw52.bin```

-rwxr-x--- 1 satimis satimis 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

Rebooted PC

$ ls -al /etc/sane.d/Esfw52.bin ```

-rwxr-x--- 1 satimis satimis 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

$ simple-scan

This time simple-scan works as user.

Thanks

Edit:
If without running "sudo chown ..." is there an alternative?

Regards
satimis

I would have used chmod to set the permissions so that all users could read the file.

Like this```
sudo chmod 644 /etc/sane.d/Esfw52.bin 
```...This way all uses can use the scanner while only root can modify the file.

---

### Post by satimis on 2015-02-13
> **bab1 said:**
> I would have used chmod to set the permissions so that all users could read the file.

Like this```
sudo chmod 644 /etc/sane.d/Esfw52.bin 
```...This way all uses can use the scanner while only root can modify the file.
Performed following steps;

$ sudo chown root:root /etc/sane.d/Esfw52.bin 

$ sudo chmod 644 /etc/sane.d/Esfw52.bin 

$ ls -al /etc/sane.d/Esfw52.bin```

-rw-r--r-- 1 root root 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

Reboot PC

Now simple-scan works as user.  Thanks

satimis

---

### Post by bab1 on 2015-02-13
> **satimis said:**
> Performed following steps;

$ sudo chown root:root /etc/sane.d/Esfw52.bin 

$ sudo chmod 644 /etc/sane.d/Esfw52.bin 

$ ls -al /etc/sane.d/Esfw52.bin```

-rw-r--r-- 1 root root 64000 Jun 25  2014 /etc/sane.d/Esfw52.bin

```

Reboot PC

Now simple-scan works as user.  Thanks

satimis

Good work!  Now post this thread as solved.  Use the ***thread tools*** tab at the top right of the thread page.

---


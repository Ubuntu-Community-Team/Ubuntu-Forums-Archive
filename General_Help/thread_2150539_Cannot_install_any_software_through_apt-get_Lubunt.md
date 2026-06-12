---
title: "Cannot install any software through apt-get Lubuntu 13.04"
date: 2013-06-01
forum: General Help
---

### Post by SangeetKhatri on 2013-06-01
Whenever i try to install any app in lubuntu using the "sudo apt-get install package" then it downloads and looks like everything is going fine but when the process is about to finish then suddenly an error shows up in the terminal which says that 

"Errors were encountered while processing: linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

What does that mean? I cannot install any software through the apt-get and also there are a lot of errors in my computer and many crashes.
Is there anything wrong with my Kernel?

And does anyone have a solution for it?

This is what i got when i tried to install gedit using the command "sudo apt-get install gedit"
Please someone help me...

```
sangeet@sangeet-Aspire-5738:~$ sudo apt-get install gedit
[sudo] password for sangeet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libpeas-1.0-0 libpeas-common python-gi-cairo
Suggested packages:
  gedit-plugins
The following packages will be REMOVED:
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libpeas-1.0-0
  libpeas-common python-gi-cairo
0 upgraded, 9 newly installed, 2 to remove and 9 not upgraded.
7 not fully installed or removed.
Need to get 1,062 kB of archives.
After this operation, 112 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ raring/main libgtksourceview-3.0-common all 3.6.3-0ubuntu1 [135 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ raring/main libgtksourceview-3.0-0 i386 3.6.3-0ubuntu1 [157 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ raring/main libpeas-common all 1.6.2-0ubuntu1 [12.8 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ raring/main libpeas-1.0-0 i386 1.6.2-0ubuntu1 [52.9 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ raring/main gir1.2-gtksource-3.0 i386 3.6.3-0ubuntu1 [13.2 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ raring/main gedit-common all 3.6.2-0ubuntu1 [147 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu/ raring/main python-gi-cairo i386 3.8.0-2 [5,728 B]
Get:8 http://in.archive.ubuntu.com/ubuntu/ raring/main gir1.2-peas-1.0 i386 1.6.2-0ubuntu1 [5,628 B]
Get:9 http://in.archive.ubuntu.com/ubuntu/ raring/main gedit i386 3.6.2-0ubuntu1 [532 kB]
Fetched 1,062 kB in 14s (70.9 kB/s)                                            
(Reading database ... 180977 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-22-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-22-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
sangeet@sangeet-Aspire-5738:~$ gedit
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt-get install gedit
```

Regards

---

### Post by ibjsb4 on 2013-06-01
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Try that and see what happens.

---

### Post by SangeetKhatri on 2013-06-01
outputs:
sudo apt-get autoremove : [http://paste.ubuntu.com/5723387/](http://paste.ubuntu.com/5723387/)
sudo apt-get dist-update : [http://paste.ubuntu.com/5723449/](http://paste.ubuntu.com/5723449/)

and still i cannot install any application : 
sudo apt-get thunar : [http://paste.ubuntu.com/5723450/](http://paste.ubuntu.com/5723450/)

Still showing the same error infact this time showing more error in the thunar installation.

Please help me what to do. I cannot install anything.
Any help is highly appreciated
Thank You.

---

### Post by ibjsb4 on 2013-06-01
Before I make another suggestion please post the output of:

```
uname -r
```

I want to be sure about the kernel that your currently using, thanks.

---

### Post by SangeetKhatri on 2013-06-01
sangeet@sangeet-Aspire-5738:~$ uname -r
3.8.0-21-generic

So what do you think?

---

### Post by Cheesehead on 2013-06-01
> **SangeetKhatri said:**
> 
```

Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-22-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
[COLOR="#FF0000"]/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found[/COLOR]
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1

```


Here's what it means:
The system is trying to remove the old 3.8.0-19-generic kernel, but is choking on a command.
Until you fix this, no package actions will work at all.

Here's what you do:
See that error line in red? Let's look there first.
```
me@deep-thought:~$ less /etc/default/grub 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
//the rest edited out//

```

Wait a second. See that word 'splash' on Line 11? That's what the error message was talking about.
So look at your /etc/default/grub and see if it's been malformed or corrupted and does not look like the example.
You'll need to use sudo to fix it.

If your /etc/default/grub looks different, feel free to paste it here.

---

### Post by SangeetKhatri on 2013-06-01
This is the content of my grub file.
Please have a look at it.
```

# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash nomodeset i8042.nomux acpi_backlight=vendor&#8221; 
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

Thankyou

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]SangeetKhatri;

Just a thought ..as the "grub" file looks all right, maybe with the updated kernel those boot parameters are no longer needed ??

what results if ya remove them and only add back in what is required ??
Leaving only "quiet splash" --the quote marks are required-  for starters .
[/COLOR][INDENT][COLOR=#000000]

kernel is smart, now real smart ??

[/COLOR][/INDENT]

---

### Post by SangeetKhatri on 2013-06-02
i seriously don't get what you're trying to say.
Can you please tell me what to do next to solve the problem. And if i have to remove something then how do i do it?

---

### Post by Cheesemill on 2013-06-02
I think it may be hanging because of the incorrect quote marks in your grub config.
Open the file for editing by running...
```
gksudo gedit /etc/default/grub
```
and change line 11 from...
```
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux acpi_backlight=vendor”
```
to...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset i8042.nomux acpi_backlight=vendor"
```

Notice that it should be straight double-quotes instead of curly ones.

Save the file and update your grub config by running...
```
sudo update-grub
```

This should fix your problem :)

---

### Post by Cheesehead on 2013-06-02
I think Cheesemill's sharp eyes have spotted the problem.

---

### Post by Bashing-om on 2013-06-02
@ [COLOR=#000000]Cheesemill ;
Awe-sooo said the blind man (me) !
Please ,if you can, shed some light on my ignorance. In respect to those "curved" quotes in the OP's file; How are the miss-quotes generated ? I am on a US (English) keyboard and can not see how to duplicate "curved" quote marks.

For the next time this situation arises ![/COLOR][INDENT=2][COLOR=#000000]
inquiring minds want to know

[/COLOR][/INDENT]

---

### Post by Cheesemill on 2013-06-02
They don't appear on a UK keyboard either.

The only time that I come across curved quote marks is when using a word processor, the auto-correct feature often replaces straight quotes with curly ones.
As to how they ended up in the OP's grub config I have no idea :confused:

---

### Post by ibjsb4 on 2013-06-02
Good call Cheesemill, I would of never seen that or expected such a thing.

---

### Post by Cheesemill on 2013-06-02
Thanks guys but don't speak too soon, we don't know for sure if this is the cause of the all the OP's problems.

---

### Post by SangeetKhatri on 2013-06-04
Thanks a lot man. Problem Solved. I am sorry for responding so late but due to some problems i was not able to connect to the internet for 2 days. And this is the first thing that i am checking since i have again got the internet and it got solved in the first instance.
Thanks a lot man.
You really got sharp eyes.

---

### Post by SangeetKhatri on 2013-06-04
Anyways how to mark this thread as [SOLVED] ?? Cannot find it anywhere..

---

### Post by Cheesemill on 2013-06-04
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by SangeetKhatri on 2013-06-05
Well.. The problem is not solved yet, the main software install problem is solved but after reboot i encountered another problem that i think might be related to grub. So here is my problem.
When i turn on my laptop it automatically boots in 1024 x 768 resolution but my screen resolution is 1366 x 768 , and when i go to monitor settings then too i cannot find only two resolutions as options. first one being "1024 x 768" and another one being the "Auto" option. Apparently none of then can solve my problem. So here is my question. How to solve this issue?

---

### Post by trishawthomas on 2013-06-05
> **SangeetKhatri said:**
> Whenever i try to install any app in lubuntu using the "sudo apt-get install package" then it downloads and looks like everything is going fine but when the process is about to finish then suddenly an error shows up in the terminal which says that 

"Errors were encountered while processing: linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

What does that mean? I cannot install any software through the apt-get and also there are a lot of errors in my computer and many crashes.
Is there anything wrong with my Kernel?

And does anyone have a solution for it?

This is what i got when i tried to install gedit using the command "sudo apt-get install gedit"
Please someone help me...

```
sangeet@sangeet-Aspire-5738:~$ sudo apt-get install gedit
[sudo] password for sangeet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libpeas-1.0-0 libpeas-common python-gi-cairo
Suggested packages:
  gedit-plugins
The following packages will be REMOVED:
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libpeas-1.0-0
  libpeas-common python-gi-cairo
0 upgraded, 9 newly installed, 2 to remove and 9 not upgraded.
7 not fully installed or removed.
Need to get 1,062 kB of archives.
After this operation, 112 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ raring/main libgtksourceview-3.0-common all 3.6.3-0ubuntu1 [135 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ raring/main libgtksourceview-3.0-0 i386 3.6.3-0ubuntu1 [157 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ raring/main libpeas-common all 1.6.2-0ubuntu1 [12.8 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ raring/main libpeas-1.0-0 i386 1.6.2-0ubuntu1 [52.9 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ raring/main gir1.2-gtksource-3.0 i386 3.6.3-0ubuntu1 [13.2 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ raring/main gedit-common all 3.6.2-0ubuntu1 [147 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu/ raring/main python-gi-cairo i386 3.8.0-2 [5,728 B]
Get:8 http://in.archive.ubuntu.com/ubuntu/ raring/main gir1.2-peas-1.0 i386 1.6.2-0ubuntu1 [5,628 B]
Get:9 http://in.archive.ubuntu.com/ubuntu/ raring/main gedit i386 3.6.2-0ubuntu1 [532 kB]
Fetched 1,062 kB in 14s (70.9 kB/s)                                            
(Reading database ... 180977 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-22-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-22-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
sangeet@sangeet-Aspire-5738:~$ gedit
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt-get install gedit
```

Regards

Just try 

sudo apt-get clean
then try to install see what happens.

---

### Post by SangeetKhatri on 2013-06-05
So guys my software installing problem has been solved but there has been a new problem for which i have started a new thread so i will mark this thread as [SOLVED]. Thank You guys for your awesome support.

---

### Post by seruling on 2013-06-18
I have same problem with ubuntu 13.04. Can't upgrade anything.

My desktop is Unity(default)+gnome+xfce. I often use gnome desktop when logging in.

On grub file, it shows:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

I still don't get how to fix it. Do I have to modify that line?

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]seruling; Hi !

No, that looks good.. must be another cause ?
Please post the output of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
``` so we may see the error and perhaps what generated the error.

Further advise is pending.[/COLOR][INDENT=5][COLOR=#000000]regards

[/COLOR][/INDENT]

---


---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-06-30
forum: General Help
---

### Post by Noorstream on 2013-06-30
Hi,

I did an upgrade that got interrupted and eversince, I get errors while upgrading.  I ran the following command in the terminal:

```
sudo apt-get -f install
```

And I get the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.8.0-24-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 96.4 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
sharez@The:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.8.0-24-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 96.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 307534 files and directories currently installed.)
Removing linux-image-extra-3.8.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-24-generic /boot/vmlinuz-3.8.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-24-generic /boot/vmlinuz-3.8.0-24-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-24-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.8.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.8.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help would be appreciated.

---

### Post by steeldriver on 2013-06-30
Hello and welcome to the forum

It looks like there might be an error somewhere in your grub configuration file - can you please post the output of

```
cat -n /etc/default/grub
```

---

### Post by Noorstream on 2013-06-30
Thank you.

I entered the command in the terminal and it gave the following output:

     1    # If you change this file, run 'update-grub' afterwards to update
     2    # /boot/grub/grub.cfg.
     3    # For full documentation of the options in this file, see:
     4    #   info -f grub -n 'Simple configuration'
     5    
     6    GRUB_DEFAULT=0
     7    GRUB_HIDDEN_TIMEOUT=0
     8    GRUB_HIDDEN_TIMEOUT_QUIET=true
     9    GRUB_TIMEOUT=10
    10    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    11    GRUB_CMDLINE_LINUX_DEFAULT=""quiet splash acpi_backlight=vendor""
    12    GRUB_CMDLINE_LINUX=""
    13    
    14    # Uncomment to enable BadRAM filtering, modify to suit your needs
    15    # This works with Linux (no patch required) and with any kernel that obtains
    16    # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
    17    #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
    18    
    19    # Uncomment to disable graphical terminal (grub-pc only)
    20    #GRUB_TERMINAL=console
    21    
    22    # The resolution used on graphical terminal
    23    # note that you can use only modes which your graphic card supports via VBE
    24    # you can see them in real GRUB with the command `vbeinfo'
    25    #GRUB_GFXMODE=640x480
    26    
    27    # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    28    #GRUB_DISABLE_LINUX_UUID=true
    29    
    30    # Uncomment to disable generation of recovery mode menu entries
    31    #GRUB_DISABLE_RECOVERY="true"
    32    
    33    # Uncomment to get a beep at grub start
    34    #GRUB_INIT_TUNE="480 440 1"



> **steeldriver said:**
> Hello and welcome to the forum  It looks like there might be an error somewhere in your grub configuration file - can you please post the output of  ```
cat -n /etc/default/grub
```

---

### Post by steeldriver on 2013-06-30
Try removing the extra quotes from the GRUB_CMDLINE_LINUX_DEFAULT string in line 11

```
11    GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=#ff0000]**"**[/COLOR]"quiet splash acpi_backlight=vendor"[COLOR=#ff0000]**"**[/COLOR]
```

(you will need sudo to edit the file e.g. 'sudo gedit /etc/default/grub') and then either re-running the apt-get -f or manually running

```
sudo update-grub
```

---

### Post by Noorstream on 2013-06-30
I did that and the problem is fixed.  Thanks!

> **steeldriver said:**
> Try removing the extra quotes from the GRUB_CMDLINE_LINUX_DEFAULT string in line 11

```
11    GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=#ff0000]**"**[/COLOR]"quiet splash acpi_backlight=vendor"[COLOR=#ff0000]**"**[/COLOR]
```

(you will need sudo to edit the file e.g. 'sudo gedit /etc/default/grub') and then either re-running the apt-get -f or manually running

```
sudo update-grub
```

---


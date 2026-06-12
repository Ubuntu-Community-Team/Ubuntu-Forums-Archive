---
title: "Grub Customizer - Failed saving grub configuration!"
date: 2014-06-08
forum: General Help
---

### Post by AmagicalFishy on 2014-06-08
Hey, everyone. 

For a while now, my Grub Customizer hasn't been working. Here's the error:

> 
failed running 'grub-mkconfig -o "/boot/grub/grub.cfg"' output:Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-23-generic
Found initrd image: /boot/initrd.img-3.11.0-23-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found Windows 7 (loader) on /dev/sda1
Found linux image: /boot/vmlinuz-3.11.0-23-generic
Found initrd image: /boot/initrd.img-3.11.0-23-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Found linux image: /boot/vmlinuz-3.11.0-23-generic
Found initrd image: /boot/initrd.img-3.11.0-23-generic
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 173
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub


Reinstalling Grub Customizer didn't work, but I don't know how to interpret the above. I've got a lot of useless entries after an  update. :l

Anyonw know what to make of it?

---

### Post by oldfred on 2014-06-09
If you make changes with Grub Customizer it modifies scripts in many cases with its version of the script. I think it copies original scripts to a sub folder. But then an grub reinstall may copy original files back in and you have duplicate script files in grub folder. 
Grub runs every script starting with 2 digits & an underscore that is executable.

Post this:
ls -l /etc/grub.d

If you have this file look at line 173, if you have errors it usually does not update grub.cfg but saves the error file. If you have a typo in grub scripts or /etc/default/grub then you get that type of error.
 /boot/grub/grub.cfg.new

---

### Post by AmagicalFishy on 2014-06-09
Ah! Which file should I be looking at (the one whose line 173 is significant)?

> 
-rwxr-xr-x 1 root root 7806 Dec  6  2013 00_header
-rwxr-xr-x 1 root root 5522 Dec  6  2013 05_debian_theme
-rwxr-xr-x 1 root root 1056 Jun  8 17:16 10_linux_proxy
-rwxr-xr-x 1 root root  223 Jun  8 17:16 30_os-prober_proxy
-rwxr-xr-x 1 root root 1046 Jun  8 17:16 33_linux_proxy
-rwxr-xr-x 1 root root 6449 Dec  6  2013 34_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 35_memtest86+
-rwxr-xr-x 1 root root 1007 Jun  8 17:16 36_linux_proxy
-rwxr-xr-x 1 root root 1388 Dec  6  2013 37_uefi-firmware
-rwxr-xr-x 1 root root  214 Dec  6  2013 40_custom
-rwxr-xr-x 1 root root   95 Dec  6  2013 41_custom
drwxr-xr-x 4 root root 4096 Apr 17 08:57 backup
drwxr-xr-x 2 root root 4096 Apr 17 08:57 bin
drwxr-xr-x 2 root root 4096 Jun  8 17:16 proxifiedScripts
-rw-r--r-- 1 root root  483 Dec  6  2013 README


I'm unfortunately not familiar enough with the file to know whether or not something's a typo. I did give a look to grub.cfg.new, though, and did not see anything blatantly wrong (this would have to be like... the lines "if True == True: destroy compputer" for me to catch it, though).

---

### Post by oldfred on 2014-06-09
If you have the grub.cfg.new then it is line 173 in that to look at. Post several lines around 173, no need to post entire thing.

I do not know grub customizier, but all the files with proxy in the name are from grub customizer and the x at the end of the permissions is the executable setting, so all are executable except the readme. Do not know what 33_ and 35_ are. They may be the duplicates?

Just to get back to normal, I might copy all the files in grub.d to another folder and use Boot-Repair to totally uninstall and reinstall grub2.
If you like grub customizer then you can reinstall it, but starting from the beginning.

Or you can manually edit most grub settings.

---

### Post by AmagicalFishy on 2014-06-09
Here's what I have starting at Line 173:
> 
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}

I think I will follow what you'd do, though, and use Boot-Repair.

Thanks for your help. :) I'll report back in if this works or not.

---

### Post by AmagicalFishy on 2014-06-09
Everything worked out beautifully. Thanks again, oldfred. :D

---

### Post by oldfred on 2014-06-09
In my system it is from 10_linux and is line 75.

```
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}

```

I cannot see a difference between my version and yours.

---


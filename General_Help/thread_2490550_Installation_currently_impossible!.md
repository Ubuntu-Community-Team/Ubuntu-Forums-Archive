---
title: "Installation currently impossible!"
date: 2023-09-07
forum: General Help
---

### Post by gramlinsinthesystem on 2023-09-07
Hi, I use Ubuntu (Budgie) and just lately I have had update and installation errors. The updater now informs me that installation is currently impossible. 

Running sudo apt-get install -f returns: 
```
~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED
  linux-image-6.2.0-31-generic
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 13.8 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 853759 files and directories currently installed.)
Removing linux-image-6.2.0-31-generic (6.2.0-31.31~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.2.0-31-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.2.0-31-generic (--remove):
 installed linux-image-6.2.0-31-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-6.2.0-31-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know quite how, but it seems to be attempting to run a script from the very package it is also trying to install. I'm afraid I don't know where to start but could really use some help. Thanks, if you are able to.

---

### Post by Impavidus on 2023-09-07
```
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
```
It tries to execute a comment. Chances are that somehow a backslash was inserted before the hash sign on the first line of /etc/default/grub.

Edit the file as root:
```
sudoedit /etc/default/grub
```Fix the issue, save the file, try again. If that wasn't the issue, please show the contents of your /etc/default/grub.

Have you done any tweaking of grub recently?

---

### Post by gramlinsinthesystem on 2023-09-07
Thank you, Impavidus. I did edit grub a while ago but thought I'd put it back to normal. The contents are: 
```
  # If you change this file, run 'update-grub' afterwards to update
 # /boot/grub/grub.cfg.
 # For full documentation of the options in this file, see:
 #   info -f grub -n 'Simple configuration'
 

 GRUB_DEFAULT=0
 GRUB_TIMEOUT_STYLE=hidden
 GRUB_TIMEOUT=0
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

I ran update-grub, just in case it hadn't been updated. Similar error:
```
$ sudo update-grub
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found

```

---

### Post by Rubi1200 on 2023-09-07
There seems to be an extra space at the start of your file:

```
[COLOR=#ff0000]  # If you change this file, run 'update-grub' afterwards to update[/COLOR]
 # /boot/grub/grub.cfg.
 # For full documentation of the options in this file, see:
 #   info -f grub -n 'Simple configuration'

```

Edit the file again and use backspace before the # to make the line even with the ones below.

Save, run update-grub and reboot.

Was that the issue?

---

### Post by Impavidus on 2023-09-08
Most script interprters don't mind an additional space before a comment, but maybe grub-mkconfig is one of those that only accept comments at the start of the line. Indeed, remove that space.

---

### Post by gramlinsinthesystem on 2023-09-12
> Edit the file again and use backspace before the # to make the line even with the ones below.

Save, run update-grub and reboot.

Was that the issue?

Unfortunately not :( I am perplexed. I searched the file for stray # and found none. I still can't work out why it's trying to run a comment at all.

FURTHER: I've played around with it, e.g. by deleting a # and then grub-update happily tells me "if: not found". I tried adding a space and grub-update tells me "  : not found". 

But as soon as I restore the # at the start of the comment (e.g. "# if you change this file...") grub-update begins telling me "#: not found" again. It's like no longer knows to ignore comments. Why would that be?

---

### Post by Rubi1200 on 2023-09-12
Are you booting any other operating systems or just Ubuntu?

Since we have come this far how about we try rebuilding the default GRUB file:

First, make a backup of the current file just in case:
```
sudo mv /etc/default/grub /etc/default/grub.bak

```

Then open and edit the file:
```
sudo nano /etc/default/grub

```

Check if everything looks fine, for example:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='lsb_release -i -s 2> /dev/null || echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This is useful when a buggy BIOS corrupts some memory areas.
# Add kernel boot options in here


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


# Set GRUB_BACKGROUND to the path of your wallpaper image file
#GRUB_BACKGROUND="/path/to/wallpaper.jpg"

```



Then run update-grub and reboot.

Keeping my fingers crossed :-)

---

### Post by Impavidus on 2023-09-12
I checked. This time really. Your initial symptom is expected if your /etc/default/grub starts with '\# ', but not if it starts with ' # ', as yours appears te be.

Maybe some non-printing characters present? Or maybe you don't run the shell you think you run.

---

### Post by gramlinsinthesystem on 2023-09-14
OK, I think editing in Nano revealed the mysterious error. The first line was showing up formatted, e.g. in white not coloured. Even though it was impossible to see it in a non-colour-coded editor. See the screen shot. I've deleted the formatted line entirely and run 'update-grub' successfully now! 

Thank for all the input. 

Screenshot:
[https://www.dropbox.com/scl/fi/tgf7yhhn9hh861anag59b/Screenshot-from-2023-09-14-10-00-50.png?rlkey=7ag9dt9p5fzmigwla0lw59wbf&dl=0](https://www.dropbox.com/scl/fi/tgf7yhhn9hh861anag59b/Screenshot-from-2023-09-14-10-00-50.png?rlkey=7ag9dt9p5fzmigwla0lw59wbf&dl=0)

---

### Post by Rubi1200 on 2023-09-14
Well, that's a new one for me! I'm not sure that was the problem though. A different color should not have affected the file as far as I know. Perhaps it was some hidden character as Impavidus suggested. Either way, if it is fixed that's great :-)

If the issue is resolved, please mark the thread Solved using the Thread Tools at the top right of your first post.

---


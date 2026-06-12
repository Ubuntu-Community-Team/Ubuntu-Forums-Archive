---
title: "why does GRUB showing even w/ only 1 operating system installed?"
date: 2024-03-22
forum: General Help
---

### Post by merlh1n on 2024-03-22
How do I make the GRUB not appearing every time I boot? this only happened after installing ubuntu23.10 then going back to 22.04 LTS. Help please

[https://paste.ubuntu.com/p/C876NYR5DV/](https://paste.ubuntu.com/p/C876NYR5DV/)
(this is from boot repair, hopefully this helps)

---

### Post by Rubi1200 on 2024-03-23
Hi and welcome to the forums :-)

The report appears to be missing information for the GRUB configuration.

Please open a terminal and post the output of this command:

```
cat /etc/default/grub
```

When replying click on Go Advanced and paste then highlight the output and click on the # icon to wrap with code tags.

Thanks.

---

### Post by merlh1n on 2024-03-23
Hello and thank you for noticing this.

Here's the output for the command you have provided:

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

---

### Post by tea for one on 2024-03-23
Your grub file looks OK (to not display the grub menu)
Did you run?
```
sudo update-grub
```

---

### Post by merlh1n on 2024-03-23
Yes. I have run it few times.

Here's the result of updating grub:
```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-26-generic
Found initrd image: /boot/initrd.img-6.5.0-26-generic
Found linux image: /boot/vmlinuz-6.5.0-18-generic
Found initrd image: /boot/initrd.img-6.5.0-18-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

---

### Post by tea for one on 2024-03-23
Department of Guesswork now responding:-

Power off
Remove your second disk (nvme1n1)
Power on

Grub has vanished?

---

### Post by merlh1n on 2024-03-23
Just tried removing my second drive and updating grub. Unfortunately, the problem still persist

---

### Post by tea for one on 2024-03-23
Zero progress so far, but let's see if anything else can be done

How about changing grub settings to deliberately make it appear for a second or two.
Boot a few times.
Then change the grub settings again to not appear.

---

### Post by dragonfly41 on 2024-03-23
Another guesswork department. Even though just one boot option is required you can install rEFInd (really intended for multi boot) and reduce the display time to one second or less.

[https://askubuntu.com/questions/1393871/how-to-edit-refind-to-make-ubuntu-boot-automatically-in-my-macbook-pro-15-2018](https://askubuntu.com/questions/1393871/how-to-edit-refind-to-make-ubuntu-boot-automatically-in-my-macbook-pro-15-2018)

rEFInd will be handy if later you add another boot option and reset the display time

---

### Post by pedrocedro on 2024-03-23
Hello friend, my problem is the opposite of yours, I have win and ubuntu but, for some reason, I'm not able to boot ubuntu anymore, BIOS doesn't show it anymore. And I don't have grub screen too. So don't be sad with grub showing to you, you may use it to boot another linux distro or win. Stay fine!

---

### Post by dragonfly41 on 2024-03-23
Then try installing rEFInd which sits alongside, not replacing grub. You should be able to locate Ubuntu.

---

### Post by dragonfly41 on 2024-03-23
Inside Win, install trial EasyUEFI, You have a 14 day trial before payment required. Use that free trial to fix UEFI issues from within Windows.

---

### Post by pedrocedro on 2024-03-23
Hello my friend. I Could solve my problem with a Windows Software called "Hasleo EasyUEFI". I could manually added the grub boot I needed. Then I could boot both OS(win and ubuntu) in the grub.
So as I said, I think you can remove it too. Do it with caution, make sure your Windows Boot manager is fine. Thats it.

---

### Post by merlh1n on 2024-03-25
Can you walk me through this?

---

### Post by yancek on 2024-03-25
>  Can you walk me through this?

The other member's situation was different as s/he had windows and the software he refers to requires a windows system as it is an .exe file.  The same for EasyRE from Neosmart.  Your boot repair report seemed to be lacking standard information for some reason and showed no sign of windows.

---

### Post by dragonfly41 on 2024-03-25
[COLOR=#000000]*> Can you walk me through this?*[/COLOR]

OP, if by "this" you are referring to earlier idea to try rEFInd here is the site explaining installation.
[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind

You might have to enter your BIOS on rebooting to identify new rEFInd in boot options and set it to top option.

The other strategy to try EasyUEFI suggested to other participant applies to Win only users.

---


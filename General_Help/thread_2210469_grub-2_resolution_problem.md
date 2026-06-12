---
title: "grub-2 resolution problem"
date: 2014-03-10
forum: General Help
---

### Post by Ken Steele on 2014-03-10
I running Ubuntu 12.04 64-bit. I have dual boot. (windows 7)
 
 My motherboard is a mcp61-gm with Integrated NVIDIA GeForce 6150SE nForce 430 graphics.

 My monitor is a Emerson Model LF320EM4.

 At bootup I can not see the bootloader because I get an error message from my monitor saying there is a resolution / refresh rate mismatch. After Grub-2 times out Ubuntu loads and runs fine. However because I cant see Grub-2 I can not boot my windows 7 install.

---

### Post by deadflowr on 2014-03-11
Have you uncommented the line
GRUB_GFXMODE=640x480
(meaning removed the # symbol from the start of that line)
in the file /etc/default/grub ?

If not maybe try that, and reset the size to something more practical.
(instead of 640x480.)

You'll need to edit it as root.
```
sudo nano /etc/default/grub
```
works good enough.
```
gksu gedit /etc/default/grub
```
when done rerun the grub updater
```
sudo update-grub
```

---

### Post by Ken Steele on 2014-03-11
gksu gedit /etc/default/grub worked I was able to edit and save.

sudo update-grub gave me the following
/usr/sbin/grub-mkconfig: 25: /etc/default/grub: x: not found  

still can not see the bootloader

---

### Post by deadflowr on 2014-03-11
Post the output for
```
cat /etc/default/grub
```
(Please use [Code Tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"))
What's line 25?

There shouldn't be any errors, so...

---

### Post by Ken Steele on 2014-03-11
ken@Kenz-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
GRUB_GFXMODE=1,360 x 768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
ken@Kenz-desktop:~$

---

### Post by deadflowr on 2014-03-11
Re edit the file and change the resolution.
make it 1360 x 768.
Remove the , symbol.
It's making no sense to the program as it reads it.
Hence the error.

See if that does anything.

---

### Post by claracc on 2014-03-11
I think wrong line is:

```
GRUB_GFXMODE=1,360 x 768
```

Perhaps, It would be say: ```
GRUB_GFXMODE=1360 x 768
``` ?

Well, I arrived a little late

---

### Post by Ken Steele on 2014-03-11
(code)ken@Kenz-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
GRUB_GFXMODE=1360 x 768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
ken@Kenz-desktop:~$ 
(code)

---

### Post by Ken Steele on 2014-03-11
```
 ken@Kenz-desktop:~$ gksu gedit /etc/default/grub
ken@Kenz-desktop:~$ sudo update-grub
sudo: unable to resolve host Kenz-desktop
/usr/sbin/grub-mkconfig: 25: /etc/default/grub: x: not found
ken@Kenz-desktop:~$ 
```

---

### Post by claracc on 2014-03-11
perhaps you cannot write empty spaces, i.e.: 

```
GRUB_GFXMODE=1360x768
```

seems to be the "good" spelling.

Please see: [http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

---

### Post by Ken Steele on 2014-03-11
I tried diffrent resolution settings, but still wont display grub in a usable resolution. when I hold the shift down it stops at the message on my monitor about resolution / refresh rate mismatch.

---

### Post by Ken Steele on 2014-03-11
Ok the spaces were it. The error when updating grub is gone. However I still cant see Grub at startup. My monitor still says there is a resolution / refresh rate mismatch. I tried a couple diffren resolution settings.

---

### Post by Ken Steele on 2014-03-11
OK I kept trying diffrent res settings. when I got down to  800 x 600 it worked. Thanks for all the help deadflower and claracc.

---

### Post by claracc on 2014-03-11
You are very welcome. Glad you got fixed your problem.

Please, mark the thread as solved with "thread tools".

Thanks.

---


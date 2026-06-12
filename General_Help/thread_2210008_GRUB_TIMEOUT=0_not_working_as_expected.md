---
title: "GRUB_TIMEOUT=0 not working as expected"
date: 2014-03-08
forum: General Help
---

### Post by donsy on 2014-03-08
WindowsXP E0L is next month and I would like to keep the partition active for a while yet boot directly into Linux without the Grub2 menu and the timeout. If I set GRUB_TIMEOUT=0, Grub will still default to waiting 10 seconds. But if I set GRUB_TIMEOUT=1 it works as expected and displays the menu only 1 second. Why won't it work for GRUB_TIMEOUT=0? I make sure to run 'sudo update-grub' after every update. Here is my complete /etc/default/grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
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

### Post by varunendra on 2014-03-08
Setting "GRUB_TIMEOUT" value to 0 is not a good idea. If it is defaulting to 10 seconds, I think it is in fact an '_Improvement_' in Grub2 to avoid some troubles users used to get in after setting it to 0.

As far as I remember, setting it to 0 used to do what you expect it to do - boot immediately into the default selection. However, think of the situation when you set windows as the "Default" selection and set the GRUB_TIMEOUT" to 0. What will happen? A trouble - you will NEVER get a chance to boot into Ubuntu again and change this setting back. Booting with a Live CD was the only option left to fix it.

That's why I think it is actually an Improvement if now it is defaulting to 10 seconds.

The Recommended Way to do what you want is to RESET the GRUB_TIMEOUT value to 10 (at least 3) seconds, THEN uncomment this line -
```
**[COLOR="#FF0000"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0
```
As soon as it is uncommented, with its value being 0, Grub will start to boot right away into the default selection, without waiting for any timeout (unless you interrupt the booting by pressing 'Shift' at boot time).

The GRUB_TIMEOUT becomes effective only when the menu is displayed. With the above change, it won't display, as if it were a single OS system (actually it is uncommented by default if there is no other OS on the system).

So.. the recommended file would look like this -
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
**GRUB_HIDDEN_TIMEOUT=0**
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=[COLOR="#006400"]10[/COLOR]**
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
Make it look like above, then do a "sudo update-grub". Then come back and let us know if it did what you wanted.

For a detailed information about what each provided option does and when, please refer to this awesome post by drs305 : [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The same (updated) information is also available on the community wiki page, but is scattered across multiple pages : [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by donsy on 2014-03-08
It looks like I may have to delete the Windows partition for it to work, and even then I'm not so sure.
```
~$ sudo update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

```

---

### Post by varunendra on 2014-03-08
> **donsy said:**
> It looks like I may have to delete the Windows partition for it to work, and even then I'm not so sure.

If you are worried about the warning, I believe you can ignore it, it may be just a notification (can't test here, since I still have an older version of Grub2). Reboot to test if the change took effect.

Also, since it is complaining about non-zero value, and a zero-value is already defaulting to 10 seconds, I think it is (with the new changes in newer version) safe now to set it to zero like you were doing. What I wrote was applicable to the version I am using (and the older ones), maybe it is zero by default for new versions. In any case, it shouldn't hurt if Ubuntu is set as the default OS.

And if you are worried about it detecting XP, I think that can be (should be) ignored as well, since it doesn't matter when the menu is going to bypassed anyway.

However, IF you want (or really need) to disable the detection of XP, just disable the "os-prober" script temporarily -
```
sudo chmod -x /usr/bin/os-prober
```
Then run an "update-grub" again. The os-prober part won't work this time, so XP won't get detected.

To enable the os-prober again -
```
sudo chmod +x /usr/bin/os-prober
```

---

### Post by donsy on 2014-03-08
> **varunendra said:**
> If you are worried about the warning, I believe you can ignore it, it may be just a notification (can't test here, since I still have an older version of Grub2). Reboot to test if the change took effect.

Also, since it is complaining about non-zero value, and a zero-value is already defaulting to 10 seconds, I think it is (with the new changes in newer version) safe now to set it to zero like you were doing. What I wrote was applicable to the version I am using (and the older ones), maybe it is zero by default for new versions. In any case, it shouldn't hurt if Ubuntu is set as the default OS.

And if you are worried about it detecting XP, I think that can be (should be) ignored as well, since it doesn't matter when the menu is going to bypassed anyway.

However, IF you want (or really need) to disable the detection of XP, just disable the "os-prober" script temporarily -
```
sudo chmod -x /usr/bin/os-prober
```
Then run an "update-grub" again. The os-prober part won't work this time, so XP won't get detected.

To enable the os-prober again -
```
sudo chmod +x /usr/bin/os-prober
```

Yes I tried both re-booting and and also setting both values to zero with no effect. As for os-prober, I think I'll just wait until 14.04 is released next month and then delete the Windows partition and resize my Linux root and home partitions before installing. Thank you so much for your help.

---

### Post by Bashing-om on 2014-03-08
donsy; Hi !

My 2 pounds worth - if it helps:
My grub control file version 13.10 install, multi-booting - with the prescribed alterations not to get those errors !
I do want to see my grub menu at boot.
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0#as per https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2 ##
GRUB_HIDDEN_TIMEOUT_QUIET=false #changed to false from true##
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by donsy on 2014-03-08
That didn't work either. Thanks for your help.

---

### Post by Bashing-om on 2014-03-10
donsy; Hello,

My understanding: to adjust which menu entry boots as 1st by default;
a) find the menu entry number ( numbering starts at 0)
```

sudo grep menuentry /boot/grub/grub.cfg

```
b)grub-set-default - Script to set a default boot entry for GRUB.
```

sudo grub-set-default 2

``` change '2' to your desired menu entry number.
c)Before that will work, the top line in the /etc/default/grub file that looks like 'GRUB_DEFAULT=0' needs to be changed to 'GRUB_DEFAULT=saved'. See Editing /etc/default/grub. Make sure you remember to run 'sudo update-grub' after editing your /etc/default/grub file, for the changes to take effect.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[INDENT]just a bit more
[INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by varunendra on 2014-03-10
Bashing-om,

I think your suggestion is for making Windows the default option, while the OP wants to boot directly into Linux -
>  I would like to keep the partition active for a while yet** boot directly into Linux** without the Grub2 menu and the timeout.

So I think everything is already set as should be, just the timeout or the grub screen is what they wish to avoid.

I believe disabling the os-prober script + update-grub should do the job. Just tried here (on my 12.04.2) and it indeed does that.

However, to get the windows entry back, the os-prober must be enabled again -
```
sudo chmod +x /usr/bin/os-prober
```
..followed by an "update-grub".

I think what they actually want is to keep the entry, just avoid the grub menu, which is doable here on my system, not sure what may be the problem with 13.10.

---

### Post by Bashing-om on 2014-03-10
varunendra;

I am often taken-a-back by what I do not know and what I am trying to learn. However, I would think this procedure will work to make any menu entry the default and setting the "timeout" as '0' would boot that entry with no display of the grub menu (??).

Bunches I still do not know ->
I remain
[INDENT][INDENT]open to learn better
[/INDENT][/INDENT]

---

### Post by varunendra on 2014-03-10
I'm not sure about the behaviour of the three timeout values anymore. From what donsy has posted so far, the version in 13.10 seems to have changed a lot from the version I have.

If you have 13.10 ISO, you can certainly offer much better help than I can. It shouldn't matter which OS the "2nd" one is, so maybe you can experiment yourself on a VM dualbooting Ubuntu/Ubuntu (same or different versions) or Ubuntu/Windows.

It is good that setting the grub_timeout value to "0" now defaults to 10 (otherwise the same problem could arise as I mentioned in my first post). I just can't imagine why skipping the menu should not work as in the older version that I have.

---

### Post by Bashing-om on 2014-03-10
It is true that grub has changed, and it is to be kept in mind that what was may no longer apply.
Try and see what works - kinda deal ? 

I do not have a 13.10 liveDVD to test with - maybe more shame on me - as it is an interim release I just did not make the effort to make one.

UHmmph ! Maybe the reference " [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2) " is not up to date ( as I had thought that was the reference I had used to direct commenting out "#GRUB_HIDDEN_TIMEOUT=0" and changing the true to 'false' in the line "GRUB_HIDDEN_TIMEOUT_QUIET=false") ? Looking over it I do not see the directive now . For my use case my menu is displayed and I no longer have the warnings that " GRUB_HIDDEN_TIMEOUT=0 " has been depreciated.

Let's see what plays out.

---

### Post by donsy on 2014-03-10
I deleted the Windows partition and it works now. Here are my Grub entries:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by varunendra on 2014-03-11
Ouch! I thought you wanted to keep XP for a while. :)

Anyway, if you got what you eventually wanted, please mark the thread as [SOLVED] using the "Thread Tools" link above the top post.

And thanks for posting the current entries, it sure shows me something I wasn't expecting, but as long as it works.. :)

---

### Post by psfal on 2014-03-17
> **donsy said:**
> WindowsXP E0L is next month and I would like to keep the partition active for a while yet boot directly into Linux without the Grub2 menu and the timeout. If I set GRUB_TIMEOUT=0, Grub will still default to waiting 10 seconds. But if I set GRUB_TIMEOUT=1 it works as expected and displays the menu only 1 second. Why won't it work for GRUB_TIMEOUT=0? I make sure to run 'sudo update-grub' after every update. Here is my complete /etc/default/grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
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

How do I remove the Memtest entries from my boot menu? Maybe one of these lines pertains to that but I'm not understanding the language used? I'm debating on removing the recovery mode entries too, since I don't know enough to be able to make use of them in any case...

---

### Post by Bashing-om on 2014-03-17
psfal; Hello ,

I must inquire why you want to hobble the system's functions ?
There is no way to tell when a need may arise to have use of them ( and then maybe not be able to re-enable them if they are).

If it is a case of a crowded menu, removing the old kernels and updating grub will resolve that issue.

Removing boot options/testing in my opinion
[INDENT][INDENT]just not a good thing to do
[/INDENT][/INDENT]

---

### Post by psfal on 2014-03-17
> **Bashing-om said:**
> psfal; Hello ,

I must inquire why you want to hobble the system's functions ?
There is no way to tell when a need may arise to have use of them ( and then maybe not be able to re-enable them if they are).

If it is a case of a crowded menu, removing the old kernels and updating grub will resolve that issue.

Removing boot options/testing in my opinion[INDENT][INDENT]just not a good thing to do
[/INDENT]
[/INDENT]


I already purge old kernels, I have never, in the 5 years I've been using Linux had a need for memtest, and there is nothing I know how to do from recovery mode (If I screw it up I just reinstall, my data is backed up and no issue to replace)... I like a neat and clean grub menu, plus I have a girlfriend who has to constantly ask me which entry to select

---

### Post by Bashing-om on 2014-03-17
psfal; OK;

As you are sure of what you desire - and this procedure is reverse-able -

Grub config/control files are also located at /etc/grub.d :
The file of interest here is "20_memtest86+ "
Try this and see if the result is as expected:
```

sudo chmod -x /etc/grub.d/20_memtest86+

```
To disble the "recovery mode" option and not have it appear, as you surmise.

In the event that you are unsure of how to edit the grub file :
Make a back up of the file to be edited - standard operating procedure -
```

sudo cp /etc/default/grub /etc/default/grub-orig

```
In the text editor edit the file and remove the '#' character at the start of the line: #GRUB_DISABLE_RECOVERY="true"
```

gksudo gedit /etc/default/grub

```
save the file and exit back to terminal.

For the changes to take effect:
```

sudo update-grub

```

Reboot and let's see
[INDENT][INDENT]what it looks like
[/INDENT][/INDENT]

---

### Post by psfal on 2014-03-18
> **Bashing-om said:**
> psfal; OK;

As you are sure of what you desire - and this procedure is reverse-able -

Grub config/control files are also located at /etc/grub.d :
The file of interest here is "20_memtest86+ "
Try this and see if the result is as expected:
```

sudo chmod -x /etc/grub.d/20_memtest86+

```
To disble the "recovery mode" option and not have it appear, as you surmise.

In the event that you are unsure of how to edit the grub file :
Make a back up of the file to be edited - standard operating procedure -
```

sudo cp /etc/default/grub /etc/default/grub-orig

```
In the text editor edit the file and remove the '#' character at the start of the line: #GRUB_DISABLE_RECOVERY="true"
```

gksudo gedit /etc/default/grub

```
save the file and exit back to terminal.

For the changes to take effect:
```

sudo update-grub

```

Reboot and let's see[INDENT][INDENT]what it looks like
[/INDENT]
[/INDENT]


Thanks very much :)
That worked great, I appreciate the assistance

---

### Post by Bashing-om on 2014-03-18
@ psfal; Good deal !

Pleased to be of some small help.

stay tuned and
[INDENT][INDENT]we will have another adventure
[/INDENT][/INDENT]

---


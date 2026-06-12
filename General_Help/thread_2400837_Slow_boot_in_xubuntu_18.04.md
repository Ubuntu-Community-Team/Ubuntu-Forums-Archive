---
title: "Slow boot in xubuntu 18.04"
date: 2018-09-10
forum: General Help
---

### Post by zlinkort on 2018-09-10
I'm running Xubuntu 18.04 as a new install (and only OS) on a Dell Latitude 3189 with an SSD. The computer takes consistently 60-65 seconds between the Dell splash screen and the Xubuntu log-in screen.

After doing some searching online, I updated the /etc/fstab file with the correct UUIDs but that did not improve the boot time.

I have run the "systemd-analyze blame" command and its output is here: [https://pastebin.com/zLfaAbNp](https://pastebin.com/zLfaAbNp). Adding the times on that list comes out to 12.322 seconds, which would be a better start-up time but there is clearly a discrepancy.

I have also run the "dmesg" command and its output is here: [https://pastebin.com/hvMB3fFq](https://pastebin.com/hvMB3fFq). This seems to show a few slowdowns:

```
[    9.920628] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   41.089006] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
```

```
[   43.655846] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   53.592821] wlp1s0: authenticate with ac:84:c6:a3:d0:a2

```

I'm not sure how to address those. Any ideas on how I can fix things? I'm completely new to Linux, so basic answers (and explanations of what I'm doing) would be greatly appreciated.

Thank you!

---

### Post by &amp;KyT$0P# on 2018-09-10
Please post the output from running this command in Terminal -
```
cat /etc/default/grub
```

---

### Post by zlinkort on 2018-09-10
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="" # default "quiet splash"
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

### Post by &amp;KyT$0P# on 2018-09-10
Try changing
```
GRUB_TIMEOUT_STYLE=hidden
```
to
```
GRUB_TIMEOUT_STYLE=menu
```

To apply this change, run
```
sudo update-grub
```

When you next reboot, after you see the Dell splash screen, you should see the GRUB menu instead of 10 seconds of black screen.  You can either wait the 10 seconds it counts down, or just hit Enter to pick the default boot.  After that step, how long does it take to get to the log in screen?

---

### Post by zlinkort on 2018-09-11
Thank you so much for your replies.

After the Dell splash screen disappeared, there was a black screen for 5-6 seconds until the GRUB menu came on. After the GRUB menu disappeared, there were 48-49 seconds until the log-in screen appeared.

---

### Post by ajgreeny on 2018-09-11
When you get to the grub menu quickly hit "e" to edit the boot stanza and remove the quiet splash from the kernel line.

Hit Ctrl+X or F10 (I think, but it will tell you) to boot and it will now be a text boot for this boot only. You should be able to see where the delay occurs.

---

### Post by zlinkort on 2018-09-11
I had updated the /etc/default/grub file to remove the "quiet splash" line; I think that achieved the same result.

The last few lines before it hangs are the following:
```

[    9.2211165] i915 000:00:02.0: fb0: inteldrmfb frame buffer device
Begin: Loading essential drivers ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... WARNING: Failed to connect to lvmetad. Falling back to device scanning.
done.
Begin: Running /scripts/local-premount ... [    9.792683] [drm] RC6 on

```
It then gets stuck there for about 30-31 seconds.

---

### Post by ajgreeny on 2018-09-12
Can I assume from that boot info that you are using LVM formatting of the hard disks/partitions?

I am lost with LVM so if I am right, and you have an LVM system, I will have to remove myself from this thread.

---

### Post by zlinkort on 2018-09-13
Yes, I believe it is LVM. When I was first installing I think I had read that LVM was recommended by some. Would things be better without LVM?

---

### Post by zlinkort on 2018-09-16
> **ajgreeny said:**
> Can I assume from that boot info that you are using LVM formatting of the hard disks/partitions?

I am lost with LVM so if I am right, and you have an LVM system, I will have to remove myself from this thread.

I reinstalled Xubuntu without LVM and my boot time is down to 34-35 seconds!

I  have read people claim to have GNU/Linux boot times in the 10-15 second  range (my old Chromebook was around that time) -- is that achievable in Xubuntu?

Currently the breakdown of my boot process is this:
Screen on -> black screen -> Dell splash screen -> black screen -> GRUB menu starts: 11-12 seconds
GRUB menu: 5 seconds
GRUB ends -> text boot lines -> log-in screen: 17-18 seconds

The output of dmesg is here: [https://pastebin.com/mgbkrXF1](https://pastebin.com/mgbkrXF1)
The output of systemd-analyze blame is here: [https://pastebin.com/mzN8FLGL](https://pastebin.com/mzN8FLGL)

Is there something I can optimize to decrease the boot time? Why is there so much time before GRUB starts? Is this a BIOS problem?

---

### Post by linux4me on 2018-09-16
You've already re-installed without LVM, but just for reference, there is a [bug reported]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230") about the long boot delay and a possible fix if you end up going with LVM.

---


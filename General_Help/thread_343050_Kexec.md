---
title: "Kexec"
date: 2007-01-20
forum: General Help
---

### Post by AndrewBarber on 2007-01-20
Hey has anybody got Kexec up and running on Ubunbtu, if so how?

---

### Post by tbroderick on 2007-01-21
Did you install kexec-tools?

---

### Post by hyperair on 2007-05-06
I did, and I ran the command: 
```

kexec -l /boot/vmlinuz-`uname -r` --append="root=/dev/hdc1 ro splash nmi_watchdog=0"
kexec -e

```

It kernel panicked, complaining about the root option, yet when I start with that root option from Grub it's fine.

EDIT: Turns out I left out the initrd option out. It works fine now, and my computer's running perfectly. This is the code I used which finally worked:
```

kexec -l --append="`cat /proc/cmdline`" --initrd=/boot/initrd.img-`uname -r` /boot/vmlinuz-`uname -r`
kexec -e

```
This must be run either as the root user, or with the command sudo. Hope this helps someone else.

---

### Post by mmendez on 2007-06-02
I am having a problem where when i type ```
kexec -l /boot/vmlinuz-2.6.20-16-generic --append="root=/dev/sda ro quiet splash" --initrd=/boot/initrd.img-2.6.20-16-generic
```
"/dev/sda" being what i get from ```
cat /boot/grub/device.map
``` and "ro quiet splash" from ```
cat /proc/cmdline
```

I get "Undefined symbol: __stack_chk_fail"


any ideas? Thanks

---

### Post by hyperair on 2007-06-04
/dev/hda refers to the hard disk. You must provide it something like /dev/sda# where # is an integer referring to the partition number. Type "mount" and check which device mounts to "/". That'll be the correct one.

---

### Post by mmendez on 2007-06-20
Sorry for not writing back, when on vacation I mean it. I immediately recognized how dumb of a mistake that was but I still get same error. I am attaching a screen shot with what I have tried.

Thanks for the help

---

### Post by hyperair on 2007-06-21
Strange. Very strange. I tried googling with your error message but cannot find anything. Is it possible that the kernel you have loaded at that time does not have kexec extensions? Like a custom compiled kernel? Try "uname -r" to find out. Also, could you copy and paste the command i gave you in my previous post and see if that works?

---

### Post by hyperair on 2007-06-21
Strange. Very strange. I tried googling with your error message but cannot find anything. Is it possible that the kernel you have loaded at that time does not have kexec extensions? Like a custom compiled kernel? Try "uname -r" to find out. Also, could you copy and paste the command i gave you in my previous post and see if that works?

---

### Post by mmendez on 2007-06-21
I did try your command its their in the screen shot, one terminal shows the contents of "/proc/cmdline" and after that in the same terminal the results of "mount".

The bottom terminal has the results of "kexec -l ....." with both of the results from the top terminal passed to "--append" separately.

My kernel is your good 'ol ubuntu stock "2.6.20-16-generic" I have checked the contents of "/boot/config-2.6.20-16-generic" and it has "CONFIG_KEXEC=y"

---

### Post by mmendez on 2007-06-21
maybe it's got something to do with my hardware. I say this because I just finished doing a fresh install of 7.04 on my Acer Ferrari, the only things I have done to it are bcm43x-fwcutter, beryl, and thunderbird, and any updates. I installed kexec-tools carried out the command and it workded like a charm.

Still any suggestions on the other machine would be great. Its a kind of old dell and I am pretty sure everything is stock except for the network card, but that works just fine.

Manny

---

### Post by supernovus on 2008-05-26
Sorry for re-opening this thread, but I figured I'd contribute my "quick-reboot" script, which when used instead of 'reboot' will use kexec to reboot into the newest kernel, using the options from grub.

```

#!/bin/sh

grub_conf() {
    STRING="# $1="
    grep "^$STRING" /boot/grub/menu.lst | sed "s|$STRING||g"
}

KERNEL=`find /boot/ -name 'vmlinuz-*' | sort -n -r | head -n 1`
INITRD=`echo $KERNEL | sed -e 's/vmlinuz/initrd.img/g'`
#KOPTS="`grub_conf kopt` `grub_conf defoptions`"
## New KOPTS method contributed by hyperair
KOPTS=`grep $KERNEL /boot/grub/menu.lst | head -n 1 | sed -e 's|^kernel.*'${KERNEL}'\s*||'`

ACTION="kexec -l $KERNEL --append=\"$KOPTS\" --initrd=$INITRD"

case "$1" in
    -n|-s)
        echo $ACTION
    ;;
    *)
        $ACTION
    ;;
esac

```

Note that this currently uses echo to show you what it would do, you need to do "sudo quick-reboot | sh" to make it execute. EDIT: *No longer necessary, as I have modified the script so by default it just executes. You now need to put -s or -n if you want to see what it would do instead of executing the action.*
I'm sure this should probably be done somewhere else, like in the [RapidReboot spec]("https://wiki.ubuntu.com/RapidReboot").

Anyway, for those who want it. Have fun.

---

### Post by hyperair on 2008-05-26
I believe the correct way to do it would be:
```

quick-reboot | sudo sh

```
This is because the quick-reboot script doesn't actually do anything that requires superuser capability, but sh does, because it's running kexec. quick-reboot merely echoes it out.

I also don't understand why you don't just make it execute the last line instead of echoing it out?

Another thing is that you don't need to provide only one argument to echo by surrounding it using quotes. echo prints everything regardless of how many arguments it takes.

Also, I'd suggest using another method to get KOPTS. 
```

KOPTS=`grep $KERNEL /boot/grub/menu.lst | head -n 1 | sed -e 's|^kernel.*'${KERNEL}'\s*||'`

```

---

### Post by supernovus on 2008-05-26
To hyperair: In my latest version, I have removed the echo part, that was for testing, to make sure that it was picking the correct version. I had also misplaced the sudo, as my initial test had been in a sudo -i environment (yes, I know, bad habits die hard).

Anyway, I have now moved it to /usr/local/sbin/quick-reboot and modified /etc/init.d/reboot using LucaFalavigna's comment from the RapidReboot spec, so that the do_stop function looks like this:

```

    log_action_msg "Will now restart"
    if [ -x /usr/local/sbin/quick-reboot ]; then
        /usr/local/sbin/quick-reboot
    fi
    reboot -d -f -i

```

I have tested it using both a normal "reboot" selection, and using the blue "you must reboot to complete updates" icon, and it works great.

It's not elegant, and I'm sure the developers will come up with something better for the RapidReboot spec, but it works now, for those who want such a thing.

YMMV.

---

### Post by hyperair on 2008-05-26
Perhaps you should put the "reboot -d -f -i" into an else block instead. It seems like an exclusive or condition.
```

log_action_msg "Will now restart"
if [-x /usr/local/sbin/quick-reboot]; then
  /usr/local/sbin/quick-reboot
else
  reboot -d -f -i
fi

```

---

### Post by supernovus on 2008-05-26
> **hyperair said:**
> Perhaps you should put the "reboot -d -f -i" into an else block instead. It seems like an exclusive or condition.
```

log_action_msg "Will now restart"
if [-x /usr/local/sbin/quick-reboot]; then
  /usr/local/sbin/quick-reboot
else
  reboot -d -f -i
fi

```

I thought so as well, however, in the [RapidReboot spec]("http://https://wiki.ubuntu.com/RapidReboot"), in the Code section, LucaFalavigna notes that you do not need to include the else block, as if kexec succeeds, it will never reach the reboot line, however if it fails, the system will still reboot normally.

This script is obviously a quick hack. It could be greatly improved by putting in stuff like the ability to use the existing command line (taken from /proc/cmdline) instead of the default options, but honestly, I think for the few times that reboot is really necessary, it's good enough.

---

### Post by hyperair on 2008-05-26
I was thinking of posting about the whole /proc/cmdline thing, but decided against it because of the following scenario:
1. User boots up computer with a custom one-time cmdline (not in grub)
2. User updates kernel
3. User wants to rapidreboot, with a new command line. 

The KOPTS line I posted will search the menu.lst to find the "kernel /boot/vmlinuz-bla <kopts here>" and filter out the unnecessary parts. I think it's cleaner than the method you posted in your script.

---

### Post by supernovus on 2008-05-26
> **hyperair said:**
> I was thinking of posting about the whole /proc/cmdline thing, but decided against it because of the following scenario:
1. User boots up computer with a custom one-time cmdline (not in grub)
2. User updates kernel
3. User wants to rapidreboot, with a new command line. 

The KOPTS line I posted will search the menu.lst to find the "kernel /boot/vmlinuz-bla <kopts here>" and filter out the unnecessary parts. I think it's cleaner than the method you posted in your script.

I have replaced my KOPTS line in my script with the method you're using. I guess that's a lot better than using my kludge to extract the update-grub comments. I'll update the script in the original message to reflect that change. Thanks!

---

### Post by hyperair on 2008-05-26
You're welcome =)

---


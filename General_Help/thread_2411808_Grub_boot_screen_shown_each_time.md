---
title: "Grub boot screen shown each time"
date: 2019-02-04
forum: General Help
---

### Post by ordak on 2019-02-04
Hi,

I use Ubuntu 18.04 fully updated. After a few days ago, each time I turn on this laptop, I see Grub boot menu. What can I do ?

---

### Post by jeremy31 on 2019-02-04
Post results for ```
cat /etc/default/grub
```

---

### Post by ordak on 2019-02-05
> **jeremy31 said:**
> Post results for ```
cat /etc/default/grub
```

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

### Post by ordak on 2019-02-11
It still happenes, BUMP.

---

### Post by #&amp;thj^% on 2019-02-11
Here's what yours looks like by default:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Make it look like this:
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```

After this run:
```
sudo update-grub
```
On your next reboot, grub should not show.

---

### Post by dmnur on 2019-02-11
There was a regression in new GRUB packages: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1814403](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1814403)
It's fixed now. You probably just need to upgrade once more.

Threads describing the same issue:
[https://ubuntuforums.org/showthread.php?t=2412153](https://ubuntuforums.org/showthread.php?t=2412153)
[https://ubuntuforums.org/showthread.php?t=2412269](https://ubuntuforums.org/showthread.php?t=2412269)
[https://ubuntuforums.org/showthread.php?t=2412335](https://ubuntuforums.org/showthread.php?t=2412335)

If upgrading will help, please mark your thread as solved. See [instructions](https://ubuntuforums.org/showthread.php?t=726150&p=4527051#post4527051).

---

### Post by Dennis N on 2019-02-11
The experts say you couldn't get to the menu when needed with a one OS system if you have UEFI. There is an additional problem if you use LVM as well.

Explained here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0)

From now on, it sounds like you always will get a menu (unless you installed a single OS on a BIOS system!)

---

### Post by #&amp;thj^% on 2019-02-11
> **Dennis N said:**
> The experts say you couldn't get to the menu when needed with a one OS system if you have UEFI. There is an additional problem if you use LVM as well.

Explained here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0)

From now on, it sounds like you always will get a menu (unless you installed a single OS on a BIOS system!)

1st I've seen that, Thanks.>>> keeping this in my back pocket:
```
inxi -Mxxx
Machine:
  Type: Laptop System: LENOVO product: 2349M88 v: ThinkPad T430 
  serial: <root required> Chassis: type: 10 serial: <root required> 
  Mobo: LENOVO model: 2349M88 serial: <root required>**_ UEFI [Legacy]:_** LENOVO 
  v: G1ETB8WW (2.78 ) date: 09/19/2018 

```

---

### Post by ordak on 2019-02-12
> **1fallen said:**
> Here's what yours looks like by default:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Make it look like this:
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```

After this run:
```
sudo update-grub
```
On your next reboot, grub should not show.

I did this, but grub menu was seen again.

---

### Post by ordak on 2019-02-12
> **Dennis N said:**
> The experts say you couldn't get to the menu when needed with a one OS system if you have UEFI. There is an additional problem if you use LVM as well.

Explained here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/0)

From now on, it sounds like you always will get a menu (unless you installed a single OS on a BIOS system!)

How can I change installation, keeping my HD intact ?

---

### Post by #&amp;thj^% on 2019-02-12
> **ordak said:**
> I did this, but grub menu was seen again.

As Dennis N and i was discussing, They just flat want you see a grub-menu at boot.
I took a very harsh method here for mine, **and this may not work on all machines**. MY idea came from: [https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks#Hide_GRUB_unless_the_Shift_key_is_held_down](https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks#Hide_GRUB_unless_the_Shift_key_is_held_down)
I added these two lines to "/etc/default/grub" 
```
GRUB_FORCE_HIDDEN_MENU="true"
GRUB_DISABLE_SUBMENU=y
```
Now that would force "HIDDEN_MENU=" to true, and "GRUB_DISABLE_SUBMENU=y" is for users with more than one kernel.(This disables that choice)
So just to be sure we can still get a menu with the "shift key" at boot-up, I set a script in:
```
sudoedit /etc/grub.d/31_hold_shift
```
the contents in that file are exactly as follows:
Found here: [https://gist.githubusercontent.com/anonymous/8eb2019db2e278ba99be/raw/257f15100fd46aeeb8e33a7629b209d0a14b9975/gistfile1.sh](https://gist.githubusercontent.com/anonymous/8eb2019db2e278ba99be/raw/257f15100fd46aeeb8e33a7629b209d0a14b9975/gistfile1.sh)
```
#! /bin/sh
set -e

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"
source "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {

  if [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then 
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" 
"${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

  adjust_timeout

    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
```
Then I set the permissions with:
```
sudo chmod a+x /etc/grub.d/31_hold_shift
```
Now I updated "grub" to set it.
```
sudo update-grub
```
Now remember this may not work for everyone! Good Luck.

---

### Post by Dennis N on 2019-02-24
Looking at virtual machines with a single OS, I now notice you only get the grub menu when you use LVM. I don't see the grub menu when using BIOS or UEFI installs to a partition in the single OS situation.

---


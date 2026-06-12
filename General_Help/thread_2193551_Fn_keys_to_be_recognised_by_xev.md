---
title: "Fn keys to be recognised by xev?"
date: 2013-12-13
forum: General Help
---

### Post by dorigoluca on 2013-12-13
Hi guys,

does someone know if there is a way to have the Fn keys of my laptop to be recognised by the command xev? (I want to remap them with xmodmap becouse some other keys on my keyboard are dead)

I know they do work because I can use them to change volume etc. but nothing appears when i run the xev command...

tyvm! :)

---

### Post by tgalati4 on 2013-12-13
That is typically because the ACPI system (in BIOS) intercepts the keys and acts on them, so they are not visible to the X-server.  What model is the laptop?

You can sometimes use scripts to reassign the behavior of these keys, but you may loose some functionality.

You can use the *acpi_listen* command to see what is happening within the ACPI system.

As you have discovered, only keys seen by *xev* are programmable as hot-keys without a lot of extra effort.

For programming keys not seen by either xev or acpi_listen, you would need to use the *setkeycodes* system.

```
man setkeycodes
```

Search the forum for different ways it is used--typically to activate unrecognized multimedia keys on extended keyboards.  For instance:  [http://ubuntuforums.org/showthread.php?t=921870&highlight=setkeycodes](http://ubuntuforums.org/showthread.php?t=921870&highlight=setkeycodes)

---

### Post by dorigoluca on 2013-12-13
Hi, thanks for the answer.

my laptop is a samsung X420.

When I run acpi_listen and press the Fn key it doesn't say anything, however when I do Fn-esc I get this:

```


button/sleep SLPB 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000


```

all other combinations of Fn-something gives me no output in the terminal but sometimes it has effects on the computer (mute, mouse locked, luminosity control, etc.).

Any Idea on what I should do?

thank you !!

---

### Post by tgalati4 on 2013-12-13
Look through all of the scripts in /etc/acpi.  For instance:

When you push power button, this gets executed:

tgalati4@Mint14-Extensa /etc/acpi $ cat power.sh
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then
    exit;
fi

pm-powersave $*

--------------------

To see your current key definitions:

tgalati4@Mint14-Extensa /etc/acpi $ cat /usr/share/acpi-support/key-constants
# Generated from /usr/include/linux/input.h dated Sat Feb  4 14:58:52 GMT 2006
KEY_RESERVED=0
KEY_ESC=1
KEY_1=2
KEY_2=3
KEY_3=4
KEY_4=5
KEY_5=6
KEY_6=7
.
.
.

---------------------

So the sleep button works and the CPU's wake up, that is what acpi_listen is telling you.  Unfortunately, Samsung would have to provide a blueprint for the key definitions for your extra function keys.  IBM/Lenovo, toshiba, ASUS and a few others have provided some keymaps so those keys are defined in /etc/acpi and /etc/acpi/events.

So the first order of business is to make a list of what function keys do not work as expected.

---


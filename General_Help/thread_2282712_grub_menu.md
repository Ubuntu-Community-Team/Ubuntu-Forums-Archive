---
title: "grub menu"
date: 2015-06-16
forum: General Help
---

### Post by eipapp on 2015-06-16
In order for Ubuntu Mate 15.04 to work properly for me I had to amend the grub menu to read:
quiet splash nomodeset
and it works fine as a result.
However, on start-up when I go to edit the grub menu (just making sure all was as it should be) I found the following...
quiet splash nomodeset $vt_handoff
I proceeded to delete that last part ($vt_handoff), updated grub and done!!
Then on next boot it was still there. 
Am I making something out of nothing ?
When I log on and open terminal and type sudo nano /etc/default/grub it doesn't show the $vt_handoff
Curious as to why the conflict, that it shows in one place and not the other. Shouldn't they be the same ?
Why would the changes show in one place and not the other ?

Just askin...............

Bruce

---

### Post by grahammechanical on 2015-06-16
You will find the /etc/default/grub is just one of several files that are used to compose the Grub configuration file, grub.cfg. If you open /boot/grub/grub.cfg in Gedit you will find that $vt_handoff is part of the script that makes up grub.cfg.
> 
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}

grub.cfg references /etc/grub.d/10_linux which has this part of its script

> prefix="/usr"
exec_prefix="/usr"
datarootdir="/usr/share"
ubuntu_recovery="1"
quiet_boot="1"
quick_boot="1"
gfxpayload_dynamic="1"
vt_handoff="1"

It is /etc/grub.d/10_linux that has vt_handoff="1" and not /etc/default/grub

Regards.

---

### Post by kerry_s on 2015-06-16
vt7 is for the gui to run. vt 1->6 is setup to run text terminal.

---

### Post by eipapp on 2015-06-16
What is odd to me, I guess, is that I had to delete the $vt_handoff in order for my machine to boot into Mate 15.04 in the first place. (after replacing it with nomodeset, of course)
So at the end of the day, I guess it really doesn't matter that it's still there.

---


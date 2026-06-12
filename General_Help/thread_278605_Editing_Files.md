---
title: "Editing Files"
date: 2006-10-16
forum: General Help
---

### Post by xptweakerntn on 2006-10-16
basically, i need to edit this file
etc/modprobe.d/aliases
i am the owner and admin, but i don't know how to give myself permission to edit it.
how do i

---

### Post by taurus on 2006-10-16
Open a terminal, Applications -> Accessories -> Terminal, and type

```

gksudo gedit /etc/modprobe.d/aliases
(use the same password that you log in with...)

```

---

### Post by Cene on 2006-10-16
Chmod?

---

### Post by Arby on 2006-10-16
```
sudo nano -w etc/modprobe.d/aliases
```
Should give you what you want. The 'sudo' part lets you act as root/administrator for just this single operation which means you will have permission to read and write this file. 'nano' is the text editor I prefer for this type of job and -w stands for write mode. If you don't have nano installed then you can swap 'nano -w' for gedit

---

### Post by taurus on 2006-10-16
> **Cene said:**
> Chmod?

Don't "chmod" files in /etc!!!  Use "sudo" to edit them...

---

### Post by xptweakerntn on 2006-10-16
well, now i messed up. not bad though, basically, i edited the file, but accidently added something too much, now it is all wrong. where can i find a copy of the original file, or does it matter?

this is what my file looks like

# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off
#alias net-pf-10 ivp6 =========the original line
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore

---

### Post by taurus on 2006-10-16
There should be a copy called /etc/modprobe.d/aliases~.  That's the original copy...

---

### Post by Cene on 2006-10-16
**taurus:**
Sorry, my mistake. I didn't pay much attention to file, and that it was on /etc/. :)

**xptweakerntn:**
There should be an backup file with same name, except ~ in the end of the file.

Edit: I'm slow, taurus was faster. :)

---

### Post by xptweakerntn on 2006-10-16
ok, i don't think i have that backup, but what i do need to do is learn how to delete a file i created, bad_list, in the same place, and where else could i get the original?

---

### Post by Cene on 2006-10-16
Use "sudo rm -rf /path/to/file" to remove files. But be careful, it really deletes the file without asking anything. :)

Backup files don't show up on Nautilus, so you need to change to that directory in terminal (cd /path/to/directory/) and use the "ls" command to show files in there. If you see the backup, you can replace the original with it by typing "sudo mv aliases~ aliases"

If you can't find the backup file, I uploaded mine. You can find it at [http://cene.ath.cx/aliases](http://cene.ath.cx/aliases)

---

### Post by xptweakerntn on 2006-10-16
yep, that all worked!! now, how do i globally disable ipv6?
anyone know?

---


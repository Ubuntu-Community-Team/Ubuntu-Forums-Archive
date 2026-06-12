---
title: "Feisty + vmwareserver + Vista + SEAMLESS how???"
date: 2007-04-25
forum: General Help
---

### Post by kbzona on 2007-04-25
:(  it keeps telling me this:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad.exe" 192.168.0.120:3389 -u admin -p pass
Autoselected keyboard map es
ERROR: connect: No route to host


in vmware im tryed with bridget and host-only networks.... none of them works

PD: admins plz apologize me for posting this on the TIPS/HOWTOS forum :lolflag:

---

### Post by dannymichel on 2007-06-22
Bump?

---

### Post by T0MA on 2007-06-26
try using VirtualBox, here is a [nice how-to]("http://ubuntuforums.org/showthread.php?t=433359&highlight=seamless")

you can use NAT, so skip the part in which it disables the network manager and installs the bridged connection. simply use port forwarding:

VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666

after that you can connect to the vm by localhost:6666

---

### Post by scxtt on 2007-06-26
can you ping 192.168.0.120 to begin w/?

---


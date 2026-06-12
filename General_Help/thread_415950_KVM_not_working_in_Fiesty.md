---
title: "KVM not working in Fiesty"
date: 2007-04-20
forum: General Help
---

### Post by neoncode on 2007-04-20
Okay I have a CPU comptable with visualisation(an Intel Core 2 Duo E6600) so I installed kvm, qemu and qemu-launcher. Then ran 

```

sudo modprobe kvm-intel
sudo chmod 777 /dev/kvm

```

And after I figured out the command line(with some help from qemu launcher) I wanted to test it so I ran:

```

kvm -boot d -snapshot -m 128 -hda '/home/neoncode/Virtual/test.img' -cdrom  '/home/neoncode/MyDownloads/ISOimage/kubuntu-7.04-desktop-i386.iso' -net nic,vlan=0 -net user,vlan=0 -localtime -soundhw sb16 -k en-gb  

```

And it core dumps and exits... Can anyone help me? Did I do anything wrong?
Oh and this command works under standard qemu(slowly...)... so it's not that...

---


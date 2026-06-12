---
title: "Ubuntu 12.04 not present in virt-install library"
date: 2013-07-08
forum: General Help
---

### Post by ptc61891 on 2013-07-08
I'm trying to use virt-install to create an Ubuntu 12.04 image 'ubuntuprecise' is not available in the virt-install --os-variant list:


virt-install --virt-type kvm --name precise --ram 1024 --cdrom=/data/isos/precise-64-mini.iso --disk 
/tmp/precise.qcow2,format=qcow2 --network network=default --graphics vnc,listen=0.0.0.0
 --noautoconsole --os-type=linux --os-variant=ubuntuprecise

ERROR    OS variant 'ubuntuprecise' does not exist in our dictionary for OS type 'linux'

These are the available variants.

sles10               : Suse Linux Enterprise Server
ubuntuoneiric        : Ubuntu 11.10 (Oneiric Ocelot)
ubuntunatty          : Ubuntu 11.04 (Natty Narwhal)
ubuntumaverick       : Ubuntu 10.10 (Maverick Meerkat)
ubuntulucid          : Ubuntu 10.04 (Lucid Lynx)
ubuntukarmic         : Ubuntu 9.10 (Karmic Koala)
ubuntujaunty         : Ubuntu 9.04 (Jaunty Jackalope)
ubuntuintrepid       : Ubuntu 8.10 (Intrepid Ibex)
ubuntuhardy          : Ubuntu 8.04 LTS (Hardy Heron)
virtio26             : Generic 2.6.25 or later kernel with virtio
generic26            : Generic 2.6.x kernel

Is there a way to add the variant to the the list or update it?

---


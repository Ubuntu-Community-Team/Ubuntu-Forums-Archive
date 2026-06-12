---
title: "ubuntu 20.04.2 veracrypt not working?"
date: 2021-03-23
forum: General Help
---

### Post by lenny444 on 2021-03-23
just get asked for admin password every once in a while when attempting to mout partition

just come from 18.04, im encrypting my personal files my laptop on a partitioned sdd into 2 parts.

encrypting a 2nd partition NOT a container.

i have the ubuntu 2004 veracrypt version installed briefly tried alternate newer and older versions, does not seem to make a difference.

ubuntu is minimal install as is an older laptop but still works ok.

apparmor apparmor-utils apparmor-profiles installed although tried removing them as well, does not seem to make a difference.

any help?

thank you.

lenny

---

### Post by CelticWarrior on 2021-03-23
Can you please describe the problem with some detail?
What are you trying to achieve, how are you doing it, what is the expected result and what happens instead?

---

### Post by lenny444 on 2021-03-23
hi,

im not how i can describe it in anymore detail than i already did.

using ubuntu 20.04.4
installed veracrypt for ubuntu 20.04 gui version
ubuntu is mininal install (is some dependant missing for encryption?)
apparmor is installed (not sure if that makes a difference tried with and without)
install is on ssd mbr method.
sda1 is ubuntu (no swap partition)
sda2 is blank space

gparted sda2 into fat32 tried both at a primary partition and logical partition method

veracrypt did encrypt partion sda2, ext4, partition only openable in linux option, files over 4gb option.

all that happens is constantly asks sys admin password on mount every 30 seconds.

dont understand why it wont work?

any help?

thank you

---

### Post by lenny444 on 2021-03-23
*update veracrypt has a automount option, i was using that. but if i point at a location for the partition /dev/sda2, then it finds it?

im thinking that this is something to do with doing a minimal ubuntu install, as disks did not work for ever formating, i had to install gparting.

also i could not do luks encryption even after gparted install through disks.

could anyone tell me what do i need to install that is not included with minimal install that is included with a full install that is causing problems with hdds formatting and encrypting?

i can see this coming that im going to have do a fdisk and full install and remove all the bloat that i dont need. just thought it would be easier to do a minimal install and install stuff i use rather than the other way.

but please anyone help

thank you 

LUKS error from disks "error creating partition" on /dev/blah.. failed to meet partition size on device on /dev/blah... (udisks-error-quork, 0)

---


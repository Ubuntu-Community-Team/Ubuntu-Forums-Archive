---
title: "Force /dev/sdX? to remain?"
date: 2008-05-06
forum: General Help
---

### Post by tbeehler on 2008-05-06
Hello all,

I have Ubuntu server 8.04, and I am running mdadm with 4 drives as well as the system drive.  It looks like below

/dev/sda1 - 500gb Raid 5
/dev/sdb1 - 500gb Raid 5
/dev/sdc1 - 500gb Raid 5
/dev/sdd1 - 500gb Raid 5
/dev/sde1 - 120gb system drive

What happens is, is that when I remove a drive to test the raid array, the "drive letters" get all screwy.

So, for example, if I remove /dev/sda1 and reboot (testing failures)

it becomes:

/dev/sda1 - 500gb Raid 5
/dev/sdb1 - 500gb Raid 5
/dev/sdc1 - 500gb Raid 5
/dev/sdd1 - 120gb system drive

Which sends mdadm into a hissy fit and won't rebuild my array.  When I put the drive back, it's like it sees it's previous drive failure and refuses to rebuild.

So my question is, is there a way to say /dev/sde1 is ALWAYS the 120gb system drive, regardless of drives that are present when the machine is up?  Thanks for all your help in advance!

---

### Post by fjgaude on 2008-05-06
mdadm raid does not rely on the drive names to assemble an array, but upon the superblocks of each drive.

When you remove a drive for testing, can you use the command:

```
sudo mdadm --assemble --scan
```

to have it come up again, after a reboot?

---

### Post by tbeehler on 2008-05-06
> **fjgaude said:**
> mdadm raid does not rely on the drive names to assemble an array, but upon the superblocks of each drive.

When you remove a drive for testing, can you use the command:

```
sudo mdadm --assemble --scan
```

to have it come up again, after a reboot?

Ok I think I may have it fixed.

What I was doing wrong was, I would take out one of the 4 drives, and it would work ok, then I would put it back, and take out the next drive, etc.  Dumb thing, I know. :)  But it did suddenly start working regardless of drive /dev assignment once I took out the "array= /dev/sda1," etc information from the /etc/mdadm/mdadm.conf file.

Thanks for your help!

---

### Post by fjgaude on 2008-05-09
I think I understand. My mdadm.conf shows this:

# definitions of existing MD arrays
ARRAY /dev/md32 level=raid5 num-devices=4 UUID=de932348:04ff8763:10c4c696:4837c677

Always use --assemble --scan while changing out motherboards and the like, to use an assisting array. Install mdadm and then do the manual --assemble --scan without needing a mdamd.conf file at all.

Glad you are moving along with software raid.

---

### Post by tbeehler on 2008-05-09
> **fjgaude said:**
> I think I understand. My mdadm.conf shows this:

# definitions of existing MD arrays
ARRAY /dev/md32 level=raid5 num-devices=4 UUID=de932348:04ff8763:10c4c696:4837c677

Always use --assemble --scan while changing out motherboards and the like, to use an assisting array. Install mdadm and then do the manual --assemble --scan without needing a mdamd.conf file at all.

Glad you are moving along with software raid.

Thank you so much for all your help and advice!  The one thing that lead me to choose software raid with mdadm, was the ability to be able to move the array over to another machine if something failed.  That's a BIG plus in my book. :)

---

### Post by fjgaude on 2008-05-09
The UUID that mdadm makes of the array is not the same UUID you get from using, say **blkid /dev/md0**... just a note.
Don't use the mdadm UUID to mount arrays or put into /etc/fstab. They will always mount with the drive name, /dev/md0 or whatever you gave it the first place.

---

### Post by tbeehler on 2008-05-13
> **fjgaude said:**
> The UUID that mdadm makes of the array is not the same UUID you get from using, say **blkid /dev/md0**... just a note.
Don't use the mdadm UUID to mount arrays or put into /etc/fstab. They will always mount with the drive name, /dev/md0 or whatever you gave it the first place.

Thanks!  Good to know!  I have taken out the UUID and all appears to be working properly.  Thanks again for all your help, I appreciate it!

---


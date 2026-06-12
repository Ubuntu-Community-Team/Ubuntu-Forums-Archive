---
title: "Making sure external HDs boot the same"
date: 2008-04-19
forum: General Help
---

### Post by tafarus on 2008-04-19
Hi all,
I've got two external USB HDs and ubuntu seems to randomly swap between the two when it names one 'disk' and the other 'disk1'. By that I mean if i restart my comp it'll sometimes swap the two which breaks all sortsa stuff (other programs which look for like '/media/disk-1/foo' when now after a reboot it's '/media/disk/foo') is there any way to force ubuntu to be consistent?

Thanks in advance!

---

### Post by Wandering on 2008-04-19
Why not give each disk a name, then Ubuntu will label them with the name?

---

### Post by tafarus on 2008-04-19
I seem to get 'operation not supported by backend' errors?

---

### Post by dsnyders on 2008-04-19
Ubuntu can also mount by the UUID number of the drive. In fact, that's the purpose of the UUID number, so that no matter what device number the drive gets assigned, it can still be mounted at the same mount point.  Interestingly, a UUID is the same length as an IPv6 address.

---

### Post by tafarus on 2008-04-19
Cool, sounds like a plan... Now for the completely ignorant among us *cough me cough* how would I go about making sure it mounts it the same way twice using this UUID?... =)

---

### Post by dsnyders on 2008-04-20
Modify your /etc/fstab.  Here's a sample from mine showing UUID usage:

#/dev/hda7                                                                   /var/backup     ext3            defaults        0       2
UUID=1eb8299b-31e6-4987-b1bd-fe6f46ae101a       /var/backup     ext3            defaults        0       2

The first line is a comment showing the original  content of the line.  The second is the equivalent using the partition's UUID.

The UUID can be found by issuing the following command:

sudo vol_id /dev/sda1

You'll have to substitute your own device for /dev/sda1

More details can be found <a href="http://linux.byexamples.com/archives/321/fstab-with-uuid/">here</a>.

---

### Post by tafarus on 2008-04-20
Thanks! I'll give it a shot later today, you guys on the ubuntu forums are great for newbies like myself!

---


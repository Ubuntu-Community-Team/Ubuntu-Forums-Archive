---
title: "mdadm nested raid recovery"
date: 2007-06-28
forum: General Help
---

### Post by evillawngnome on 2007-06-28
Greetings all.

I am on the verge of freaking out becausemy 1TB fileserver went down today when the power went out. Here is an overview of my setup:

There are four 500GB sata hard disks:
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd

All of these come up just fine. There are two RAID 1 arrays that are used to make up a RAID 0 array:

/dev/md0
      /dev/sda
      /dev/sdc

/dev/md1
      /dev/sdb
      /dev/sdd

/dev/md2
     /dev/md0
     /dev/md1

The two RAID1 devices come up fine, but they wont assemble into the RAID0 device like they should:

```

root@Maximus:~# mdadm -A /dev/md2 /dev/md0 /dev/md1
mdadm: superblock on /dev/md1 doesn't match others - assembly aborted
root@Maximus:~#  mdadm -A --force --update=resync /dev/md2 /dev/md0 /dev/md1
mdadm: superblock on /dev/md1 doesn't match others - assembly aborted


```

The only softraid i have any experience with is solaris' disksuite, so i'm kind of hurting on this one. ANY advice or help at all would be MUCH appreciated.

---

### Post by kidders on 2007-06-30
Hi there,

When I saw this thread, I really didn't want to leave you without *some* kind of answer for any longer than you've waited already. I'm afraid I don't have very much of a positive nature to say though ... you see, the trouble with RAID 0 is that, since there's no redundancy, losing *any* of an array generally costs you the whole thing.

Having said that, I'm having trouble imagining specifically what kind of failure would leave your underlying RAID1 arrays intact, while leaving the uppermost (RAID 0) array somehow inconsistent. The only things I can come up with are...
[LIST]
[*]You accidentally jumbled up /dev/sd[a-d], and now both your RAID 1 arrays contain the same data.
[*]The superblock of one of your RAID 1 arrays really is damaged.[/LIST]The output of **mdadm --examine /dev/md0** and **mdadm --examine /dev/md1** would be interesting. It *should* give some insight into what damage has occurred.

In general terms though, you should switch away from RAID 0 as a matter of urgency ... it's really unsafe!

---


---
title: "Need help with ZFS backups"
date: 2017-07-06
forum: General Help
---

### Post by courtney2 on 2017-07-06
I have been using ZFS as my filesystem for a while now and have been loving using it for regular data scrubs with my mirrored zpool, but I have been wanting to use a more effective solution for backing up, so I want to return to my long-deserted venture of send/receive snapshots for backups to an external HDD. Currently I think my backup is working as it should, but my trouble seems to be with restoring these backups. Here is what I have done so far:

Creating snapshots:
sudo zfs snapshot -r tank@`date +"%Y-%m-%d"`

For my first send/receive to my external HDD (with a zpool called backups):
sudo zfs send -R tank@2017-06-30 | sudo zfs receive -vu backups

Then for my incrementals, I did 2 as such to get the ball rolling for my testing, here is what I did:
sudo zfs send -Ri tank@2017-06-30 tank@2017-07-01 | sudo zfs receive -vu -F backups

When I do a "zfs list -t snapshot" I see my zpool with all its subvolumes, along with everything tagged with an @2017-06-30 and a @2017-07-01 respectively. My filesystem layout looks kind of like this in terms of my zfs subvolumes:

tank
|
| -- dir1
| -- dir2
| -- diir3
|      | -- dir3A
| -- dir4
       | -- dir4A
       | -- dir4B

I can't seem to get my restore from my backups zpool to work right. I did a zpool export from my main machine and did a zpool import to my test machine and started by testing my older snapshot. I found that doing this:

sudo zfs send backups@2017-06-30 | sudo zfs receive tank

doesn't work, along with trying a zfs -R send. So because of that I did a send/receive with the template above for dir1, dir2, dir3, dir3A, dir4, dir4A, and dir4B and it all appeared to send the data over but then I went to look at their locations at tank/ and the directories were empty. I'm pretty certain the data is being sent over because the snapshot listing shows the proper amount of storage used, and each data stream took the time I expected it to take. Can someone help me get this send/receive down? I've scoured the forums and FreeBSD forums and can't seem to get something that works for my case

---

### Post by ariek on 2017-07-15
I know this is not an answer to your question, but I would like to point out a script called [**zrep**]("http://www.bolthole.com/solaris/zrep/"). This a great tool that simplifies the send/receive tasks, an gives you great control over backups.

---


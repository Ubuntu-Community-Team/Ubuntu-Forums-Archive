---
title: "bind Failure in fstab"
date: 2019-10-20
forum: General Help
---

### Post by OriTheEep on 2019-10-20
Ubuntu 16.04

Running out of disc space (what a surprise) led to the purchase of a USB drive.

The single volume thereon has been labelled Overspill and is mounted (seemingly successfully) by the following entry in fstab

UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx        /media/tom/Overspill  ext4    rw,user,auto,noexec 0       0

The least intrusive method of making use of the extra space would, from the digging around I've done, be to move the most populated folders of /home/tom/Sharing, which is shared on the local network via nfs, to this drive and then mount the transported folders back into their original position using bind in fstab as follows:

/media/tom/Overspill/Podcasts        /home/tom/Sharing/Podcasts  none    bind 0       0

I'm convinced that this should work but, when tried, what this machine and the network sees in /home/tom/Sharing/Podcasts is an empty folder, Podcasts, bearing the same modification date as the Podcasts folder it is mounted in. The folder I am attempting to mount is populated.

I have rebooted several times with the same results.

I have to admit that, whilst working all this out, I was, for various domestic reasons, unable to pay proper attention to what I was doing and made a number of very silly mistakes, some of which may be preserved in possible intermediate files between fstab and the actual process of mounting.

It is also entirely possible that there is a silly mistake still there.

Can anybody spot it for me, please?

Thanks.

---

### Post by Dennis N on 2019-10-20
The problem is, if you use a folder as a mount point, the existing contents of that folder temporarily disappear from view and are not available until the mounted folder is unmounted.

---

### Post by OriTheEep on 2019-10-20
Thanks for reading and answering, Dennis.

I do know about that and it isn't really the problem: The point is that the /home/tom/Sharing/Podcasts folder, which should show after mounting all the best that Auntie Beeb has to offer, has only an image of itself to display.

---

### Post by Dennis N on 2019-10-20
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/tom/Overspill ext4 rw,user,auto,noexec 0 0
```
This mounts Overspill, not Podcasts. To do bind mount, you must mount this previously mounted folder, Overspill.
```
/media/tom/Overspill /home/tom/Sharing/Overspill none bind 0 0
```
I think should be correct. Again, you can't bind mount Podcasts since it was not mounted by the fstab command.

---

### Post by OriTheEep on 2019-10-20
Thanks for staying with me.

I should perhaps explain better. Overspill is the hopefully sufficiently large (2TB) drive which, at the end of the exercise, will have had transferred over to it all the most populous folders from /home/tom/Sharing. Each of these folders will then be mounted back to its former position within /home/tom/Sharing, to avoid causing any disruption to the overall structure of the Sharing folder as seen by the other machines on the network. This whole business needs to be quite invisible to them.

I started with the Podcasts folder (why not?) and immediately became unstuck in the way described.

I've been doing a little more digging myself and have found that my suspicion that fstab is no longer the completely system defining document it used to be. However, discovering how it has been partially replaced has not been so easy. Ongoing, as and when I get a minute or two.

In the meantime, largely because I know how fruitless such searches can be, I am rather hoping that someone who knows will save me a lot of time and effort :)

---

### Post by Dennis N on 2019-10-20
> Each of these folders will then be mounted back to its former position within /home/tom/Sharing, to avoid causing any disruption to the overall structure of the Sharing folder as seen by the other machines on the network. This whole business needs to be quite invisible to them.

Why don't you just use symbolic links to the new folder locations? The structure of the Sharing folder will look the same.

---

### Post by OriTheEep on 2019-10-20
Sadly, symlinks don't function when it is attempted to share them with other machines over a network. This is the only method which will do and indeed does that. At least that part of things works - all the machines on the network can see the duplicate of the Podcasts folder within the (errr...) Podcasts folder of Sharing.

---

### Post by Dennis N on 2019-10-20
Time for our experts to jump in. Wait and maybe one of them can give better advice.

---

### Post by Skaperen on 2019-10-20
> **Dennis N said:**
> The problem is, if you use a folder as a mount point, the existing contents of that folder temporarily disappear from view and are not available until the mounted folder is unmounted.

and you can't put any new files in that covered-over folder, either.

---

### Post by Skaperen on 2019-10-20
if you do a mount of a file system (call it B) into the middle of another file system (call it A) exporting A over NFS will not include B.  in order to export 2 disks over NFS you must have 2 export statements and every host mounting them must do 2 mounts to get both.  and some OSes (MS Windows, OS/2, DOS) don't support mounting within to re-create the same structure.

---

### Post by OriTheEep on 2019-10-20
I am grateful that you took the trouble to try and help. Hopefully, when and if a solution is uncovered, having posted here will help others with the same sort of trouble.

---

### Post by OriTheEep on 2019-10-20
Your first post is worth saying, I suppose, but if there is a relevancy here, I've been too stupid to see it.

However I think I need to ponder a bit about your second post.

As I stated somewhere above, this computer and the remainder of the network can see this unexplained folder apparently lying within itself, but not indefinitely nested. If that is because I am barking completely up the wrong tree here then I need to renew my researches about this.

Arguments against this being the case are that it was an internet search that threw this technique up as a solution to what seemed to be precisely the problem I have. No mention was made of requiring your 2 mounts.

I wasn't silly enough to mount over the original /home/tom/Sharing/Podcasts folder. That got a new name and a substitute put in place for the purposes of this exercise.

I have some experiments to make. I'll report back after I've made them but the machine is busy with a long job at the moment so I won't be able to reboot for a while. Hopefully it is possible to umount a mount made in fstab otherwise it'll be much later.

---

### Post by OriTheEep on 2019-10-20
Once again free to reboot the computer, I commented out the following line in fstab:

> /media/tom/Overspill/Podcasts        /home/tom/Sharing/Podcasts  none    bind 0       0

I then rebooted then took out the comment character. Rebooted again and all seems well as far as this computer seeing /media/tom/Overspill/Podcasts in /home/tom/Sharing/Podcasts is concerned.

As this was the prime motivation behind this post, I suppose I must mark it Solved without understanding what actually went wrong.

That leaves the matter of exporting over the network. Looks like I'll have to follow Skaperen's advice, which makes the whole thing rather messy.

I am quite convinced that the contents of /media/tom/Overspill/Podcasts was visible over the network in /mnt/Sharing/Server/Podcasts before. It clearly isn't now so perhaps I should reduce my cheese consumption?

Thanks to all who contributed and I do feel slightly guilty about this. Sorry.

---


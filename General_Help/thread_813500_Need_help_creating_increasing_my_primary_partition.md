---
title: "Need help creating increasing my primary partition(gParted)"
date: 2008-05-30
forum: General Help
---

### Post by Truckerpunk on 2008-05-30
First of all please don't be scared off but all the text... Perhaps the solution to my problem isn't that difficult...

So I underestimated the space I needed for Ubuntu. It's only on a drive on about 10Gb, witch is absolutely  to small. The good thing is that I have 30Gb of free space that I want to expand the drive with. I got myself the gParted liveCD and thought this would be easy-piecey... I was wrong. My Ubuntu install is loctated on a primary drive(as far as I've come to learn), and the other partitions I have are all extended. I can easily resize the extended partitions... But I can't add some free space from the extended drives to my primary. And when I use gParted and create a new ext3 drive from unallocated space it won't let me choose "primary   partition". So I basically need help to transfer free extended space to my primary partition. Right now I'm pretty much stuck.... and I would hate to reinstall Ubuntu all together... Any help is appreciated.

---

### Post by abhiroopb on 2008-05-30
If I had a visual image of this it would be easier for me. Could you take a screenshot of gparted and post it on here?

---

### Post by Truckerpunk on 2008-05-30
Here are the images. So what I want to do is increase the boot partition with the approx. 30Gb of unallocated space. But when I create a new partition, I can't choose to make it a primary partition, witch I think it need to be for me to be allowed to transfer the space to the boot partition. I can only choose logical partition. Thanks for the fast reply... And it would be sweet if you had a solution to this.

---

### Post by abhiroopb on 2008-05-30
To clarify what you want:
1. ext3 partition with current 10gb + 30gb 
2. Linux swap
3. Rest for ntfs.

Can you erase the extended partition and start again? Or do you need whatever is on the ntfs? This would be the easiest thing to do. Erase the extended partition. Add whatever you want to the current boot partition, and then create an extended partition for the swap space.

---

### Post by Truckerpunk on 2008-05-31
The extended partition is filled with a lot of important stuff from the hideous old days when I ran MS Windows (Pheeew.. Good thing that has ended). It would by far ease my trouble if it wasn't necessary to kill it off.  But you've gotten it correctly... What you describe is exactly what I want to do. If there aren't an easy way 'round letting the NTFS drive survive then I could kill it, but as said it would be the least painful if I didn't have to.Once again I appreciate your help.

---


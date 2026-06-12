---
title: "Switching to Btrfs; separate partitions for root and home?"
date: 2023-05-19
forum: General Help
---

### Post by Advait on 2023-05-19
Newbie here. I'm using Ubuntu 22.04 ext4 on my laptop. I have a simple setup. All my data is on my main drive and I've got plenty of free disk space. And I do daily backups to USB connected external HDDs.

I'm considering switching to Btrfs cuz Btrfs snapshots are super cool (or so I hear). And Btrfs has become stable. 

When I switch, should I use separate partitions for home and root? Or keep them in the same partition? Why one or the other?

My newbie brain thinks separate partitions cuz that will give me flexibility to snapshot both or only one partition as needed for different backup situations. 

Am I missing some important reason to put them on only one partition?

So let me know which you think is best and why.

Thanks in advance from a newbie.

(Update: I checked with GPT4 and it suggested something called 'Btrfs subvolumes'. I'm not familiar with them. I'll research. Are subvolumes the best solution?)

---

### Post by TheFu on 2023-05-19
You have much research about volume management and how that relates to BTRFS to do before making any decisions. If you haven't used a volume manager before, prepare for your mind to be blown.  Wrap your head around that.

if it were me, I'd do a standard install, use that and play around with it for 6 months before blowing it away (if needed) and installing with storage setup the way I like.  I think you'll see some powerful stuff in the volume management and may not need to start over.

Regular partitions have always been a little too rigid.

Do you use virtual machines?  If so, be certain to look up what that means under BTRFS.

---

### Post by Advait on 2023-05-20
> **TheFu said:**
> You have much research about volume management and how that relates to BTRFS to do before making any decisions. If you haven't used a volume manager before, prepare for your mind to be blown.  Wrap your head around that.

if it were me, I'd do a standard install, use that and play around with it for 6 months before blowing it away (if needed) and installing with storage setup the way I like.  I think you'll see some powerful stuff in the volume management and may not need to start over.

Regular partitions have always been a little too rigid.

Do you use virtual machines?  If so, be certain to look up what that means under BTRFS.

I'm now learning about subvolumes. If I read your post correctly, you think Btrfs subvolumes are preferred over separate partitions for my simple setup?

---

### Post by Advait on 2023-05-20
> **TheFu said:**
> Do you use virtual machines?  If so, be certain to look up what that means under BTRFS.

Thanks for the heads up. Yes, I regularly use VBox (Ubuntu and Windows guests). Are you saying that VMs operate differently when the Ubuntu host is using Btrfs? Do VBox guests fail to work with Ubuntu/Btrfs? If yes, that's a big issue for me. I'm now researching, but if you could give me a quick summary of the VBox/Btrfs issues, that would be helpful.

Update: I checked with GPT4 and it says (IIUC) that Btrfs can cause slowdowns when VBox guests have heavy workloads. That should not a problem for me. I don't put heavy workloads on my VBox guests. And I've got a somewhat powerful laptop with 40GB RAM and fast internal nvme drive.

I mainly use my VBox guests for browsing the web.

PS: My Ubuntu 22.04 guest is using Btrfs. This guest has separate partitions for root and home. I paid a Linux admin to remotely connect and set it up while I watched and took notes. I'm playing around with it to learn about Btrfs. Maybe I'll do this again but using subvolumes instead of partitions.

---

### Post by TheFu on 2023-05-21
If you are happy with your research, go for it.  I don't use BTRFS nor virtualbox.  Worst case, you'll just need to reinstall with a solution that better meets your needs.

Not all Linux admins are equal. Beware of someone who claims expertise with everything. Nobody knows everything.  I don't know everything about BTRFS and haven't used virtualbox at all in over 10 yrs.

---

### Post by #&amp;thj^% on 2023-05-21
BTRFS has come a long way in just the past couple years. (A lot of fixes have been implemented)
BTRFS is great for home since it's management interface doesn't require you rebuild pools so often as it is the case with ZFS .  And for updating your kernel, you don't have to wait for new kernel support of OpenZFS team. (One downside)
I use both with no problems. And like TheFu I haven't used Virtual Box in many years now...(KVM)
To be fair, Compared to ZFS, BTRFS is a simpler solution and better supported on Linux. The major downside is that it does not scale as well (when adding large number of disks) and does not have the same feature set.
Here is very detailed dive from someone I know: [https://www.ilsistemista.net/index.php/virtualization/47-zfs-btrfs-xfs-ext4-and-lvm-with-kvm-a-storage-performance-comparison.html?start=1](https://www.ilsistemista.net/index.php/virtualization/47-zfs-btrfs-xfs-ext4-and-lvm-with-kvm-a-storage-performance-comparison.html?start=1)

And I too warn of **" Beware of someone who claims expertise with everything. Nobody knows everything."**

---

### Post by Advait on 2023-05-22
> **TheFu said:**
> Not all Linux admins are equal. Beware of someone who claims expertise with everything.

I'm aware that Linux admins have different levels of knowledge. And I've never heard someone claim expertise with everything.

---

### Post by zebra2 on 2023-05-22
It's what you learn after you know it all that counts. There is a great deal of experience around this forum. No one needs an excuse for their experience even if it fails. 

So far as the OP is concerned I have found it to be organized and helpful to have separate partitions for for /root  /home and /SWAP.  It makes a reinstall simple. Just reformat /root and reuse /home. For my self, I am still using EXT4.  I don't need my partitions to be "fun".  /esp /swap /root /home, works just fine.

---

### Post by MAFoElffen on 2023-05-22
@zebra2 --

I taught Computer Science... I am old and have just been exposed to a whole lot of things. I don't claim to know everything. That is the challenge that keeps me driven.

If I don't know about something (and it sparks an interest), then I think to myself that maybe I should learn more about that...

I enjoy learning new things every day. That is entertaining to me, keeps my mind fresh, and keeps me informed. I even try to do things 'differently', just see where the pushed limits are, and to prove that things are not just assumed to be a certain way. You then get to learn how things break, and how to fix them when that happens. LOL

Whether the learning process is a systems methodology, a programming challenge, etc. Take the perspective that things can be applied to other things, in how you apply them. You would be surprised at how many times in my life, that people have told me that something will not work. Then I point out, that it could, and "here is how it can". Sometimes it just takes a different perspective.

I learn a lot from new users. Teaching and helping others makes you look at those things carefully, to ensure that they really make sense. In many cases, there is more than one way to do the same thing.

Learning about differing filesystems and file managers makes logical sense. It just takes learning and understanding how they work and the value they can add. Why limit yourself? Why not learn new things? 

Playing around with things in a virtual environment is a good way to learn and see how things do, can and could possibly work. That is where I do most of my DEV testing, before moving things to STABLE.

---

### Post by #&amp;thj^% on 2023-05-22
> **MAFoElffen said:**
> @zebra2 --

I taught Computer Science... I am old and have just been exposed to a whole lot of things. I don't claim to know everything. That is the challenge that keeps me driven.

If I don't know about something (and it sparks an interest), then I think to myself that maybe I should learn more about that...

I enjoy learning new things every day. That is entertaining to me, keeps my mind fresh, and keeps me informed. I even try to do things 'differently', just see where the pushed limits are, and to prove that things are not just assumed to be a certain way. You then get to learn how things break, and how to fix them when that happens. LOL

Whether the learning process is a systems methodology, a programming challenge, etc. Take the perspective that things can be applied to other things, in how you apply them. You would be surprised at how many times in my life, that people have told me that something will not work. Then I point out, that it could, and "here is how it can". Sometimes it just takes a different perspective.

I learn a lot from new users. Teaching and helping others makes you look at those things carefully, to ensure that they really make sense. In many cases, there is more than one way to do the same thing.

Learning about differing filesystems and file managers makes logical sense. It just takes learning and understanding how they work and the value they can add. Why limit yourself? Why not learn new things? 

Playing around with things in a virtual environment is a good way to learn and see how things do, can and could possibly work. That is where I do most of my DEV testing, before moving things to STABLE.

=d> Very Well Worded.
EDIT: If we did know everything about Linux systems would we even be here now???

---

### Post by Advait on 2023-05-23
After reading the posts and doing a bit of research, my intuition is to go with Btrfs subvolumes rather than separate partitions when I make the switch from ext4 to Btrfs. I'll need to hire another remote access Linux admin to do the work while I watch. In addition to watching some youtube videos, I'll have the admin show me the basics re managing subvolumes. 

So far I've had good success with the admins I've hired from Upwork.

My plan is to make the switch after 23.10 comes out.

Thanks everyone for your posts.

---

### Post by TheFu on 2023-05-24
I don't think partitions or subvolumes are the question. You need both.

---

### Post by Advait on 2023-05-24
> **TheFu said:**
> I don't think partitions or subvolumes are the question. You need both.

Oh, now that's interesting. Time for more research. I'll hop onto the Btrfs subreddit.

---


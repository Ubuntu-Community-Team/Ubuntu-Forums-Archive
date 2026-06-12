---
title: "Script to rebuild SWAP &amp; Config Hostname?"
date: 2017-01-24
forum: General Help
---

### Post by Smokin Whale on 2017-01-24
Hey guys. I'm currently doing some work to refresh some older hardware by deploying Ubuntu via custom SOE images, and I wanted to know if it were possible to script a process that can be run either automatically at boot, or manually if desired.

Essentially I have built a Ubuntu 16.04 configuration to my liking (also have an image for Linux Mint, works in the same way), deleted the SWAP partition and shrunk the partition down to 8GB or so. I then create an image using Macrium reflect, and I can seamlessly restore this image to new drives of any size.

Now, this part works great, but there are a few things that need to be done once the system is booted to make sure that the system is usable, which is fairly easy to do manually, but it would be nice to automate. The most important step is to adjust the partition, re-create linux-swap and edit /etc/fstab to mount it on boot. I've detailed this process in pseudo code:

1. Find the amount of system memory in the system so we can work out how large the SWAP should be. (Create variable $ram)
2. Find the amount of free space on /dev/sda. (create variable $free)
3. Subtract $ram from $free, so we know what the new size of the primary partition will be (create variable $sda1newsize. I'm not sure if this needs to be converted to sectors or not)
4. Set new size of primary partition (/dev/sda1) to $sda1newsize
5. Find amount of free space on /dev/sda (update variable $free)
6. Create linux-swap partition (dev/sda2) where size = $free
7. Apply changes.
8. Determine UUID /dev/sda2 (create variable $swapuuid)
9. Edit /etc/fstab and replace "f4dfd675-be4d-40b1-94e2-cb320bdea96b" with $swapuuid to enable the system to mount the new swap partition on boot.

There is also an optional step that I'd like to script which is nice for networking functionality, but isn't necessary. This is to change the hostname, so you don't have a bunch of identically named systems on your network.

1. Generate random 3 character string that is compatible with NETBIOS standards (eg. "6ef"). Create as variable $hostsuffix.
2. Edit /etc/hosts and replace string "Ubuntu-PC" with "Ubuntu-$hostsuffix"
3. Edit /etc/hostname and replace string "Ubuntu-PC" with "Ubuntu-$hostsuffix

If someone can help me out or at least point me in the right direction to try to get this scripted that would be awesome, and I'd be more than happy to share it here so others can use this as well. If someone has already done this, please point me in the right direction, but I've searched and I don't believe someone has done it and put it out for public availability. Thanks in advance!

---

### Post by TheFu on 2017-01-25
Yes, you can script it.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) should be helpful. Don't see anything that isn't pretty easy, though I'd probably do most of it using **ansible**.

Swap doesn't need to be rebuilt all the time and the old rules about sizing it based on RAM generally don't apply anymore, unless you allow hibernation. On servers, I try to have ZERO swap (RAM is cheap). On desktops, 4G is the best number for swap - 2G isn't quite large enough on limited systems and systems with more RAM will never need swap, but 4G is needed thanks to modern browsers easily sucking up 3.5G of RAM on their own.

If you don't need any data, I'd just wipe the disk and set the partition as desired, then use something like **fsarchiver** to load whatever image I wanted. Would look into PXE booting and auto-configuration methods if I had more than 10 of these devices - **cobbler**.  Though it wouldn't be too hard to put everything on a  flash drive running Linux, including ansible stuff, and have it load as you wanted.

Over the years, I've found that mixing case in hostnames is a bad idea. There's always 1 script written by someone that doesn't handle the mixed case correctly.  Just saw something on LAS that has convinced me to use "ubuntu-" rather than "linux-" for hostnames too. Mainly, so that end-users looking for answers always google with "ubuntu" in the search, not linux. Wouldn't want them to find fedora or debian answers and get confused/frustrated.

Just to be clear, I've never done this.  I manually partition systems, load a minimal server with ssh, then bring them up on the network and let ansible reconfigure everything (except the partitioning). Since a new system is needed less than once a month, it isn't a big deal. Having a base server ready (including current patches) in about 30 minutes is pretty common. We do have a local package caching server, so most needed updates are only pulled off the internet once for all the systems to use.

I look forward to seeing how other people handle this.

---

### Post by slickymaster on 2017-01-25
*Thread moved to **General Help**.*

---

### Post by Smokin Whale on 2017-04-03
Thanks for the response. Not familiar with Ansible. I've noticed that hibernation support has been getting better, so I do want to ensure swap is sufficient for hibernation. It's useful on my noisy desktop when I'm in the middle of something and need to close up for the night.

---


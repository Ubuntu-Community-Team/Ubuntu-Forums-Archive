---
title: "USB Flash Drive has bad superblock"
date: 2023-03-07
forum: General Help
---

### Post by Acharn on 2023-03-07
I bought a cheap USB 3.0 2TB thumb drive and tried to install Kali Linux on it. Failed on partitioning. e2fsck says there's a bad magic number in the superblock. Trying alternate superblocks doesn't help. Deleting the partition and creating a new one doesn't help. Formatting in disks doesn't help. e2mkfs -c would take more than 2 days to finish. What should I try next?

---

### Post by coffeecat on 2023-03-07
How cheap was cheap? If less than, say, $100, then I'd bet the $100 on you having bought a scam fake drive. Articles about the problem of fake 1-2TB USB drives are all over the internet, and a quick Google brought up this: [https://datarecovery.com/2022/03/the-2tb-flash-drive-scam-why-high-capacity-flash-drives-are-fakes/](https://datarecovery.com/2022/03/the-2tb-flash-drive-scam-why-high-capacity-flash-drives-are-fakes/) 

It's a year old, but I'm sure it's still relevant.

What should you try next? If I'm right then throw it away and chalk this one up to éxperience.

---

### Post by Acharn on 2023-03-07
Yeah, it was only $6 (&#3647;199), and I figured on just throwing it away, but after I posted above I ran fsck.ext4 again, and this time it actually worked. I'll try again tomorrow to install Kali Linux. I don't understand the ending diagnostic from fsck, though. I've attached it.

ETA: Finished reading the article you linked to. Yeah, looks like another throwaway, although I'll still look at it some more tomorrow. There are several dozen guys selling these on the internet site I buy from. TANSTAAFL.

---


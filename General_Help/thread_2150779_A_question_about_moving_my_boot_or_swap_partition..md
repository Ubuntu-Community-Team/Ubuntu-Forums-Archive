---
title: "A question about moving my boot or swap partition."
date: 2013-06-02
forum: General Help
---

### Post by Reduced_Oxygen on 2013-06-02
I have a thinkpad T430u which comes with a 1TB HDD and a 24GB SSD, as far as I can tell Ubuntu doesn't use the SSD at all (at least not by default) 

So should I move my boot partition onto it? if so how?

would it make more sense to put a swap partition there? (though I have 8GB of RAM so that might be a waste)

[IMG]http://i.imgur.com/gy1UMijh.png[/IMG][IMG]http://i.imgur.com/Rxhdtfdh.png[/IMG]

---

### Post by 2F4U on 2013-06-02
Personally, I wouldn't move swap to the SSD since a) as you already said, you have 8 GB of RAM and b) if swap is indeed necessary, it will wear out the SSD quicker. It would, however, make sense to move the / partition to the SSD for a much quicker boot and start of applications. But if you do that, I would recommend to leave /var and /tmp on the hdd in order to reduce write operations on the SSD. However, all that is much easier to do on a fresh install.

---

### Post by Reduced_Oxygen on 2013-06-02
do you know a decent guide for doing that from a fresh install? I'll do it next release.

---

### Post by 2F4U on 2013-06-02
There is not much magic behind it. Choose the "Something else" option of the partitioning dialogue. This will allow you to manually select or create the partitions and assign mount points such as / or /home.

---


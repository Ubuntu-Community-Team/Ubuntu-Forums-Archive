---
title: "ReadyBoost on Windows Vista, any equivalent on Ubuntu"
date: 2006-07-10
forum: General Help
---

### Post by dhruv_1884 on 2006-07-10
Hi,

I've been usuing Ubuntu for months now and absolutely love it but i do keep track of the competition.

New Competition ----- Vista

I just saw show on TV where a microsoft official kept bragging about a new feature called Readyboost.

Readyboost allows a user to use his/her Flash stick to give a boost to the RAM, he made it sound like as if the Flash disk was becoming another RAM Module. In his words "When your computer gets slow, just plug in your flash stick and problem solved". I dont believe that completely but i know that a flash stick could actually lessen the burden of the RAM

Anybody at Ubuntu who knows about this and is planning a similar thing for Dapper. The feature seems like a good idea to me.



By the way he was also bragging about the new "security" features. He He, :razz: 
He was also of the opinion that this version will not get "pirated", i hope so too.

Why?????

Ubuntu's biggest competition in Inida is the pirated XP. No body pays for any software here and people are used to formatting their computers when it's full of viruses.

If by some miracle, Vista doesn't get pirated, people will be forced to look for other alternatives in the near future and Ubuntu user of India will be there.

Hoping for a "secure" Vista

Regards

Dhruv

---

### Post by Darling on 2006-07-10
Given the speed of a USB stick, it don't think it'll give you much boost. You'd better create a 'RAM drive'.
And since ubuntu can run on a fraction of the minimal RAM required to run Vista, you won't really need it.
Your view on the pirated XP is interesting and might be very true.

---

### Post by dhruv_1884 on 2006-07-10
By the way, i forgot to mention,

it's not only the pirated Xp, the pirated anti virus also has a significant role.

The pirated anti viruses are good enough and generally are able to clean the system well enough for them to last at least 3 months without a reformat.

the only reason half these anti-virus/spam/adware/spyware companies exist is because of a poor microsoft product.

some times i feel that m$ might have an inside agreement with the top anti-v/s/a/s firms. it probably goes like this, m$ purposely makes a poor product which forces users to buy another expensive product like an anti-virus and the anti-virus company in turn pays microsoft a royalty.

---

### Post by 3rdalbum on 2006-07-10
The speed boost isn't a lot - about 7 percent on development Vista, but this varies from task to task and machine to machine.

Virtual memory is a bad bottleneck in Windows and Mac OS 9, because it's a retrofitted feature. In Linux and OS X (and BSD), virtual memory was written into the kernel from the very beginning, so everything else was written *around* it.

Also, the virtual memory file (also known as the "swap" or the "paging file") can become fragmented in Windows, so performance suffers as the hard disk seeks from one place to another. This is what the USB flash drive eliminates: the seek time. In Linux, as the swap is kept on a seperate partition, and a lot of space reserved for it, there's much less fragmentation.

In short, I don't think we need this feature. It's bound to cause more problems than it solves, too.

---

### Post by swamytk on 2006-07-10
I too heard about it. I think it is already there in Linux based system. How? Insert your USB stick in the system and format in swap file system. This is to be done only once. Whenever you need boost, issue swapon command to add this partition as swap space. How is it? :-) :-)

---

### Post by raldz on 2006-07-10
> **swamytk said:**
> I too heard about it. I think it is already there in Linux based system. How? Insert your USB stick in the system and format in swap file system. This is to be done only once. Whenever you need boost, issue swapon command to add this partition as swap space. How is it? :-) :-)

cool, but I think I will never be able to use the "swap stick" I have been observing the performance of my machine with 256 RAM and 1G swap.. it never even used greater than 256 of swap..

---

### Post by RAOF on 2006-07-10
> **swamytk said:**
> I too heard about it. I think it is already there in Linux based system. How? Insert your USB stick in the system and format in swap file system. This is to be done only once. Whenever you need boost, issue swapon command to add this partition as swap space. How is it? :-) :-)
I think the Vista system is a bit more sophisticated than this.  The deal being that while flash memory is much slower than either RAM **or** hard-drives in large reads, it has a much lower seek time than a harddrive.  So you can use flash memory in a different way than harddrive swap, and get better performance.

That said, I can't imagine that the performance benefit is really that great.  I'm not sure that the effort required to implement it would be worth it ;)

---


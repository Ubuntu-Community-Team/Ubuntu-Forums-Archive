---
title: "How to safely increase swap memory?"
date: 2015-04-17
forum: General Help
---

### Post by luke40 on 2015-04-17
My physical memory is 4G, and the swap space is 4G too.
How to safely increase the swap memory to 8G(double of physical memory)?
Thanks.

---

### Post by ricky-flammia on 2015-04-17
This should help. [http://askubuntu.com/questions/367331/how-to-increase-the-size-of-linux-swap-partition](http://askubuntu.com/questions/367331/how-to-increase-the-size-of-linux-swap-partition)

---

### Post by kerry_s on 2015-04-17
> **luke40 said:**
> [SIZE=5]My physical memory is 4G, and the swap space is 4G too.
How to safely increase the swap memory to 8G(double of physical memory)?
Thanks.[/SIZE]

why ? thats perfect as is, are you even using 4gb ram & 4gb swap ?

---

### Post by luke40 on 2015-04-18
I will try the method. Thanks.

---

### Post by luke40 on 2015-04-18
Yes. my ram is 4g and the swap is 4g too. Bcoz it is said the swap would be best double of ram.

---

### Post by plucky on 2015-04-18
> **luke40 said:**
> Yes. my ram is 4g and the swap is 4g too. Bcoz it is said the swap would be best double of ram.

What tutorial are you following?

Probably out of date.

Do you hibernate?

I would leave it at 4G.

Good Luck

---

### Post by mcduck on 2015-04-18
> **luke40 said:**
> Yes. my ram is 4g and the swap is 4g too. Bcoz it is said the swap would be best double of ram.

That rule was correct back in the days when you'd have 512MB or less of RAM.

Now, when we have gigabytes worth of RAM the swap shouldn't in most case be needed at all (although having some just as a backup is often a good idea). However you definitely don't need 8GB of swap in any normal use.

The rule these days is pretty much that having a gigabyte or two of swap is good (although not required), but if you wish to hibernate your computer, then you need same amount of swap as you have RAM.

---

### Post by Skaperen on 2015-04-18
do you have free space on disk for this, either an 8gb spot or a 2nd 4gb spot?

test how much time it takes to read that much ... this is how much slower your system will become.

can increase your RAM?

---

### Post by Bucky Ball on 2015-04-18
2Gb /swap unless you intend to hibernate, then it should be the same size as installed RAM. I'd launch gparted, right click the /swap partition and 'swapoff' then *_shrink_* the /swap to 2Gb.

Please use default font and font size. Large font is considered shouting and is discouraged. I have changed the font size in your first post.

---

### Post by HermanAB on 2015-04-18
Well, if you really need more swap for truly huge computations, then you can make a swap file.  It is not any slower than a swap partition.  Read the swapon man page - it is good one and explains it all:
$ man swapon

---

### Post by Skaperen on 2015-04-19
i consider an upper limit on swap space to be whatever takes a working tolerable time limit so that i don't end up with too much swapped out and it taking **too long to swap back in**.  _these days RAM is cheap enough to avoid swap entirely_.  on desktops over 12gb and laptops of 16gb or more **i just avoid swap when i do the install**.  there is a rumor that the kernel behaves "funny" so i suggest having some swap but **i see no need for more than 1gb** and suggest an upper limit of 2gb.

---

### Post by luke40 on 2015-04-19
OK. I understood. many thanks to all replies to this question and I will leave the current size of swap as it is.

P.S. I asked this question bcoz the dolphin seems a little solw when reading and showing the contents of big folders which contains hundreds of files.

---


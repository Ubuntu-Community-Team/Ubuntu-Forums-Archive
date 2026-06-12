---
title: "need help with ubuntu 9.04 and chromium"
date: 2021-10-22
forum: General Help
---

### Post by leol1126 on 2021-10-22
so i have a really old laptop with ubuntu on it.
it has ubuntu 9.04 installed and i dont want to update.
it only has firefox 3.0.8 which cant load many webpages so i need to install chromium.
so i need the latest versoin of chromium ubuntu 9 supports and a download for it.
please help i tried looking and cant find a working one.
can someone help please.

---

### Post by guiverc on 2021-10-22
Ubuntu 9.04 reached EOL (*end-of-life*) in 2010; so I'd not try and bring it online, nor look for a version of `chromium` for it (the latest is *snap* which 9.04 cannot run).

[https://fridge.ubuntu.com/2010/11/12/ubuntu-9-04-end-of-life-reached-on-october-23-2010/](https://fridge.ubuntu.com/2010/11/12/ubuntu-9-04-end-of-life-reached-on-october-23-2010/)

I don't know what you consider *old*, but I used devices from 2003 upwards in QA-testing Lubuntu/Xubuntu releases up to 19.04 when *i386* images were finally stopped; then they were used with re-spins of 18.04 LTS (eg. [August-2020 was 18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/"))

If your box is *i386* (32-bit only; Debian & Ubuntu call x86 32-bit all *i386*) then your safest solution is a re-install of a 18.04 LTS *flavor*.  

If you box is *amd64* or x86_64 then newer releases are they way to go.  64-bit boxes came out prior to 2000 though they weren't common until subsequent years (laptops were commonly 32-bit until 2005; though later cheap/consumer grade netbooks released well after that). 

I'd not suggest using a 9.04 box online with any modern browser  (`lynx` maybe safest; but your box still isn't safe online)

---

### Post by leol1126 on 2021-10-22
i dont really care about security (i have a windows xp laptop that i use and it is almost always connected to the internet when i use it). also i dont think that would work well because i had to install it to usb (toshiba partitioned the drive into 4 segments so i cant install to hdd) and i think its making a faulty connection because a lot of the time it gives me the operating system not found error and it rarely doesnt. im not updating because this install is only going to be used for a while because the usb i installed ubuntu 16.04.7 lts on broke (it got bent) so i just need it to work. i use out of support operating systems too i use 20.10 on my desktop and that desktop is what i am posting this on and it works fine.

---

### Post by guiverc on 2021-10-22
Ubuntu 20.10 is EOL too - [https://fridge.ubuntu.com/2021/06/18/ubuntu-20-10-groovy-gorilla-reaches-end-of-life-on-july-22-2021/](https://fridge.ubuntu.com/2021/06/18/ubuntu-20-10-groovy-gorilla-reaches-end-of-life-on-july-22-2021/)

Ubuntu 16.04 LTS has ended its *standard* or *community* supported life, and receives patches & security fixes on with ESM enabled - [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

Use LTS (*long-term-support*) releases if you want a longer life.

A MBR/DOS/legacy partition table can only have 4 *primary* partitions; you can have more via the use of *extended* partitions (ie. the *extended* partition can be divided up into numerous partitions)

---

### Post by yancek on 2021-10-23
>  i dont really care about security (i have a windows xp laptop that i use and it is almost always connected to the internet  

We, or at least I, don't care about the security of your computer either but do care about other people's computers and by using outdated and insecure operating systems, you are jeopardizing other people's computers by allowing your computer to be used as a bot to hack others.  If you don't care about your own computer being hacked, have  little concern for others.

---

### Post by mIk3_08 on 2021-10-23
> **leol1126 said:**
> i don't really care about security (i have a windows xp laptop that i use and it is almost always connected to the internet when i use it).. Yes, Your computer can be use to manipulate others computer and we are only to support those under supported releases not EOL (End of Life) Operating System. But if you continue to use it. Take it as your own risk. Good Luck.

---

### Post by dragonfly41 on 2021-10-23
Actually, I have an ancient Dell rugged laptop still with Windows XP installed.
I retain it in my museum since I might have to extract data from ancient drives.

Meanwhile, it is possible that your old setup could be used to access a virtual Ubuntu desktop at [https://rollapp.com](https://rollapp.com).
There you can play with various applications.

I am also toying with the idea of installing virtual Ubuntu 20.04 desktop on Linode account.

---

### Post by coffeecat on 2021-10-23
> **leol1126 said:**
> i dont really care about security (i have a windows xp laptop that i use and it is almost always connected to the internet when i use it). 

Two members have already responded to this alarming comment, so there's nothing much that I can add. Except that although we do not have a formal forum policy disallowing support for EOL releases, we strongly discourage it except for certain rare use-cases, for example where someone needs to use an EOL release for research or educational purposes, or for running an obscure piece of software that will only install on an EOL release. *But in all cases we hope and expect that the user will act responsibly and not connect the system to the internet.* On this forum we have a responsibility to new users of Ubuntu, who constitute a significant part of our membership, to ensure that they are not influenced by bad practices, such as connecting an obsolete operating system to the internet. Both Ubuntu 9.04 and Windows XP are very much obsolete. 

In the circumstances I shall close this thread, since there is really nothing more to say about using Ubuntu 9.04 in the way in which you describe. If you want help installing a *supported* version of an operating system on that "really old laptop" then you are welcome to start a new thread. That being said, I suspect that this old laptop is 32-bit and therefore unsuitable for all recent and supported releases of Ubuntu and official flavours of Ubuntu. Which means that any thread you start may be moved to a non-Ubuntu part of the forum, but I am sure that members here would have useful suggestions. 

Thread closed.

---


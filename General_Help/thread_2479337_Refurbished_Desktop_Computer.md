---
title: "Refurbished Desktop Computer?"
date: 2022-09-21
forum: General Help
---

### Post by billywyatt2 on 2022-09-21
Hello everyone

I am thinking of getting a refurbished desktop computer from Amazon in order to save some of my pension money but all the desktop computers i have seen so far are running Windows 10 or 11 operating systems. Now i only want to run the latest Ubuntu OS and would delete the default Windows OS the desktop came with. Would there be any problems by doing this? Also, i have never installed Ubuntu on an SSD drive so could anyone pointed me to an easy to follow tutorial covering this please.  Big thanks

---

### Post by mikewhatever on 2022-09-21
There is nothing special about installation on SSDs. Try this guide: [https://ubuntu.com/tutorials/install-ubuntu-desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop).
There is no way to guarantee problems free installations without any details. Usually, it works well, and if there are problems, you can ask here.

---

### Post by Bashing-om on 2022-09-21
billywyatt2 

#2
I found to be of assurance:
[https://easylinuxtipsproject.blogspot.com/p/ssd.html](https://easylinuxtipsproject.blogspot.com/p/ssd.html)

And to further your confidence:
[https://ubuntu.com/certified](https://ubuntu.com/certified)

[INDENT]my bit to try and help
[/INDENT]

---

### Post by ne29914 on 2022-09-21
There are always problems.
From painful recollection: don't do this alone.
Have a friend alongside you with a working PC with Internet connection, and have a handful of USB-thumbs on hand. The moment you start the installation, your machine is dead to the outside world, and you have no chance of recovering on your own.
Hopefully, the installation will run perfectly, but you never know. This applies to Win installs/updates as well, BTW.

---

### Post by mIk3_08 on 2022-09-21
> **billywyatt2 said:**
> Also, i have never installed Ubuntu on an SSD drive so could anyone pointed me to an easy to follow tutorial covering this please.  Big thanks Yes. Nothing special on SSD. It will just give you more speed than the rotating disk the Hard Disk Drive (HDD) The difference between the two is that HDD now is more cheaper compared before. You can buy HDD now with a cheaper price in a higher capacity storage. Regards and cheers.

---

### Post by ian-weisser on 2022-09-21
You already made one wise choice: Purchase from a vendor with a generous return policy.

Next, DON'T wipe Windows immediately. Instead, boot the LiveUSB into the "Try Ubuntu" environment and test, test, test!

- Test your network connectivity and bandwidth. Test streaming a movie.
- Test connecting to printer, scanner, and other USB peripherals. Do test prints and scans.
- Test your keyboard and mouse for proper function and no lag.
- Test your monitor and video card (if any) for graphical glitches during the movie.
- Test your microphone and audio. Make sure you have a full range, clear sound, no weird buzzing or static. Check sync with video during the movie.
- Test your Bluetooth headphones and other peripherals,
- Test-install your favorite software and put it through a few paces.

You're looking for compatibility more than speed. The "Try Ubuntu" environment can be a little slow. Speed comes *after* the install.

After an afternoon of testing, you'll KNOW if you like the hardware, how well it works with Ubuntu, and whether you should return it or keep it.

Now you're ready to install Ubuntu.

---

### Post by QIII on 2022-09-21
And bear in mind that a USB session may run slowly.  That's just the nature of running from USB and not a problem with the OS.

---

### Post by Impavidus on 2022-09-22
Refurbished means it's not brand new, which is good news for compatibility with Ubuntu. There are not always Linux drivers available for the latest hardware. If it comes with Windows 10 or 11, it's certainly powerful enough to run Ubuntu.

Paying a little attention to the exact hardware may help. Sometimes it works out of the box with Ubuntu, sometimes (for example, nvidia graphics) you need proprietary drivers. It's not too much of a hassle normally, but you may want to avoid it anyway.

---

### Post by billywyatt2 on 2022-09-22
Hello everyone

Please let me start by thanking everyone who has taken the time out to reply.

I have selected a desktop pc from the Amazon site [https://www.amazon.co.uk/OptiPlex-Desktop-Computer-Windows-Renewed/dp/B09X5RHK2K/ref=pd_rhf_d_se_s_pd_sbs_rvi_sccl_2_3/262-3776979-3896547?pd_rd_w=0xG9S&content-id=amzn1.sym.0963df7f-7cea-4859-a393-2a2c2885a717&pf_rd_p=0963df7f-7cea-4859-a393-2a2c2885a717&pf_rd_r=83JHWSC6TWW11F3SPE1Q&pd_rd_wg=KK8JN&pd_rd_r=943281d2-f2c9-4c3f-abf4-b1f4d4315b9a&pd_rd_i=B09X5RHK2K&psc=1](https://www.amazon.co.uk/OptiPlex-Desktop-Computer-Windows-Renewed/dp/B09X5RHK2K/ref=pd_rhf_d_se_s_pd_sbs_rvi_sccl_2_3/262-3776979-3896547?pd_rd_w=0xG9S&content-id=amzn1.sym.0963df7f-7cea-4859-a393-2a2c2885a717&pf_rd_p=0963df7f-7cea-4859-a393-2a2c2885a717&pf_rd_r=83JHWSC6TWW11F3SPE1Q&pd_rd_wg=KK8JN&pd_rd_r=943281d2-f2c9-4c3f-abf4-b1f4d4315b9a&pd_rd_i=B09X5RHK2K&psc=1) so that you can see the machine. I just want a machine that will run Ubuntu 22.04 or newer versions as and when they are released. I don't want Windows 10 or Windows 11 i just want my Ubuntu installed on the SSD drive. Does the machine i've selected come with a SATA hard drive or will i have to purchase one myself?

Once again big thanks everyone

---

### Post by QIII on 2022-09-22
SATA is an interface, not a storage type.  Don't worry about that.  Whether stored on spinning platters or non-volatile solid state chips, it is all the same to the SATA interface.  The controllers inside the storage devices do all the work of communicating.  You don't have to bother.

Your machine appears to be provisioned with an SSD and an SSHD (a hybrid SSD/HDD from a time when SSDs were expensive, but it was nice to have the extra speed with some of the storage), each of which is connected via a SATA interface.  You don't need to be concerned with the inner workings of the storage devices.  The interfaces will look no different to you than any SATA disk.  You will not need to buy anything.  There will be no special installation considerations.  

Otherwise, the machine appears to be perfectly capable of doing what you want and you should have no surprises.  Nothing is perfectly guaranteed, but if I were you I would rest assured that it will "just work".

That said, I'll repeat what someone said above:  Refurbished is not new.  It is possible that the older hardware is nearing the end of its service life.  But the CPU, an older one, can be found online for < $50US, a 500GB SSD can be had for a song and the memory type is inexpensive.  No need to worry about a graphics card because that CPU has an integrated on on-die GPU.  If you replace the CPU, you will be replacing the GPU.

The i7 4770 is a fourth generation CPU and is getting a bit dated.  That is not bad for what you appear to want to do with the machine.  It just means that you won't be setting any benchmark records with it.  For a home-use machine, you won't notice anything frustrating.  It will provide solid performance.  It's a multi-core 64-bit CPU, and that should run any new Linux distro for the foreseeable future.  The on-die GPU is not a screaming fast bit of hardware.  Movies and videos should be just fine, but more recent games are probably going to struggle.

What you have there is just exactly the sort of thing that many Linux enthusiasts like:  a bit older, inexpensive and very capable of running Linux.

---

### Post by mIk3_08 on 2022-09-22
> **billywyatt2 said:**
> Now i only want to run the latest Ubuntu OS and would delete the default Windows OS the desktop came with.Wise decision, check, test the Ubuntu Operating System. You can always try Ubuntu Operating System without installing first. As what ian-weisser said that test.... test.. test.. It will be wiser decision you'll made. test all the hardware components of your hardware system. Regards and cheers.

---

### Post by SeijiSensei on 2022-09-23
I've never owned a Dell that had problems with Linux. Right now I'm on a refurb Optiplex 9020 that I bought from Wal-Mart for $300. I added one of my spare SSD drives and installed Ubuntu. I swapped the SATA cables to make the Linux drive primary. Now I can boot either operating system. Though usually I prefer using virtual machines for Windows on top of Linux, games demand direct access to the hardware for best performance.

---

### Post by TheFu on 2022-09-24
> **ne29914 said:**
> There are always problems.
From painful recollection: don't do this alone.
Have a friend alongside you with a working PC with Internet connection, and have a handful of USB-thumbs on hand. The moment you start the installation, your machine is dead to the outside world, and you have no chance of recovering on your own.
Hopefully, the installation will run perfectly, but you never know. This applies to Win installs/updates as well, BTW.

99% of the time, the flash drive with the installation has a "Try Ubuntu" mode which is sufficient to run for a few days.  I've run a media server after a hard drive failure from a "Try Ubuntu" flash drive while waiting for a replacement HDD to arrive.
So, keep your current computer until you are certain the new-to-you one is working for a week with Ubuntu.  Have a pre-built Ubuntu Install flash drive that you know works.  It can be tested on any x86-64 computer that will boot from USB.

Amazon isn't the only place to get used computers.
* Any local computer shop that fixes computers will have used computers for sale.  That includes national chains like Microcenter (or your local equivalent), but small, independent, computer fix-it shops will definitely have plenty.
* ebay - I buy 2-4 yr old laptops off ebay. They are being sold from corporate replacement efforts - basically they were leased by a company and when they come off-lease, there are thousands of the same model flooding the market. Desktops are even easier, since those off-lease desktops are seldom desirable.

My local Microcenter has Core i5 desktops for $150 - off lease, for example.

As for compatibility, stick with Lenovo or Dell for the best compatibility.  Any be certain to use some benchmarks so you don't get screwed by a really, really, slow CPU, terrible GPU, and tiny storage.
In the front of your mind should be that you can build a desktop system with a Ryzen 5 5600G for about $400. That's a 20K passmark box for $400 with a reasonable iGPU for light games and any office productivity needs.  So, only you can decide if 30 minutes of turning some screws and connecting 5 cables and inserting 2 RAM sticks is worth having an excellent, fast, computer or not.

There is good news.  Since Win11 requires some newer CPUs, many computers that are just a few yrs old which don't have the needed hardware (TPM chip) will be available and flooding the market.  Ubuntu doesn't care about TPM, though I think it can use it.

Looks like a Core i5 6xxx is $200.  Don't pay that for anything slower or older.  We all have different needs, so only you can decide on the budget and performance for your workload.  I picked up an 8th-gen Core i5-8250 laptop about 3-4 yrs ago for $305. That should provide some expectations on a price never to exceed in a used computer - desktop or laptop.

If you have time, you can watch for deals over the next few months, but be ready to pounce.  Dell has a refurbished sales website that has been having some good deals on Core i5/i7 systems the last 3 weeks - over 50% off.  I haven't been watching the desktop sides, since I prefer to upgrade my desktops with new internals, not buy full computers.  I do watch the laptops, since I'm in the market for a 13inch 1080p 10th gen Core i5 Dell laptop.  I like Dell keyboards.  I've been burned by bad keyboards from Toshiba, Acer, Asus, Apple, HP, and nearly everyone else.  The Dells seem to have 5+ year lives and are easier to replace.  With a desktop, I expect a mechanical keyboard to last 20 yrs.  Was using a real IBM 101M until last Feb that cost me $0.50/ea in 1996.  Grabbed 3 from a metal bin at a used/off-lease computer show back then. Over the years, seems I gave 2 of those away - big mistake. Now I'm putting up with a Logitech mechanical keyboard. The "feel" is fine, but the USB interface sucks.

---

### Post by TheFu on 2022-09-24
> **billywyatt2 said:**
>  
I have selected a desktop pc from the Amazon site [https://www.amazon.co.uk/OptiPlex-Desktop-Computer-Windows-Renewed/dp/B09X5RHK2K ](https://www.amazon.co.uk/OptiPlex-Desktop-Computer-Windows-Renewed/dp/B09X5RHK2K ) so that you can see the machine. 

That machine with Win11 would be painful.  The passmark is: 7000. Meh. [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-4770+%40+3.40GHz&id=1907](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-4770+%40+3.40GHz&id=1907)  Unless it is under $100, I wouldn't touch a CPU that old.  I see a Core i5-4xxx model for $153.  Really should look for a 8xxx or 10xxxx CPU these days.  The current Intel CPUs are 12xxxx, BTW.  

Look for DDR4 RAM, not DDR3. That's a reasonable cutoff for any used purchase.

BTW, the link is showing 'out of stock' to me.

---

### Post by scumbalina on 2022-09-25
The OP stated fairly clearly that he won't be running Windows at all so your remark is irrelevant. An i7-4770 with 16GB DDR3 RAM will run any Linux based distro just fine. In fact anything short of higher end gaming will run fine. It is an office pizza box form factor so I hardly think he will be putting in an expensive videocard to run the latest games.
The only other note I would make is that it has an SSD and a HDD so he will have to pay attention to which drive he installs the OS to. He will also have to format the second drive in order to use it as storage.

---

### Post by TheFu on 2022-09-26
> **scumbalina said:**
> The OP stated fairly clearly that he won't be running Windows at all so your remark is irrelevant. An i7-4770 with 16GB DDR3 RAM will run any Linux based distro just fine. In fact anything short of higher end gaming will run fine. It is an office pizza box form factor so I hardly think he will be putting in an expensive videocard to run the latest games.
The only other note I would make is that it has an SSD and a HDD so he will have to pay attention to which drive he installs the OS to. He will also have to format the second drive in order to use it as storage.

People say they are switching to Linux desktops all the time.  I've helped nearly 1000 people do just that and about 80% run back to Windows for 1 or another reason, sadly.
There's a point where getting too old hardware is just getting someone else's old crap. That was/is my point.  The market is about to be flooded with 8th gen computers due to Win11 requirements.  Nearly every company/govt in the world will be replacing thousands of desktops with new hardware to meet the Win11 requirements.  [https://www.tomsguide.com/news/these-are-all-the-intel-and-amd-cpus-that-can-run-windows-11](https://www.tomsguide.com/news/these-are-all-the-intel-and-amd-cpus-that-can-run-windows-11) says 8th-gen (and later) or Ryzen 2xxx or newer.  That leaves the Ryzen 1xxx series and older Intel off the list.  There's a huge difference in 4th gen and 7th gen.

---

### Post by cmcanulty on 2022-09-27
Should be no problem. Dell sells computers with ubuntu linux and I have converted several Dell Optiplex for our local library from windows to ubuntu with no issues.

---


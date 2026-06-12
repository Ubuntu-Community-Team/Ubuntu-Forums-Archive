---
title: "Compaq Armada e500 help with boot isue"
date: 2020-04-19
forum: General Help
---

### Post by konik1342 on 2020-04-19
hello
tried to disable Compaq Armada e500 Notebook PC Mobile Intel PRO/1. NIC PXE Boot Manager using tool IBAUtil.exe 
as far i remember i used option to disable one off boot option hopping i will get option to boot from CD or USB 
So after i did save&reboot i got just  Compaq logo without any chance to go in bios
Any help 
](*,)](*,)](*,)](*,)

---

### Post by CelticWarrior on 2020-04-19
Welcome.

There's ALWAYS a way to access BIOS/UEFI and also it is in its settings that one enables/disables boot devices and/or changes boot order, not using some random software to disable network cards (really??)

---

### Post by CelticWarrior on 2020-04-19
And are you talking about this [Compaq Armada E500]("https://www.cnet.com/products/compaq-armada-e500-15-piii-win98-se-128-mb-ram-20-gb-hdd-series/") ?
If so what exactly are you trying to do with it that could be Ubuntu related? Ubuntu doesn't run in that thing, that thing belongs to a museum.

---

### Post by konik1342 on 2020-04-19
hi
i appreciated any reply 
i know how old this laptop is 
recently i got laptop from eBay with no HD 
Originally tried to kill some quarantine time to run this laptop whit live CD or  USB 
Was trying all boot option but no result every time boot manager skips all boot option and displays "missing operating system"
Guess main boot option are on missing HD  tried other options in order to make laptop boot from cd but no success
and on the end i tried  IBAUtil.exe  I know where i make mistake i disable one of boot option ????
what i needed to do is only to upgrade old bios or i am wrong

any advice???

---

### Post by mörgæs on 2020-04-19
I used to have one of those:
[https://ubuntuforums.org/showthread.php?t=1155961&page=27&p=9834517&viewfull=1#post9834517](https://ubuntuforums.org/showthread.php?t=1155961&page=27&p=9834517&viewfull=1#post9834517)

As you can see from the post, with some effort I managed to run a system which was considered lightweight ten years ago. 

With today's heavyweigth browsers in mind I wouldn't put time in the project.

---

### Post by CelticWarrior on 2020-04-19
How were you able to run a DOS/Windows executable without an OS? In a floppy, maybe? Anyway, not the point...

Even with the RAM maxed out (512MB) it could, at best, run something like AntiX or Puppy Linux. And not from USB, only from CD/DVD and that implies an optical drive that still works (possible but very unlikely).

IMO, you wasted money and now you're wasting time. If you're into retrocomputing start by watching a few Youtube channels like 8-bit Guy, LGR, RetroManCave, etc.

---

### Post by konik1342 on 2020-04-19
Guys I really appreciated your effort but my concern is not that the I don't know which distro to install 
Simply I'm just trying to recover the bios on laptop 
Just trying to figure out how to flash new bios 
Is it "bios programmer" my last option&#55357;&#56911;&#55357;&#56911;&#55357;&#56911;&#55357;&#56911;

---

### Post by CelticWarrior on 2020-04-19
Are you sure you need to flash a new BIOS?
If so you need to find a compatible one somewhere. Maybe our dear Pajero driver staff emeritus can help?
Fun fact: "Pajero" in spanish means "wanker" :lolflag::lolflag:  


Then you also need some bootable media from where to flash the new BIOS with.

---

### Post by konik1342 on 2020-04-19
Wow that's help a lot &#55357;&#56832;&#55357;&#56832;&#55357;&#56832;&#55357;&#56832;
Just joking thanx budy
After I mess up whit a bios on laptop I end up whit a brick
Is there any other option or I must use one off those 
[https://www.google.com/search?q=programer+chip+adapter&client=ms-android-hms-tmobile-us&prmd=sivn&sxsrf=ALeKk00xea19so60hqlX2kNRAcV_KDFxgQ:1587343298219&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjr5LTL4vXoAhXOknIEHSq6D20Q_AUoAnoECA0QAg&biw=360&bih=520#imgrc=3vEdezBtEI3iaM](https://www.google.com/search?q=programer+chip+adapter&client=ms-android-hms-tmobile-us&prmd=sivn&sxsrf=ALeKk00xea19so60hqlX2kNRAcV_KDFxgQ:1587343298219&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjr5LTL4vXoAhXOknIEHSq6D20Q_AUoAnoECA0QAg&biw=360&bih=520#imgrc=3vEdezBtEI3iaM)

---

### Post by CelticWarrior on 2020-04-19
For the record, I was messing with our dear staff emeritus and his ride.And the joke is only for spanish speaking people; Hyundai almost did something similar recently with its Hyundai Kona which sounds the same as "Cona". Any portuguese speaking person should be familiar with this very feminine word. They ended up changing the name for Portugal but released it anyway in Spain, Galicia is part of Spain (it shouldn't be...) and here many of us speak Galician (some as portuguese, different accent).

And I was messing with him because he mentioned he owns or owned the same model as yours. If anyone can help it's surely him.

> Is there any other option or I must use one off those 
[https://www.google.com/search?q=prog...3vEdezBtEI3iaM]("https://www.google.com/search?q=programer+chip+adapter&client=ms-android-hms-tmobile-us&prmd=sivn&sxsrf=ALeKk00xea19so60hqlX2kNRAcV_KDFxgQ:1587343298219&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjr5LTL4vXoAhXOknIEHSq6D20Q_AUoAnoECA0QAg&biw=360&bih=520#imgrc=3vEdezBtEI3iaM")
There must be because nothing in that list is...
The firmware must be flashed the usual way but the main problem is finding it. This is must understand. You have to have the actual firmware to flash and the motherboard must be in a "flashable" state. Otherwise the whole thing IS indeed a brick.

I'm afraid the BIOS is no longer available for download. Compaq was bought by HP some 20 years ago, give or take, and now all former Compaq product are hopelessly out of support. So, if it's really broken and nobody has it now, it's end game, period.

But are you sure it's really broken? I think you should at the very least try this: [https://dewagdkasl.wordpress.com/2010/11/22/how-to-enter-the-bios-setup-on-a-compaq-armada-e500-laptop/](https://dewagdkasl.wordpress.com/2010/11/22/how-to-enter-the-bios-setup-on-a-compaq-armada-e500-laptop/)

---

### Post by konik1342 on 2020-04-19
Thanx bud 
Would like if we can continue tomorrow about this matter 
Its true that Compaq supports stopped long time ago but there are still places on internet were u can find those files 
I will show you tomorrow 
I know that only solution that I have is to flash bios and only I can use flash programmer like I show you in the link above 
Just was checking whit Ubuntu forums to see maybe someone has any other solution becouse
I tried most of them
Those laptops are extremely powerful machine and durable that's way I love to work with 
I Also have CompaqArmada 1700 whit one of Pupy Linux flavor installed on it 
Ok lets continue tomorrow
Thanx bud

---


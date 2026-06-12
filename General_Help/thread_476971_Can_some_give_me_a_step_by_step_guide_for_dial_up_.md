---
title: "Can some give me a step by step guide for dial up in Edgy?"
date: 2007-06-17
forum: General Help
---

### Post by twistedbydesign on 2007-06-17
Here's my deal, I started my Ubuntu existence at college where i had high speed internet. Now school is over...and my mom, who is a minimal computer user, has no problem with dial up..and i really didnt either...until i tried getting it to work on Ubuntu.
before i go any further...if dial up DOES work in 6.06, i am willing to install it...i wasnt sure if it was broken in that one too...so if you know whether it works in that version let me know,.
Basically I have to get Dial up working on my machine WITHOUT having to download anything...because when Ubuntu is running i have NO access to the internet. My modem is a "56k Fax modem V.9.2 ready PCI".
so IF it is possible to get dial up working on my computer, and anyone can give me a step by step guide to get it working...i would be eternally grateful.
If it's not possible to fix i can live with windows until school starts back up...I just miss my ubuntu.
Thanks in advance if you can offer any help!

P.S. There is another computer in the house...so i can download stuff using it and just transfer it over if necessary...so i guess i DO kinda have access to the internet..just not on the machine im running ubuntu on

---

### Post by BrokeBody on 2007-06-17
Well, since you have another computer with Internet access, then install Ubuntu, and if your dial-up modem doesn't work out of the box, then we'll start searching for the driver. ;)

---

### Post by Bartender on 2007-06-17
Some internal winmodems can be made to work with Linux but it's a pain and very likely beyond the typical new Linux user's capacity to work thru.
The simplest thing to do is shop around for a true hardware external serial modem like a US Robotics.  Have been told there are a couple of others, such as a model from Trendnet.

See if you can get gnome-ppp installed to your Linux PC (borrow someone's broadband), or try out PCLOS or MEPIS which come with KPPP.

Then you have to deal with the ISP.  Maybe they'll work OK with Linux, maybe not.  Some cut you off pretty quickly if they don't see active browsing, others are more lenient.

EDIT:  Although the GUI modem setup in Dapper works but doesn't in Edgy and Fiesty, Dapper won't work any better for you than the newer ones if the issue is a winmodem that Ubuntu can't talk to.  Apparently better winmodem support is on the priority list for Gutsy.  I'm not expecting any miracles but cautiously optimistic.

---

### Post by twistedbydesign on 2007-06-18
I guess i should have been more specific...my question was really based on the broken modem setup wizard...i already read about winmodems and all that stuff...so if that's the problem i should be able to tell.
i'll go ahead and try 6.06. if it doesnt work i'll come back and beg for more help lol.
thanks

---

### Post by Bartender on 2007-06-19
twisted -
If you're not really set on Ubuntu, and have a friend who can download/burn a CD for you, you should try PCLOS or MEPIS, which comes with KPPP.
KPPP won't solve all your problems if you have a winmodem, but it's a fairly straightforward program for finding/configuring a functional external modem.  I've found pretty good KPPP tutorials on some ISP websites, like ISP.com!

---

### Post by MichaelSM on 2007-06-22
Hi Twistedbydesign. It's simple. Save yourself a lot of headaches and grab a 56k serial modem from somewhere like a garage sale or the op. shop or the tip. Use 6.06 and nothing later. FORGET 6.10 and Feisty. They're not worth the effort unless you get incredibly lucky with a 'supported' PCI modem and even then it's a  s%$t-fight.
With Dapper 6.06 just plug in the external modem, go to Admin>Networkiing>etc. and follow the instructions to connect with your ISP credentials. Easy as. Works every time, unless you get a crook modem, and that's pretty rare.
I loaded up a spare box with Dapper the other day and downloaded all the updates and there's heaps of them. Hundreds of megs. Everything I need from heaven to breakfast is there, including BlueTooth etc. (in Synaptic of course)
This Forum is replete with update worries. 
Get back to something which works without losing sleep over /etc/blah/blah.  entries. 
Dapper was my first entry into Ubuntu and I'm shocked that I got sucked into playing with development  packages when everything was working fine. 
Hope this helps.
Mike.

---

### Post by Bartender on 2007-06-22
Hey, guys, I've been screwing around with ways to get dial-up working.  Found a few things that might help.
Please add to this thread if you have any helpful info.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

I feel like a dope about the Ubuntu packages webpages.  Hadn't looked into them at all.  If you have any sort of access to broadband at work or school or a friend's house, you could use the package website for the huge downloads that would be a pain on dial-up.  And smaller packages like gnome-ppp can be brought to your PC from any Windows PC, even one on dial-up.

Anyway, it looks like Feisty can be set up for dial-up fairly easily if you create the /etc/resolv.conf file.  There's some other step, too, and I know MichaelSM is familiar with it but I forgot what it is right now.  Something about adding some lines to chap or pap?

An external US Robotics serial modem is probly the simplest way to get a functional modem.  If you go to ebay be careful to avoid buying old 36K modems (56K is what you want), modems without the serial cable, and modems without the 120V wall cube.  I bought a couple of old Sportster model #0701's on ebay with all cables included and they've worked fine.

---

### Post by MichaelSM on 2007-06-22
Thank you Bartender but all that editing pap or chap files sent me nuts. I can't remember any of it and wish it had never occurred. So I'm sorry I can't help in the Edgy/Feisty framework. The threads are there and anyone can give it a go. I simply gave up, sad to say. Other people have made it work but I'm just dumb. 
 I'll never understand why Ubuntu 6.10 plus retained the networking gui for dial-up whilst making it inoperable at the same time. Weird ....
Yeah. 
Hmmm.
Mike.

---


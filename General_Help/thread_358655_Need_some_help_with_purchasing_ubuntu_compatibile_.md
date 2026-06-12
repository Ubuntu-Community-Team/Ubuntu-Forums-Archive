---
title: "Need some help with purchasing ubuntu compatibile hardware"
date: 2007-02-11
forum: General Help
---

### Post by mich_r on 2007-02-11
Hi all

I am going to replace my old dusty PC with something fresh. I would like to buy something that let me stay with the best OS in the world ;)
After three hours of googling I have real mess in my head , I just cannot find a hardware configuration , which will work for sure in linux.

My dream PC is the following:
Motherboard: **[GIGABYTE GA-M61VME-S2]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2381&ProductName=GA-M61VME-S2")**
Processor: Athlon™64 X2 Dual-Core
VGA : integrated GeForce 6100
Sound: integrated REALTEK ALC883
LAN: integrated Realtek RTL8201 phy
HDD: any Sata II

I am asking you for any suggestions, especially if you have experience with the modules mentioned. Will the propertiary nVidia driver work (can't find straight answer nor on their website neither with google)? Will Sound work ? LAN? etc.

Thanks in advance.

---

### Post by dexter on 2007-02-11
> **mich_r said:**
> Hi all

I am going to replace my old dusty PC with something fresh. I would like to buy something that let me stay with the best OS in the world ;)
After three hours of googling I have real mess in my head , I just cannot find a hardware configuration , which will work for sure in linux.

My dream PC is the following:
Motherboard: **[GIGABYTE GA-M61VME-S2]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2381&ProductName=GA-M61VME-S2")**
Processor: Athlon™64 X2 Dual-Core
VGA : integrated GeForce 6100
Sound: integrated REALTEK ALC883
LAN: integrated Realtek RTL8201 phy
HDD: any Sata II

I am asking you for any suggestions, especially if you have experience with the modules mentioned. Will the propertiary nVidia driver work (can't find straight answer nor on their website neither with google)? Will Sound work ? LAN? etc.

Thanks in advance.

Ubuntu has realtek lan drivers by default (using them right now), cpu and graphics card should by no issue to. I can't tell anything about the rest though.

---

### Post by mich_r on 2007-02-11
Thanks dexter for your reply.

In the meantime I have found this:
[http://www.linuxquestions.org/hcl/showproduct.php?product=3741&cat=46]("http://www.linuxquestions.org/hcl/showproduct.php?product=3741&cat=46")
It is about similar mainboard, but with slightly different chipset - nForce 430 instead nForce 400. According to the post it has the same onboard GeForce6100 and works fine with nvidia drivers.

I think I could spend 25% more money for this board (even if I don't need extra PCI slots or firewire) if only I was sure that I would have no problems with it under ubuntu, but I also found this:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67734]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67734")
It is about some DELL system but nForce430 based so there is a chance that other boards with this one will be affected, isn't it? 

Please, ubuntu people, help me what to buy , I don't want to end with buying M$ OS after all, I do need ubuntu in my life...

---

### Post by reclusivemonkey on 2007-02-13
What is going to be the purpose of your machine?

---

### Post by mich_r on 2007-02-14
> **reclusivemonkey said:**
> What is going to be the purpose of your machine?
Home machine - mainly internet, multimedia (videos/music/photos). I work as a programmer and I do some development @home too. My aim is to have cool modern, silent, problem-free device - that's why I prefer this board (nice integrated components - 6 channel sound card, great nVidia 6100 with passive cooling etc)

---

### Post by housam on 2007-02-14
search  [this list ]("http://ubuntuforums.org/showthread.php?t=293798"), it has what you are looking for.

---

### Post by reclusivemonkey on 2007-02-14
I'm not sure what the state of 64 bit support is for Ubuntu; I certainly know that with things like Beryl it can cause some problems. For maximum compatability then you should stick to 32 bit architecture. You might want to ask in the Feisty forum though about the state of play with regards to 64 bit as Feisty is almost upon us.

As for the main body of your PC, I would be very suprised to find a motherboard which isn't supported. If you are working with multimedia though, I would check that you can handle multiple channels at the same time on your on-board sound card. I know this can be emulated in software, but multiple channel playback/recording is much better handled by a fully fledged soundcard. My soundblaster live wasn't much but its definitely worth the extra cash for that one feature. As long as you buy from a reputable source, you should find them willing to exchange components for you. A quick email before buying will help you establish this.

---

### Post by mich_r on 2007-02-14
housam: the topic you specified is about tools, not hardware? or I am missing something?

reclusivemonkey: I thought I could install 32-bit ubuntu on amd64 processor? At least it is possible with windows (as far I know those processors do hw emulation of 32-bit mode, opposite to infamous Itanium)

I did some research in my work place, and found that some of my colleagues have Gigabyte GA-M55PLUS-S3 in their PCs (with sempron64 but this should make no difference IMHO). I don't think they allow me to install ubuntu on their machines, but I thought that I would try Live-CD some weekend. It will allow me to check if the onboard devices are supported correctly, won't it?

---

### Post by housam on 2007-02-14
> **mich_r said:**
> housam: the topic you specified is about tools, not hardware? or I am missing something?

reclusivemonkey: I thought I could install 32-bit ubuntu on amd64 processor? At least it is possible with windows (as far I know those processors do hw emulation of 32-bit mode, opposite to infamous Itanium)

I did some research in my work place, and found that some of my colleagues have Gigabyte GA-M55PLUS-S3 in their PCs (with sempron64 but this should make no difference IMHO). I don't think they allow me to install ubuntu on their machines, but I thought that I would try Live-CD some weekend. It will allow me to check if the onboard devices are supported correctly, won't it?

You are right. I get it wrong. any way I suggest to visit this link : [http://www.system76.com/]("http://www.system76.com/") , they build pc specially for ubuntu.

---


---
title: "Recommendations for NAS"
date: 2015-02-26
forum: General Help
---

### Post by pfeiffep on 2015-02-26
I was a bit unsure where to post this question and decided on General Help. 

I'm planning on setting up a NAS attached directly to my router. My household consists of the following IT / IP devices:
[LIST=1]
[*]Mac Book Pro OSx Yosemite (10.10.2) 
[*]HP Desktop 64bit (both Ubuntu 14.04.2 and Windows 7) 
[*]Dell Laptop 64bit (both Ubuntu 14.04.2 and Windows 7) 
[*]iPhone 5 and 5s (ios 
[*]Apple TV 
[*]Verizon FIOS DVR 
[/LIST]


[LIST]
[*]Ideally I would like to have all the above devices able to use the NAS; but realistically 1 - 4 are essential. 
[*]Iv'e researched a bit and found that a majority of NASes don't list Linux as supported. 
[*]I'm interested to know whether a NAS supports different partition types? 
[*]Ease of use is important for #'s 1 & 4 
[/LIST]

Ideas? Thanks in advance!

Further searching uncovered WD my cloud ... although WD doesn't support Linux there's info about successful Ubuntu connection.  It's hard to believe that 'my cloud' is running a Linux kernel and WD doesn't directly support it.

---

### Post by CaptainMark on 2015-02-26
If you plan on buying a ready setup nas drive then it's not really so much of "Does it support Linux" it's more a case of "Does Linux support it" and the answer is almost guaranteed to be yes, I have yet to hear of a network storage option that Windows can handle but Linux cant so you've no worries there really. If you plan on setting up your own nas using a low-power pc and external HDD then you should be more selective about how you set it up, often you may have to use technically inferior methods (older protocols) to guarantee compatibility with more diverse systems. Something like a samba share will work with definitely 1-3 and a quick google search for iphone samba share, bought plenty of hits so that should be fine, Apple TV also shouldn't be hard. Not 100% on the DVR, they often have custom software which can be notoriously temperamental.

What's important to remember is that NAS just stands for network attached storage, so that on its own doesn't provide much useful information about how it is setup, often if you using a NAS plugged into your router it is actually the software on your router that determines how the NAS is addressed over the network. If you have a modern router, it tends to be very easy, just plug it in and go to your router settings to do some basic setup and your good to connect to it from the clients.

---

### Post by pfeiffep on 2015-02-26
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar825880_4.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=825880") 				 				 					 						 	[**[COLOR=#000000]CaptainMark[/COLOR]**]("http://ubuntuforums.org/member.php?u=825880") Thanks, I'm planning on purchasing 'ready to roll' rather than roll my own.  So far I've seen WD My Cloud reviews and how to make it work with Ubuntu. I'm hoping to get some input WRT my other requirements.

---

### Post by tgalati4 on 2015-02-26
[QNAP NAS]("https://www.qnap.com/i/useng/product/items_by_series.php?CA=3") devices run linux as an operating system, so I presume that they will work in a multi-OS environment.  They are not cheap, but then you get what you pay for.

Pick a suitable model and then read the reviews.

---

### Post by uwe-bungto on 2015-04-11
I have a Synology DS214se and a Dlink DNS 321. The D-link is end of life years ago, no support, does not support NFS 3, disk format is ext 2 it still works 

The DS214se is a year old, low priced, under powered, reliable, tons of software, good support,  disk format is ext 4. can be used as a cloud server. Linux support .

---


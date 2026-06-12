---
title: "IPblock better than Moblock?"
date: 2008-04-05
forum: General Help
---

### Post by chunchengch on 2008-04-05
I am not going to judge which one is better because I use both of them, but as you can see in the snapshoots attached, I am just wondering why IPblock keeps blocking attacks but Moblock doesn't. 

[ATTACH]64994[/ATTACH]       [ATTACH]64995[/ATTACH]

furthermore, IPblock works just flawlessly after installation, while when I tried to install Moblock 0.9rc from Synaptic with the instruction from [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/), I faced problem on connecting to the internet, because Moblock blocked everything, although I edited the /etc/moblock/moblock.conf and Uncommented WHITE_TCP_OUT="80 443", I still lost the connection from time to time. at last, I have no choice but to install the moblock-nfq_0.8-26+gutsy_i386.deb which I downloaded a couple of time ago.

any comment? thanks a lot!

---

### Post by Stabilityonitsown on 2008-04-05
lolz are you making this because I just created a post saying moblock was buggy as shizzles.

---

### Post by jre on 2008-04-05
> **chunchengch said:**
> I am not going to judge which one is better because I use both of them, but as you can see in the snapshoots attached, I am just wondering why IPblock keeps blocking attacks but Moblock doesn't.
Stop IPBlock and MoBlock will start blocking connections. At the moment MoBlock will be started at boot time and later you start IPBlock manually. This means that the traffic will first be checked by IPBlock and then by MoBlock. Now, how should MoBlock block anything if this connection was already blocked!?
There's no point in using both apps at the same time.

> **chunchengch said:**
> furthermore, IPblock works just flawlessly after installation, while when I tried to install Moblock 0.9rc from Synaptic with the instruction from [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/), I faced problem on connecting to the internet, because Moblock blocked everything, although I edited the /etc/moblock/moblock.conf and Uncommented WHITE_TCP_OUT="80 443", I still lost the connection from time to time. at last, I have no choice but to install the moblock-nfq_0.8-26+gutsy_i386.deb which I downloaded a couple of time ago.
As I already wrote in another thread the moblock 0.9 package uses more blocklists then the moblock-nfq 0.8 package. So probably with 0.9 your router is blocked. (You still get an IP because at that time during the boot MoBlock is not yet running). This results in problems which aren't solved with whitelisting the ports 80 and 443. To solve them you have to whitelist your router's IP or better your whole LAN:
E.g. if your IP was 192.168.178.12 your router's IP would probably be 192.168.178.1 and your local network 192.168.178.1-192.168.178.255. This means you should set in /etc/default/moblock:
```
WHITE_IP_IN="192.168.178.0/24"
WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD="192.168.178.0/24"
``` (onyl the WHITE_IP_OUT is really important for you). Of course you have to do that with your IP (check "ifconfig" for a start if you don't know it). Don't forget to restart moblock afterwards.

> **Stabilityonitsown said:**
> lolz are you making this because I just created a post saying moblock was buggy as shizzles.
Feel free to use IPBlock instead. It has a really nice developer, too.
Or just use nothing at all.
If you are interested in MoBlock just report the bugs and I'll have a look on it. Currently I'm not aware of any severe bugs. The only thing is that you have to whitelist some ports and/or IPs. Unfortunately there is no default configuration which fits for all people.
EDIT: Just saw your other thread: [http://ubuntuforums.org/showthread.php?p=4656759&highlight=moblock](http://ubuntuforums.org/showthread.php?p=4656759&highlight=moblock)
I've answered there.

---

### Post by chunchengch on 2008-04-06
> **jre said:**
> Stop IPBlock and MoBlock will start blocking connections. At the moment MoBlock will be started at boot time and later you start IPBlock manually. This means that the traffic will first be checked by IPBlock and then by MoBlock. Now, how should MoBlock block anything if this connection was already blocked!?
There's no point in using both apps at the same time.

I do start IPBlock manually when the system is totally up, at this moment, MoBlock is already started. before I  start IPBlock, I always check if there is anything blocked in MoBlock, unfortunately, nothing is blocked, then I start IPBlock, wow! it immediately blocks attacks.

maybe I don't need both IPBlock and MoBlock, but I think it won't be harmful to have both, since I believe they don't use the same blocklist, isn't it?


> **jre said:**
> As I already wrote in another thread the moblock 0.9 package uses more blocklists then the moblock-nfq 0.8 package. So probably with 0.9 your router is blocked. (You still get an IP because at that time during the boot MoBlock is not yet running). This results in problems which aren't solved with whitelisting the ports 80 and 443. To solve them you have to whitelist your router's IP or better your whole LAN:
E.g. if your IP was 192.168.178.12 your router's IP would probably be 192.168.178.1 and your local network 192.168.178.1-192.168.178.255. This means you should set in /etc/default/moblock:
```
WHITE_IP_IN="192.168.178.0/24"
WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD="192.168.178.0/24"
``` (onyl the WHITE_IP_OUT is really important for you). Of course you have to do that with your IP (check "ifconfig" for a start if you don't know it). Don't forget to restart moblock afterwards.

Thanks so much for this detailed explanation, I do need this to configure MoBlock, I will try it later.

As I said in my other thread, I am not very familiar with the setting of this kind of security softwares, I just want to protect my computer with a easy way, and I do really appreciate your efforts and contribution to provide such a good tool - MoBlock, thanks again!

---

### Post by jre on 2008-04-07
> **chunchengch said:**
> I do start IPBlock manually when the system is totally up, at this moment, MoBlock is already started. before I  start IPBlock, I always check if there is anything blocked in MoBlock, unfortunately, nothing is blocked, then I start IPBlock, wow! it immediately blocks attacks.

maybe I don't need both IPBlock and MoBlock, but I think it won't be harmful to have both, since I believe they don't use the same blocklist, isn't it?
I don't know which lists are exactly used by IPBlock, but I'm quite sure that they are (nearly) the same.
The MoBlock 0.9 package uses the following by default (see also at /etc/moblock/blocklists.list)
[www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz](www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz)
[www.bluetack.co.uk/config/bogon.gz](www.bluetack.co.uk/config/bogon.gz)
[www.bluetack.co.uk/config/dshield.gz](www.bluetack.co.uk/config/dshield.gz)
[www.bluetack.co.uk/config/fornonlancomputers.gz](www.bluetack.co.uk/config/fornonlancomputers.gz) (new in 0.9~rc2-9)
[www.bluetack.co.uk/config/hijacked.gz](www.bluetack.co.uk/config/hijacked.gz)
[www.bluetack.co.uk/config/iana-multicast.gz](www.bluetack.co.uk/config/iana-multicast.gz)
[www.bluetack.co.uk/config/iana-private.gz](www.bluetack.co.uk/config/iana-private.gz)
[www.bluetack.co.uk/config/iana-reserved.gz](www.bluetack.co.uk/config/iana-reserved.gz)
[www.bluetack.co.uk/config/level1.gz](www.bluetack.co.uk/config/level1.gz)
[www.bluetack.co.uk/config/level2.gz](www.bluetack.co.uk/config/level2.gz)
[www.bluetack.co.uk/config/Microsoft.gz](www.bluetack.co.uk/config/Microsoft.gz)
[www.bluetack.co.uk/config/proxy.gz](www.bluetack.co.uk/config/proxy.gz) (new in 0.9~rc2-9)
[www.bluetack.co.uk/config/rangetest.gz](www.bluetack.co.uk/config/rangetest.gz) (only up to  0.9~rc2-8)
[www.bluetack.co.uk/config/spider.gz](www.bluetack.co.uk/config/spider.gz) (only up to  0.9~rc2-8)
[www.bluetack.co.uk/config/spyware.gz](www.bluetack.co.uk/config/spyware.gz) (only up to  0.9~rc2-8)
[www.bluetack.co.uk/config/templist.gz](www.bluetack.co.uk/config/templist.gz)

Could you post (in CODE tages) the output of "moblock-control status" before you start IPBlock and after you do so. It *may* be that they conflict because they both mark packets.
Also please try a "moblock-control test" before and after you start IPBlock.

---

### Post by chunchengch on 2008-04-07
Is the MoBlock rc0.9 deb corrupted? I have been trying to install moblock from Synaptic since last night, but it can not be installed properly, because it can not find /etc/moblock/????.p2p (sorry,I forget the file name). weird!

---

### Post by jre on 2008-04-08
It should work.
What you describe hints to the fact that downloading (some of) the blocklists failed. Can you give me the complete output from synaptic and the end from /var/log/moblock-control.log if the problems persist?
You can also try a "moblock-control update" to fix this.

---

### Post by makovick on 2008-04-15
Just for your information, some time ago after trying out MoBlock, I ended up writing my own derivative, which eats much less memory, uses simpler algorithms (rbtrees are a bit overkill) and can also read gzipped ascii blocklists (such as the ones available at Bluetack.co.uk). From the outside, it should work the same way as MoBlock.

Feel free to try it out, any feedback is welcome.

[http://makovick.googlepages.com/nfblockddaemon]("http://makovick.googlepages.com/nfblockddaemon")

---

### Post by jre on 2008-04-15
oh dear, one more ;-) Now I started a link section to related projects such as yours at moblock-deb.sf.net.

I downloaded nfblockd and had a VERY quick look at it.
EDIT: quite interesting, it took me longer then I wanted, even installed it but still I have not really tested it YET.

As you write yourself most parts of the README are from Morpheus. How about the code? Which parts did you rewrite?

I'm especially interested in:

- Blocklist management (I hope you have not implemented the "merge range" bug from MoBlock 0.8 ): Is it possible to load multiple lists by just specifying them on the command line? E.g.:```
nfblockd ipfilter.dat level1.gz myownlist
``` or better ```
nfblockd /path/to/my/blocklists/*
```, where the lists may be in different formats?
How efficient/fast is the range merging (Can you compare it with MoBlock's)?

- The daemon part: So this is a real daemon, not just a process forked to the background (that's in my wishlist for MoBlock). Then I guess when you start it with your debian init script you get a correct feedback when and if it loaded!? And the "Starting netfilter blocking daemon: nfblockd" gets just finished with the "." after the daemon loaded the complete blocklist? - Oh I'd like that :-)

- Marking packets (instead of accepting/dropping them): starting nfblockd without options tells me that this is possible - so you already have implemented this feature?

It seems to me as if you don't handle the iptables insertion in your init script. Feel free to take mine from moblock-control.

So, really nice! From my perspective it would be best if you could merge your improved parts back to MoBlock. Of course I know that it's not that easy (both for you and for Morpheus) to handle someone others code instead of just having ones own project. Anyway, keep up your good work, more to follow.

Greetings
jre

---

### Post by makovick on 2008-04-15
> **jre said:**
> 
As you write yourself most parts of the README are from Morpheus. How about the code? Which parts did you rewrite?


The NFQUEUE interfacing code (nfqueue_cb and nfqueue_loop) is taken from MoBlock as I couldn't find any decent documentation on this matter anyway. The rest, which is basically just the blocklist handling and some setup code is mine.

> **jre said:**
> 
I'm especially interested in:

- Blocklist management (I hope you have not implemented the "merge range" bug from MoBlock 0.8 ): 

Don't know. Any testcase?
> **jre said:**
> 
Is it possible to load multiple lists by just specifying them on the command line? E.g.:```
nfblockd ipfilter.dat level1.gz myownlist
``` or better ```
nfblockd /path/to/my/blocklists/*
```, where the lists may be in different formats?

This is indeed possible.
> **jre said:**
> 
How efficient/fast is the range merging (Can you compare it with MoBlock's)?

I didn't benchmark it, as it was fast enough for me. The merging operates on the sorted range list and it should be pretty efficient.

> **jre said:**
> 
- The daemon part: So this is a real daemon, not just a process forked to the background (that's in my wishlist for MoBlock). Then I guess when you start it with your debian init script you get a correct feedback when and if it loaded!? And the "Starting netfilter blocking daemon: nfblockd" gets just finished with the "." after the daemon loaded the complete blocklist? - Oh I'd like that :-)

Yes, that's how it works. It also supports on-demand blocklist reloading and stats dumping (see README).

> **jre said:**
> 
- Marking packets (instead of accepting/dropping them): starting nfblockd without options tells me that this is possible - so you already have implemented this feature?

This stuff is taken from MoBlock (see above), so it is implemented. (well, should be... I didn't really test it much)

> **jre said:**
> 
It seems to me as if you don't handle the iptables insertion in your init script. Feel free to take mine from moblock-control.


I actually didn't need this to scratch my itch - I use my personal IPTables setup anyway so I don't need more magic scripts to mess with it :) Maybe later.

> **jre said:**
> 
So, really nice! From my perspective it would be best if you could merge your improved parts back to MoBlock. Of course I know that it's not that easy (both for you and for Morpheus) to handle someone others code instead of just having ones own project. 
First, I also thought about creating a patch for MoBlock, but after a brief inspection of its code, I realized that I'd like to throw almost all away, so I opted for my own (mini)project.
That's why I think that merging of my changes to MoBlock is neither likely nor reasonable.

---

### Post by jre on 2008-04-15
> **makovick said:**
> Don't know. Any testcase?
This is the complete bug report of the list range bug: [https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649](https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649)

The problem was with two ranges like these:
```
Sympatico test range:70.51.132.0-70.51.132.255
p2p Corrupt Data Senders:70.51.132.110-70.51.132.110
```
When they were merged only 70.51.132.0-70.51.132.110 was blocked, but not 70.51.132.111-70.51.132.255. This was fixed in MoBlock 0.9RC2.
Of course this bug did no harm if you were only using the nipfilter.dat since there are no overlapping ranges. It was affecting those who use multiple lists (level1.gz et al.).

---

### Post by makovick on 2008-04-15
> **jre said:**
> This is the complete bug report of the list range bug: [https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649](https://sourceforge.net/tracker/index.php?func=detail&aid=1818886&group_id=162910&atid=825649)

The problem was with two ranges like these:
```
Sympatico test range:70.51.132.0-70.51.132.255
p2p Corrupt Data Senders:70.51.132.110-70.51.132.110
```
When they were merged only 70.51.132.0-70.51.132.110 was blocked, but not 70.51.132.111-70.51.132.255. This was fixed in MoBlock 0.9RC2.
Of course this bug did no harm if you were only using the nipfilter.dat since there are no overlapping ranges. It was affecting those who use multiple lists (level1.gz et al.).

The merging works, but this example uncovered a silly bug in ascii PG format autodetection. I uploaded v0.4 with a fix in place.

You can verify the merging using the -v option:

Merging ranges: 70.51.132.0-70.51.132.255 70.51.132.110-70.51.132.110 into 70.51.132.0-70.51.132.255 (Sympatico test range; p2p Corrupt Data Senders)

---

### Post by krlhc8 on 2008-06-10
Just download Mobloquer, the front-end GUI to Moblock.  It is amazing!  I had numerous troubles with Moblock as it would block EVERYTHING, so I had to uninstall.  I installed Mobloquer, and everything works now.

```
sudo apt-get install mobloquer
```

FTW

---


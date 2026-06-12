---
title: "Can't connect to website unless I ping it"
date: 2005-10-30
forum: General Help
---

### Post by `GooZ´ on 2005-10-30
I've got a really strange problem here. I can connect to my (unencrypted) router, and surf to it. I can also ping every server, connect using kopete, check for new mails using gmail-notify, ... However I can't surf to any website unless I ping it first. In Windows (got a dual-boot system) everything works properly. Help would be appreciated :-)

---

### Post by zekolas on 2005-10-30
Sounds like some wierd DNS issue, what happens if instead of typing in the url you type in the ip adress? Will the page still not load unless you ping it? For example 66.35.250.150 is slashdot. 

I am assuming your have your computer set up for DHCP. Boot into windows and write down your ip adress, your default gateway, DNS server adresses and then boot into linux and run ifconfig and compair them to make sure they are the same. Try to set ubuntu up with a static ip adress and manually assign the DNS servers and default gateway to see if that helps.

---

### Post by zekolas on 2005-10-30
Actually some people seem to be having this problem and it is related to having ipv6 enabled and going through a router that does not support it yet.

try the following turn off ipv6 in firefox

type "about:config" in the address bar
then type "network.dns" and you will see the options shrink to only a few.
double click on the "ipv6 enable" and this will disable the function.

if that does not work do this

1. sudo nano /etc/modutils/aliases

Look for this line:
# alias net-pf-10 off # IPv6

Change the line to: (remove the #)
alias net-pf-10 off # IPv6

2. sudo update-modules

---

### Post by `GooZ´ on 2005-10-30
Thanks alot! This worked vor FF. The only problem is that it doesn't work for synaptic because I just change FF settings... However, I can surf now! It's great! Thanks!

---

### Post by rrkryder on 2006-04-15
Boy, this fixed my problem too.
I have been searching long and hard for this solution.
I am such a Linux newbie! But, I am enjoying my Breezy 5.10 very much.
I wish there was a button I could click on your response that would rate it 5 stars out of 5 stars so the post would join the upper eschalon of hits...If that makes any sense. In other words, make it a post that shows I got results...
oh, well. thanks!

---


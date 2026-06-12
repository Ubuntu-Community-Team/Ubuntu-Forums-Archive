---
title: "New build...Wifi connecting but without any network access"
date: 2017-04-21
forum: General Help
---

### Post by dazati7 on 2017-04-21
I just built an i7-7700 system with an AsRock Z270M-Pro motherboard to use with a remastered 16.04 image I  made myself that I've used on my old AMD A8-5500 system. Everything works except the wifi. It connects but only after selecting the network again from the list...after typing in the right password and hitting OK, it goes through the motions and just stops.

I'm getting an IP address (via DHCP) after it finally connects but I have no network access. I can't even ping my own router or gateway, let alone a DNS server (I.e., Google's 8.8.8.8). This occurs not only with the remastered 16.04 image I made myself, but also with a plain vanilla 17.04 live CD I downloaded just to test this problem.

To make matters even more complicated, I swapped out the WLAN card in my old system (which never had any connectivity issue).. same behavior. The new card, intended for the new system, works without a hitch in the old system. Didn't need any drivers either, it just worked out of the box, as expected.

What gives? I'm not sure if this could be a chipset issue, since the WLAN card is (somewhat) independent from that, even though Kaby Lake is pretty new. I don't think my PCIe x1 slot that it is in is bad, this happens in the other slot as well. I will install Windows 7 and use it for a few days to test that theory. I'm wondering if I should just remove the card and buy a compatible USB adapter? I'm wondering if it is something with the chipset that is intercepting how the WLAN cards--both old and new-- are working. I'm also wondering if my graphics card (which is in a PCIe x16 slot directly above the adapter) is giving off interference to the point that the adapter cannot function correctly. This is unlikely though because components are supposed to be more or less immune from interference these days. 

My old wlan card = Rosewill RNX-N150PCe
My new wlan card = Rosewill RNX-N600PCe v2.0

---

### Post by dazati7 on 2017-04-21
Should add that I've tried manual addressing too, no dice.

---


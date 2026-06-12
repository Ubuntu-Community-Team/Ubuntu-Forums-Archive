---
title: "What to do if copy hangs?"
date: 2007-12-26
forum: General Help
---

### Post by FrankVdb on 2007-12-26
Something nasty happened to me when I tried to copy 480 unique pictures from an SD card to my Ubuntu machine. After picture 70 or so, the copy process hung. Cancelling didn't work, so I killed Nautilus. Bad idea. Half of my desktop stopped working. Worst of all, I couldn't unmount my disk through the terminal. It kept saying the device was busy although the light had stopped flickering since the moment the copying process failed. The copy window persisted and couldn't be cancelled. So I removed my card and corrupted it by doing so.

I promised my mother-in-law to make a backup and I almost screwed up all her pictures just by using my Ubuntu box to copy them over. I managed to recover the pictures with Photorec, which is in the repos. It's command-line but fairly straightforward. Thank you Mr. Grenier! My mother-in-law thanks you on her bare knees.

Could this be a hardware problem (I mean the card, not my mother-in-law)? 

I noticed the first pictures copied very fast. I thought, wow, that card is fast. Then the copying started to slow down until it ground to a halt. When I couldn't cancel, I knew I had a problem..

---

### Post by anubhavrocks on 2007-12-26
First thing you should try to do is 
```
sync
``` and then maybe try to kill the misbehaving process and umount.

---

### Post by bvdborst on 2008-03-06
Hi all,

I encountered the same problem except is was my entire system (very fresh install) that hung, only option was hard reboot. It happened 3 times in a row, 2 x when using import wizard and 1 x direct copy.......anyone has a solution??, please help.....

---


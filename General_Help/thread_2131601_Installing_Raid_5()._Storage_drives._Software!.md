---
title: "Installing Raid 5(?). Storage drives. Software?!"
date: 2013-04-02
forum: General Help
---

### Post by Newuser901 on 2013-04-02
Best forum I could find for this.

Ubuntu 12.04

I can't find any instruction to do this properly. How do you simply make a set of raids while in the OS, with software or otherwise, so you can mount them and use them for storage. All instructions are making them for installations, and to boot their instructions are all incorrect as to what options are available when you partition and I can't figure out how to do it. I'm assuming software raid because I want what is most versatile to switch between installs and or hardware. Is there an easy way so I can switch it bewteen any upgrades in ubuntu relativlely easily. I'm planning on keeping to 12.04 currently. I"m using it currently to play DDO. Also for game storage for games I might try to get to work. I have a 90GB agility 3 SSD for my main install. One big partition currently but my windows virtualbox and wndows games are filling it up till I can get it up to get them off the main drive.(I just deleted windows entirely)

I have 3 250gig drives I want to make a raid 5 out of. Also is there a better raid for this circumstance?

One is a ST3250310AS(32mb?) drive I was thinking to make the parity disk if you can. The other two are WDC WD2500JD-00FYB0(16mb?). Is that a good way to do it. I was also looking to find which way to set them up. I"m not sure if there is a difference in their ability becuase of the differing ram on the drives. What would be most optimal.

---

### Post by SlugSlug on 2013-04-02
use mdadm skip to section 7 here [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by Newuser901 on 2013-04-02
That helped. 

IS there a way to organize them so that sdc is disk 0 in the array and sdb for instance is after it? Or does it matter with a raid 5?

---

### Post by SlugSlug on 2013-04-02
not 100% sure but I don't think it shows as disk0 just sdc etc.. The raid array will be /dev/md0

---

### Post by Newuser901 on 2013-04-02
I used the commands in teh example but create with only sdb sdc sdd with no number. it worked. But it's degraded(one drive is a bit old and fragile 8) using it up till it dies, Already knew this BTW.)It's currently recovering it. What I'm curious is is there some point to making sure the newer better 32mb cache drive is in any particular place in the raid or does it not matter in raid 5?

Oh wait. I switch to the disk utility that comes with 12.04 after creating to do the rest. 8) I'm now looking from it's perspective. It shows them as 0/1/2 in the same order as the letters used b/c/d. Was curious if ther was a way to reorganize without opeining the computer. 8) If not I probably don't care.

sdb is a WD 16mb cache(oldest I think), it's stable. sdc is the other newer 32mb cache(newest), stable. sdd is the other 16mb WD, questionable. 8)

When you go in the edit components screen for the array it shows the first 2 as fully synchronized and the third as partially synchronized.

---


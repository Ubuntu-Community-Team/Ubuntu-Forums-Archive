---
title: "Ubuntu on VirtualBox"
date: 2008-02-11
forum: General Help
---

### Post by cowdog88 on 2008-02-11
I installed ubuntu FF to my virtualBox.  I am able to hit the internet from my host still, but I cant hit the internet from my guest. Any advice?

---

### Post by jetsam on 2008-02-12
Have you enabled networking on the virtual machine?  If not, start virtualbox, select but don't start your machine, and click "network."  In the adapter 0 tab, check "enable network adapter", select "attached to NAT", and check "cable connected."  

Then start the virtual machine.  

It may work automatically, or you may have to configure networking with network manager or system-->Administration-->Network from within the Ubuntu guest as well.  Get it to use dhcp and turn off roaming if you need to.

---


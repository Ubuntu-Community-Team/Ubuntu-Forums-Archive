---
title: "vmware server and multiple nics"
date: 2007-03-22
forum: General Help
---

### Post by scotttkd on 2007-03-22
apparently during installation of vmware server on my edgy laptop I set up eth0, but  I failed to set up my wireless nic (ath0).  can anyone point my to the file and tell me what I need to add in order to activate the second nic??  I am a noob but pretty good at cutting and pasting script!  any help would be mucho appreciated!!!

---

### Post by banditti on 2007-03-22
no wireless under vmware server.

---

### Post by scotttkd on 2007-03-22
hi...thanks for the quick reply...I guess I am confused...I thought that I had read that if the underlying hardware was working/recognized by edgy, it would be available/recognized bythe vm.

---

### Post by banditti on 2007-03-23
[http://www.vmware.com/community/thread.jspa?threadID=6258&tstart=60]("http://www.vmware.com/community/thread.jspa?threadID=6258&tstart=60")

---

### Post by Redeyes_Gambit on 2007-03-24
What the post banditti is referring to says is you can't use *bridged* network for your wireless. You can however set the card up to use NAT (Network Address Translation) in VMWare. I currently (no, scratch that, did) have my wireless card set up to use NAT. To my guest OS (Windows 98se in my case) my wireless card looked like a standard wired NIC.

If you edit your configuration for you virtual machine to use NAT for the wireless card it should work. There should be a button on the "page" for your powered-down guest OS that allows you to edit virtual machine settings. I would go into greater depth but I currently don't have VMWare server installed and can't remember exactly what buttons to press. Should be fairly self-explanatory though. If you need help, just post :) .

---


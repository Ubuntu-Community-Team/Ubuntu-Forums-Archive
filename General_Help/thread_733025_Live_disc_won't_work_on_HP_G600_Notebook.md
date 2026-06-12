---
title: "Live disc won't work on HP G600 Notebook"
date: 2008-03-23
forum: General Help
---

### Post by dr_james2k on 2008-03-23
I've been using Ubuntu for about a year now and I've just got a new laptop - however I can't seem to install ubuntu on it.  I've tried both the 64-bit and 32-bit versions but after loading instead of showing the login screen the screen goes black then some weird blobs appear and seem to get brighter and brighter till I'm forced to reboot incase the screen gets burnt.  Anyone have any idea what the cause is or if there's any way round? (I was considering using the alternate disc but I'm worried that the same problem would occur on a normal start up).

[Some More info on the HP G6000]("http://h10010.www1.hp.com/wwpc/uk/en/ho/WF05a/21675-38187-38191-38191-38191-80247790.html")

Any information anyone has would be greatly appreciated - I'm so sick of vista.

---

### Post by pillu on 2008-03-23
Something similar happened to my friend on his new thinkpad. Did you try the safe graphics mode option in grub at bootup?

---

### Post by dr_james2k on 2008-03-23
Yeah, still gave me the black screen with the blobs.

---

### Post by dr_james2k on 2008-03-23
Got it working, seems to have been a problem with the CPU clock.  I needed to add the word noapic to the end of the kernal (Using F6 on the live disc) and it worked as it should.  I'm guessing when I get round to installing it I'll need to edit grub to make sure it runs with the noapic parameter added to the end of the kernal command.

---


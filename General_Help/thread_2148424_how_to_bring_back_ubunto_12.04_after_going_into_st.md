---
title: "how to bring back ubunto 12.04 after going into standby"
date: 2013-05-25
forum: General Help
---

### Post by tomsax on 2013-05-25
Ubunto on my laptop goes into standby when the screen is lowered and at low power.  How can I bring it back after this happens?  The only thing I seem to be able to do is press the power button to close it down completely and then reboot.

Thanks if you can help.

Tom

---

### Post by tomsax on 2013-05-25
I should say its an hp laptop.  In windows it has a 'windows button' to bring back from suspend but it doesn't work in ubuntu.

---

### Post by grahammechanical on 2013-05-25
Is the swap partition larger than the amount of system RAM? When Ubuntu is suspended the data in RAM is saved to the swap partition. If that is too small, then the data is lost and there is nothing to bring back from suspend.

Regards.

---

### Post by leunam12 on 2013-05-25
This is usually a video card problem. Go to system settings>Additional Drivers and check if there is another driver that you can use for your card.

---

### Post by tomsax on 2013-06-02
Thanks for that.  I've managed to resize the swap partition.  It was indeed smaller and I have now increased it to 4.2 GB (for 4 GB Ram).  Unfortunately I still seem to have the same problem remaining.  Any other ideas anybody.

---


---
title: "Cannot Boot or Install Ubuntu 12.10 from USB 3.0"
date: 2012-12-05
forum: General Help
---

### Post by TurtleKing on 2012-12-05
I keep getting a ton of errors reported from a busyboy program after the Ubuntu logo loading screen. I think it might have something to do with the motherboard GIGABYTE 990FXA-UD3, as it only lets me boot the Ubuntu USB from USB-ZIP. In addition, I have to plug it in one of the USB 2.0 ports because it will not read it from the USB 3.0 port.

Any suggestions?

---

### Post by C.S.Cameron on 2012-12-06
I was having trouble booting Ubuntu on a USB drive from USB3 also.
Not quite sure what fixed it but some things I tried were installing a non PAE kernel, which let me boot.

Then I tried the PAE kernel again and ended up booting into a kaleidescope screen.

Next I Tried booting PAE recovery mode and selected continue with normal boot and it worked fine.

Im quite sure that it is working off of USB3 because of the acceptable speeds.

I am still having no luck with normal PAE mode.
If you get it working, please let us know what worked.

---

### Post by TurtleKing on 2012-12-06
Well, I'm kind of a medium Ubuntu learner, so I'm not familiar with PAE kernal you are referring to. In addition, is this procedure you are referring to safe?

---

### Post by TurtleKing on 2012-12-06
Is there any information I can provide to help resolve the issue? I really miss Ubuntu :(

---

### Post by C.S.Cameron on 2012-12-07
What version of Ubuntu are you using?
Do you get the grub prompt when booting?
If so is the first option PAE?
If so the second option should be PAE...Recovery.
Try that and when you get to Continue... try that.

Above is safe.

---

### Post by TurtleKing on 2012-12-07
1.Ubuntu 12.10 64bit (AMD Quad Core processor)
2.No. It says loading Operating System, and then several commands related to Linux appear and take me to the loading screen.
3.Not applicable
4 Not applicable

---

### Post by C.S.Cameron on 2012-12-07
Hold down the shift key during boot, the grub menu should appear.
Select the Recovery option.
Select the continue with normal boot when given the option.

---


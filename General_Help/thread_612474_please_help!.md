---
title: "please help!"
date: 2007-11-13
forum: General Help
---

### Post by anemptygun on 2007-11-13
I have a usb mouse ( a razer krait to be exact). This mouse works fine when I first start up, but after a minute or two the mouse freezes. The rest of the computer keeps running, even the keyboard. what am I doing wrong?

---

### Post by Sef on 2007-11-14
Do you have a mouse that you could borrow?  If so, then use it in the USB slot, and see if it freezes.  If it does, then get a PS/2 mouse and check it out.   If it works then likely the problem is with your usb port.

---

### Post by anemptygun on 2007-11-14
> **Sef said:**
> Do you have a mouse that you could borrow?  If so, then use it in the USB slot, and see if it freezes.  If it does, then get a PS/2 mouse and check it out.   If it works then likely the problem is with your usb port.

See, thats what i thought too. It must be a port problem. But when i try out all the other ports, they all l act the same. I also have one of those usb to ps/2 converters and the mouse will not works at all with it. My old ps/2 mouse worked fine until i got this new one.

---

### Post by anemptygun on 2007-11-17
still nothing...

---

### Post by geraldm on 2007-11-18
Try the mouse again.  Then when it fails, look in /var/log/syslog and see if there are any
messages about the mouse, or the port that it was using, such as disconnect.
If the usb->ps2 converter came with the mouse, perhaps a change in protocol might work?
Also, at the start of use, note how many usb busses there are in use.  After the fail, check
if all the usb busses are still there.  If one is absent, it would point to a problem with 
the interrupt.

Gerald

---

### Post by anemptygun on 2007-11-20
lol sorry guys, i ran out of time to troubleshoot. So i just returned it and got a different one.

---


---
title: "Howto send CR LF in Terminal?"
date: 2008-06-19
forum: General Help
---

### Post by microscope on 2008-06-19
How do I send CR (ASCII 10) followed by LF (ASCII 10) in Terminal?

I am trying to talk to a microcontroller board that takes ASCII commands over the serial port, but requires both CR and LF to complete every commmand. (Works fine HyperTerminal in Windows, but I need to do this from a Linux box.)

It doesn't have to be Gnome Terminal--if there is another terminal program among the Hardy packages, I could install that, too.

Thank for any help,

microscope

---

### Post by sisco311 on 2008-06-19
Try something like:
```
echo -e '\0NNN' > /dev/*xyz*
```
where NNN is the ascii code in octal.

---

### Post by VMC on 2008-06-19
man echo

Something like this:
```
echo -e \\r
echo -e \\t hello
```

---


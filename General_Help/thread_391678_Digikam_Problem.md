---
title: "Digikam Problem"
date: 2007-03-23
forum: General Help
---

### Post by CheeseQueen452 on 2007-03-23
Digikam won't detect my camera for some reason. It was working before, but now I get an error message that a kernel or program may be using the device. I rebooted, but no luck. Wasn't there an update to Digikam recently? If so, that might explain it.... Is anyone else having this problem?
Also, I did drop my camera a couple of weeks ago, but I was still able to transfer my pictures/videos to my computer afterwards. HELP!!!

---

### Post by CheeseQueen452 on 2007-03-23
Screenshot attached....

---

### Post by llamakc on 2007-03-23
It's a bug with udev and rules. Here's a possible fix:

Open a Terminal and type:

```

sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

```Comment out the third line and add insert DIRECTLY beneath it this:

```

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```Save the file and close Gedit.

When you're done editing the first five lines should look like:

```

# udev rules file for libgphoto2 devices (udev < 0.98)
#
#BUS!="usb*", GOTO="libgphoto2_rules_end"
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
ACTION!="add", GOTO="libgphoto2_rules_end"

```

Now, restart udev:

```

sudo /etc/init.d/udev restart

```

---

### Post by CheeseQueen452 on 2007-03-23
It still didn't work :( At least it's a bug, & not my camera!! But even Picasa doesn't work.....

---

### Post by CheeseQueen452 on 2007-03-24
Any idea when this will be fixed? If anyone from the Ubuntu staff is reading this, PLEASE resolve this issue ASAP!

---

### Post by CheeseQueen452 on 2007-04-03
Still not fixed.... Is there anything I can do?

---

### Post by CheeseQueen452 on 2007-04-07
If anyone from Ubuntu Support is reading this, PLEASE fix this problem ASAP!!

---

### Post by llamakc on 2007-04-07
> **CheeseQueen452 said:**
> If anyone from Ubuntu Support is reading this, PLEASE fix this problem ASAP!!

The proper thing to do is file a bug report, or confirm an existing one. That's where stuff gets fixed at.

---


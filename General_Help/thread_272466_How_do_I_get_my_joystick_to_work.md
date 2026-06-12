---
title: "How do I get my joystick to work?"
date: 2006-10-06
forum: General Help
---

### Post by namelessone on 2006-10-06
I have a Logitech Wingman Extreme Digital joystick, and I don't know how to get it to work. I've looked at a lot of posts throughout the forums, but it seems no one can get these to work/don't want to help people who can't get them to work.

It should be noted that my joystick is not a usb joystick.

---

### Post by namelessone on 2006-10-07
What is with this question that no one wants to answer it? Is it really that hard?

---

### Post by jsandys on 2006-10-13
I am not a linux pro but I got my joystick working *after two weeks of experimenting* by reading the linux kernel joystick documentation:
[http://www.linuxhq.com/kernel/v2.4/10/Documentation/joystick.txt](http://www.linuxhq.com/kernel/v2.4/10/Documentation/joystick.txt)
and this thread:
[http://ubuntuforums.org/showthread.php?t=55173](http://ubuntuforums.org/showthread.php?t=55173)

If you are using the midi/gameport you might need to add _modprobe ns558_ with the other modprobes in the script from the above thread.
The Linux joystick doc also says you need _modprobe adi_ for your Wingman joystick.
By using _lsmod_ I found that the ns558 wasn't getting loaded so I added it to the script.

---

### Post by namelessone on 2006-10-13
Thanks! It looks like this stuff will really help me. I'll try it as soon as I have time.

---


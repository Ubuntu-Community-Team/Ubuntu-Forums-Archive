---
title: "Ubuntu 18.04 Backlit Keyboard not working"
date: 2019-01-25
forum: General Help
---

### Post by Redalien0304 on 2019-01-25
Have a Dell Latitude E6500 got a new Backlit Keyboard for it. Installed keyboard per instructions. Worked when i turned on laptop. Turned it in BIOS. Boot into Ubuntu 18.04 does not work? Have tried [https://www.dell.com/support/article/us/en/04/sln308123/how-to-configure-the-keyboard-backlight-time-out-interval-in-ubuntu-linux?lang=en](https://www.dell.com/support/article/us/en/04/sln308123/how-to-configure-the-keyboard-backlight-time-out-interval-in-ubuntu-linux?lang=en)
& Xset led, xset led on, xset led 3, from different sites.
Found a Fn right arrow-Key, with what looks like to me Keyboard Illumination. When i press the Fn Right-arrow appears to do nothing?

---

### Post by Redalien0304 on 2019-01-26
Bump anyone Backlit Keyboard??

---

### Post by Redalien0304 on 2019-01-26
Ok Solved now. Got what i  Needed from Here
[https://askubuntu.com/questions/1076393/dell-keyboard-backlight-is-not-working](https://askubuntu.com/questions/1076393/dell-keyboard-backlight-is-not-working)

Show the configured brightness:


$ cat /sys/devices/platform/dell-laptop/leds/dell\:\:kbd_backlight/brightness
0


See the maximum brightness:


$ cat /sys/devices/platform/dell-laptop/leds/dell\:\:kbd_backlight/max_brightness
4


Set the desired level of brightness (here: 4):


$ echo 4 | sudo tee /sys/devices/platform/dell-laptop/leds/dell\:\:kbd_backlight/brightness

---

### Post by smcnally2 on 2019-04-05
Upvoted the same article which helped with this Precision M6600 - 
That poster also mentioned this related info: 

> Slightly related: You might also want to configure the time-out interval for the backlight, using the stop_timeout setting. See also the article [How to Configure the Keyboard Backlight Time-Out Interval in Ubuntu Linux]("https://www.dell.com/support/article/de/de/debsdt1/sln308123/how-to-configure-the-keyboard-backlight-time-out-interval-in-ubuntu-linux?lang=en") in the Dell knowledge base.

I'm digging for ambient light sensor config options re the same keyboard backlight.

---

### Post by spyamine on 2019-09-22
Hi,

you could just use the following commands in the terminal

to turn it on

xset led 3 

and to turn it off

xset -led 3

---

### Post by EthanBoyle on 2020-05-17
Hello folks!

I've been working on this for a while now and tried all of the above mentioned to get my keyboard backlighting to even work. Silly as this might sound, and I truly do hope this helps someone, F10 on my keyboard turns the keyboard backlights on. It's kind of embarrassing to say that I struggled with this, but I'm reporting it to save another from the same struggle.

---

### Post by jaswithareddy on 2020-06-04
Hello!
I am using a Dell Latitude 3490. My keyboard back lighting stopped working after it came back from the service centre (display problems). I usually use Fn+F10 for back lighting but now it stopped working. What to do?
xset led on / xset led 3 are also not working.

---

### Post by CelticWarrior on 2020-06-04
> What to do?

Take it back to the service centre.

---

### Post by mkschultz on 2020-11-16
Just wanted to say "thank you" and confirm this solution also worked for me on Ubuntu 20.04.  My keyboard backlight was working fine... until it wasn't.  As the solution suggests, it was not that the backlight was *off* it was set to 0 brightness.

---


---
title: "Screen brightness Lubuntu 19.10 issues"
date: 2019-12-25
forum: General Help
---

### Post by ProDigit on 2019-12-25
Hello,
I made a complaint about the screen brightness a while back on Lubuntu 18.10, when running it on an Intel Atom N2000/N3000 series laptops, like the HP stream 11 or 14. The issue was that the screen brightness doesn't adjust the actual screen backlight (2 on picture), but the gain/gamma (1 on picture) instead, causing the screen to deform colors and over/under-saturate the colors.
On 19.10, Lubuntu finally has an option for screen brightness added in the GUI (2 in picture), however screen brightness controls (F2-F3) do not control these. They still control the image gain (1).
[IMG]https://i.ibb.co/M1xw17J/1.png[/IMG] 

Aside from this issue, the lowest the number 2 can get, equals the terminal setting of:
```
echo 300 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Meanwhile, I need my display at night, to go as low as: 
```
echo 50 | sudo tee /sys/class/backlight/intel_backlight/brightness
```.

[LIST=1]
[*]1 Where can I change change these parameters, so that the GUI can go as low as 50?
(On the stream 11, a screen brightness of 50 is still acceptable in the dark, where as a HP stream 14 being identical to the 11, save for screen size, probably needs closer to a setting of 100 to have equal brightness).

[*]2 Where can I change the F2-F3 controls to adjust display brightness, instead of gain?
[/LIST]

---

### Post by GhX6GZMB on 2019-12-25
A suggestion: look at Preferences -> LXQt Settings -> Shortcut Keys to see which commands are assigned to F2/F3.

Second, are you certain that your hardware supports backlight dimming? On slim, lightweight, low cost machines like these I have my doubts. It costs extra hardware, and a software solution is much cheaper/easier.

---

### Post by billkent on 2020-01-21
I have a similar issue on an Asus Zenbook Pro Duo...did you ever get resolution?

---

### Post by guiverc on 2020-01-31
@Prodigit You mention a complaint, I'd read that as a bug report on launchpad or report tracker so it reached developers, if so can you please provide details (link). Your post did remind me of something I recall on ask.ubuntu (another support site) but that's a user support site and doesn't fit my idea of 'complaint' (bug report, feature request by bug.tracker).  Links back can be useful.

It could also be you were the reason I was asked to do some (*Lubuntu*) testing on lxqt-backlight, lxqt-config-brightness etc though what I did was in the 19.10 development cycle (so 19.04 was the then stable release).  What I did find (*reading my summary*) was different laptops responded differently to the same commands, ie. different components/chipsets/firmware caused the same commands to react differently to others, eg. what worked on thinkpad/vaio laptops didn't work on latitude/inspiron which does make it hard to create a single interface that works for all devices.

---


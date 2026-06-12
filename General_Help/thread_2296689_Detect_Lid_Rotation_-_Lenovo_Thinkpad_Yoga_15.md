---
title: "Detect Lid Rotation - Lenovo Thinkpad Yoga 15"
date: 2015-09-28
forum: General Help
---

### Post by 7pde on 2015-09-28
[FONT=Helvetica Neue]I just picked up the Lenovo Thinkpad Yoga 15 (20DQ001KUS) for $799. Here is a link:[http://shop.lenovo.com/us/en/laptops/thinkpad/yoga-series/yoga-15/#tab-tech_specs](http://shop.lenovo.com/us/en/laptops/thinkpad/yoga-series/yoga-15/#tab-tech_specs)[/FONT]
[FONT=Helvetica Neue]I'd really like to get the tablet features working in Linux Mint 17.2. I have been doing some googling and found some old scripts below:[/FONT]
[FONT=Helvetica Neue][https://github.com/admiralakber/thinkpad-yoga-scripts](https://github.com/admiralakber/thinkpad-yoga-scripts)[/FONT]
[FONT=Helvetica Neue][https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)[/FONT]
[FONT=Helvetica Neue]With their help, I was able to put together a python script that polls my accelerometer values (found in /sys/bus/iio/devices/iio:device*) to figure out when the screen should be rotated. The difficult part seems to be detecting when the device should be in laptop or tablet mode. If I bend the lid past 180 degrees, or if I tilt the device on its side so that it is perpendicular to the ground, there is a light on my keyboard that shuts off and the keyboard itself is completely disabled. This appears to be a bios feature and indicates that there is definitely a sensor. This would be ideal, and it would solve all of my current problems.[/FONT]
[FONT=Helvetica Neue]Unfortunately, I have been unable to find any sensor readout in linux that would tell me when the computer should be in tablet mode. I need this to determine when autorotate should be turned on, when the touchpad/trackpad/keyboard should be disabled, and when I should launch or kill the onscreen keyboard app.[/FONT]
[FONT=Helvetica Neue]In the meantime, I'm using the lid's incline sensor (also found in /sys/bus/iio/devices/iio:device*). This works mostly, as It can detect tent mode and tablet mode. Unfortunately, the sensor is aligned to gravity, so it cannot tell the difference between laptop mode and stand mode (because the lid/screen is in the same orientation with respect to gravity).[/FONT]
[FONT=Helvetica Neue]The older scripts suggest that there is a special keycode in older models that is triggered when the mode changes from laptop to tablet and vice-versa. Unfortunately, I am not seeing any such keycode/scancode being thrown when I monitor xev/evtest.[/FONT]
[FONT=Helvetica Neue]In short, I'd like to be able to programmatically determine when the laptop screen/lid is opened more than 180 degrees. Can anyone help me with this?[/FONT]
[FONT=Helvetica Neue]My current script is linked below, if anyone else wants to see how I'm doing it (or if anyone else wants to make suggestions), I've only spent a day on it, so it's nowhere near finished. I'll probably publish it for GNU release at some later point in time for anyone else needing the same functionality.[/FONT]
[FONT=Helvetica Neue][https://gist.github.com/anonymous/5d2c2d2967eac8774b69](https://gist.github.com/anonymous/5d2c2d2967eac8774b69)[/FONT]
[FONT=Helvetica Neue]P.S. As an aside, I'm still trying to get full functionality from the ALPS touchpad. Using some psmouse DKMS installers, I have been able to get multi-touch capabilities like two-finger scroll and two/three finger tap working. However, the 3 physical buttons don't do anything (even in xev/evtest). Passing proto=imps to the psmouse module causes them to work , but breaks multi-touch functionality. If anyone would like to offer advice for that, I'd be grateful as well.[/FONT]

---


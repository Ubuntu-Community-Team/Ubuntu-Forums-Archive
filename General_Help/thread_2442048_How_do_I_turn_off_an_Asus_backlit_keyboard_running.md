---
title: "How do I turn off an Asus backlit keyboard running 20.04"
date: 2020-04-29
forum: General Help
---

### Post by MPacheco on 2020-04-29
I've overstepped my knowledge and hoping someone can please help me back out my mistake.

I have a laptop, Asus Vivobook F512D on which I installed Ubuntu 20.04 alongside Win10. In Win10, the keyboard can be backlit, but I couldn't get the keyboard to light up in Ubuntu. I tried several remedies but none seemed to work, less one: in terminal I entered 'sudo /etc/acpi/asus-keyboard-backlight.sh'. I was a little apprehensive about using the 'sudo' command but thought I was being too skiddish so I thought I'd give it a shot. To my pleasure, the keyboard lit up, and that's great in the evening but now I can't turn off the backlit keyboard unless I power down the laptop. When I power up again, the keyboard remains lights back up. How can I negate the command I entered to turn off the keyboard?

Here's the READ ONLY file I found at the end of the command:

#!/bin/sh


# this directory is a symlink on my machine:
KEYS_DIR=/sys/class/leds/asus\:\:kbd_backlight


test -d $KEYS_DIR || exit 0


MIN=0
MAX=$(cat $KEYS_DIR/max_brightness)
VAL=$(cat $KEYS_DIR/brightness)


if [ "$1" = down ]; then
	VAL=$((VAL-1))
else
	VAL=$((VAL+1))
fi


if [ "$VAL" -lt $MIN ]; then
	VAL=$MIN
elif [ "$VAL" -gt $MAX ]; then
	VAL=$MAX
fi


echo $VAL > $KEYS_DIR/brightness


I hope it's helpful. Any guidance is greatly appreciated. Thank you, in advance.

---

### Post by MPacheco on 2020-04-29
OKAY! Contrary to every youtube and webpage I read, it's not the FN + F3 to light up the keyboard and FN + F4 to turn it off. FN + F7 cycles through off to brighter and brighter and then dimmer and dimmer back to off. Thanks all for allowing me to post and work through this.

---

### Post by Impavidus on 2020-04-29
I don't know about Asus laptops, but I can tell what that script is doing. Whenever you run that script with the word "down" as its first argument, the brightness is reduced by one:```
sudo /etc/acpi/asus-keyboard-backlight.sh down
```When you run the script in any other way, the brightness is increased by one. And it would be possible to change brightness in other ways by writing the requested brightness to the file **/sys/class/leds/asus::kbd_backlight/brightness** using any value between 0 and the value in **/sys/class/leds/asus::kbd_backlight/max_brightness**. Now I guess that the keys to control brightness are somehow mapped to commands using that script.

Those files aren't real files. The /sys/ directory contains a pseudo-filesystem, which is used to gain access to many properties of the running system.

---


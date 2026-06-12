---
title: "Beaglebone Black: No GPIO Activity on 12.04?"
date: 2014-05-22
forum: General Help
---

### Post by Tim_Limon on 2014-05-22
Hello,
I'm hoping to find a little help, I've been googling and trying all permutations for a week now here's the issue:

I have a BBB Model A5C with Ubuntu running on the sim.  I cant seem to get any of the python examples to actually blink the LED's I've been following the Adafruit tutorial at "https://learn.adafruit.com/blinking-an-led-with-beaglebone-black/writing-a-program" with no luck.  I can get the LEDs to blink using "sudo sh -c 'echo 0 > value' " in both the /sys/leds and /sys/gpio directories so I know the board is capable, but the simple python script given in the tutorial does nothing.  I've even tried this attached script with no result as well. 



Thank you for taking the time to read this, I would appreciate any help you might offer.

--Tim

---


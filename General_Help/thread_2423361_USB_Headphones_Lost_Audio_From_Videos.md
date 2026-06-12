---
title: "USB Headphones Lost Audio From Videos"
date: 2019-07-22
forum: General Help
---

### Post by Smallwheels on 2019-07-22
Tonight I was watching a Netflix show. When the show ended the audio stopped going through my USB headphones and it came out of the speakers. Nothing was touched.
I unplugged them and plugged them in again and the audio didn't switch from the speakers to the headphones. I used the volume control on the headphones to see if it needed adjusting.
Interestingly the beep noises that identify that the adjustment is changing did go through the headphones. The light on the headphones also remains on. I tried switching the USB headphones to the other two USB ports. There was no change. 

I restarted the computer and that didn't fix it. 

I'm using the Google Chrome browser. 

Earlier today I used an HDMI cable to attach to a TV set. That was the first time doing it. The HDMI cable was unplugged long before watching the Netflix program. 

I plugged in using ear buds with the 3.5mm jack and the sound does switch to them as the computer speakers have turned off. 

I also plugged in an external USB drive into the USB port and it worked too. 

I plugged the headphones into a different laptop and they worked just fine.

I also tried using the Firefox and Brave browsers. Neither of them made the sound go to the USB headphones. What do you think is happening? Has this happened to others? 
Please let me know how to fix this.

---

### Post by VMC on 2019-07-22
Look at Menu>Preferences>Sound>Output

---

### Post by Smallwheels on 2019-07-22
> **VMC said:**
> Look at Menu>Preferences>Sound>Output

Thank you for the information. I went to that spot and looked at the page. The internal audio speakers were listed. Then I plugged in the USB headphones. They then appeared in the list of audio devices. I selected the headphones and nothing happened. I turned the button on and off and nothing happened. Next I selected the internal speakers. They continued to play. Then I selected the headphones again. The headphones then turned on. 

What do you believe triggered the machine to suddenly just stop using the USB headphones?

---

### Post by VMC on 2019-07-22
You might try looking at ```
[COLOR=#242729][FONT=Consolas]dmesg -wH
```[/FONT][/COLOR] at time of use. Then just plug in/out your usb headphones an observe dmesg outputs.

---


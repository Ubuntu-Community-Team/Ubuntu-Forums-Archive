---
title: "Palm pilot problem"
date: 2007-11-25
forum: General Help
---

### Post by ksadil on 2007-11-25
Hello,

I have been able to synchronise my Palm Z22 with Gutsy, but it intermittently fails. When it fails I notice the device that gets configured has changed from ttyUSB0 &ttyUSB1, to ttyUSB2 & ttyUSB3 as observed in /var/log/messages.

killing off gpilotd processes, and resetting the device in gnome-pilot seems to work (sometimes)


A reboot normally fixes it, but this is reminiscent of W98, don't really want to resort to that sort of thing. Any ideas on a workaround.

Any ideas to help would be appreciated.

Thanks,
Kim

---

### Post by darkazurka on 2007-12-19
I'm not so far daring to try any own solutions for it to synchronise. Giving me an error summarised as: can't synchronise on port "/dev/pilot" . I have requested old-style usbserial 'ttyUSB' syncing. (have I? what does that mean?) . I might need to select an usb: device. Hmm. In my attachment is an image. 

Do you have a similar in your situation?

---

### Post by ksadil on 2007-12-19
I think I solved that problem by adding the following lines to the file /etc/modules:

usbserial
visor

They will make the extra modules get loaded at a reboot. They can be loaded without a reboot by using the following commands:

sudo modprobe usbserial
<enter your password>
sudo modprobe vsor
<enter your password>


My system does synchronise, but after syncing the first time, I think the usb port is not released, making it try another one. (my theory at least) To sync again, I have to reboot or kill some processes. 

Regrads,
Kim

---

### Post by darkazurka on 2007-12-20
Yes, ksadil: ```
sudo modprobe visor
``` was a vital part to help me sync my palm z22.

I found a solution from this thread to sync my palm z22 device: [http://ubuntuforums.org/showthread.php?t=418979](http://ubuntuforums.org/showthread.php?t=418979)

The following is something I posted as thanks for something that helped me out:
> trents: Your 3# post helped me to sync my Palm Z22 . The lines I followed to get it to work were:
[QUOTE]If I open terminal and issue the command "sudo modprobe visor" before attempting the hotsync then J-pilot is able to locate the palm device. I then tap the hotsync button on my Palm Z22 screen and then I mouse click on J-pilot's hotsync button.

very helpful (!!), after I set the device in preferences to /dev/ttyUSB1 .
I had also installed a program in synaptic called "pilot-link". I don't know if that helped the situation, but I think it did help.[/QUOTE]

---


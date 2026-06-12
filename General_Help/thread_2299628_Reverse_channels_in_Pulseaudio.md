---
title: "Reverse channels in Pulseaudio"
date: 2015-10-20
forum: General Help
---

### Post by Evil Wayz on 2015-10-20
My favorite Bluetooth headset reverses channels.  I'm looking for a way to add an additional option to my "Output" tab in Sound Settings.  I came across this:

```
edit /etc/pulse/default.pa
``` 
then add
```
load-module module-remap-sink sink_name=reverse-stereo master=0 channels=2 master_channel_map=front-right,front-left channel_map=front-left,front-right
```

I don't like just editing or copy and pasting things into the command line without understanding what I'm doing, So I'm wondering if one of y'all would tell me if this is correct or if there is an easier way of doing things.
Thanks.

---

### Post by Bucky Ball on 2015-10-20
If you're uncertain, backup the file first:
```

sudo cp /etc/pulse/default.pa /etc/pulse/default.pa.original
```

... then:

```
sudo nano /etc/pulse/default.pa
```

... and add the line:

```
load-module module-remap-sink sink_name=reverse-stereo master=0 channels=2 master_channel_map=front-right,front-left channel_map=front-left,front-right
```

... where you were told to on whatever web page you are using. 

If things don't work and you can't get to the file to remove the offending line, then:

```
sudo mv /etc/pulse/default.pa.original /etc/pulse/default.pa
```

... will move the original file back and things will be as they were.

(PS: Please use code tags for terminal stuff, see last link in my signature. Thanks. :))

The command you provide looks like it is intended to reverse the left and right, yes, but I am no expert. I very much doubt this will do any serious damage to anything but audio, and that is also doubtful ... and fixable if you move the original file back or retract your changes.

---

### Post by Evil Wayz on 2015-10-20
Sorry about that, edited to include code tags. 

Ok, this gives me a nice remapped audio option.  I had one additional question, I restarted Pulseaudio and everything is working perfectly.  IS there something I need to add additionally for permanence when i restart my system for kernel upgrades/video upgrade drivers etc?

---

### Post by Bucky Ball on 2015-10-20
> **Evil Wayz said:**
> IS there something I need to add additionally for permanence when i restart my system for kernel upgrades/video upgrade drivers etc?

Possibly the stuff of another thread, but if you are talking about the change you made to the pulseaudio file, no, that will stick after reboot. If it doesn't, post back here. If it does and this support issue is solved, please see the first link in my signature to help others and post a new thread with a descriptive title regarding any further issues and questions.

Good luck. :)

---

### Post by Yellow Pasque on 2015-10-20
> **Evil Wayz said:**
> Is there something I need to add additionally for permanence when i restart my system for kernel upgrades/video upgrade drivers etc?

No. You should be set. If there's an upgrade to pulseaudio that installs a new version of the default.pa file, you may be prompted to keep the old file or install a new one. (Example: 
[https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/](https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/) )
You can either keep your version of the file or accept the new version and add your custom line back into it. I'd recommend the latter.

---

### Post by Bucky Ball on 2015-10-20
> **Temüjin said:**
> No. You should be set. If there's an upgrade to pulseaudio that installs a new version of the default.pa file, you may be prompted to keep the old file or install a new one. (Example: 
[https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/](https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/) )
You can either keep your version of the file or accept the new version and add your custom line back into it. I'd recommend the latter.

Good point and yes, the latter. Update to the newer file, add the line. Good luck. :)

---

### Post by Evil Wayz on 2015-10-25
Ok, ever since I did this I can only use bluetooth for 15 minutes or so before it freezes any program running audio.  I then have to shut down bluetooth, manually change the sound settings back to built in audio, and then attempt to get bluetooth to restart, which sometimes works and sometimes doesnt.

---

### Post by Evil Wayz on 2015-10-25
I did this ```
rm -r ~/.config/pulse; pulseaudio -k
``` And bluetooth has been working for an hour so far.  I'm guessing the config file got corrupted somehow.

---

### Post by Evil Wayz on 2015-10-29
Turns out I was wrong, it was a bad usb hub that was unmounting itself from time to time.  So bluetooth would get stuck.  Plugged the dongle directly into the box and everything is good.

---

### Post by Evil Wayz on 2016-05-04
OK this doesn't work in 16.04.  I have lost my reversed channel profile, and my equalizer profile.  Any ideas?

---


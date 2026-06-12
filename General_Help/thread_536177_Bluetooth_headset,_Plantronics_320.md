---
title: "Bluetooth headset, Plantronics 320"
date: 2007-08-27
forum: General Help
---

### Post by cfexrun on 2007-08-27
Hi everyone. I've looked at all the other bluetooth threads I can find, and so far none have helped much. My dongle is a Trendnet, and lsusb reports Bus 002 Device 002: ID 1310:0001 Roper Class 1 Bluetooth Dongle. The headset is a Plantronics 320. Anyway, I can pair it using either gbtsco or btsco -r, and so long as it's the first time I've paired it the applet will request my PIN, but the headset never seems to respond, staying in pairing mode until it eventually times out. This is all under 7.0.4. Oh, and whenever I'm trying to connect it I get an error message saying that it failed to connect to the sdp server and the reason given is that it timed out.

Any ideas?

Thanks,
Fargo

---

### Post by wieman01 on 2007-08-28
I have got a Plantronics 590 and I was eventually able to pair it on Kubuntu. There is a solution posted here:

[http://ubuntuforums.org/showthread.php?t=486087]("http://ubuntuforums.org/showthread.php?t=486087")

If you still have problems, let me know.

---

### Post by cfexrun on 2007-08-28
Ahh, thanks for the input. I'll give that a shot and post how it went.

---

### Post by cfexrun on 2007-08-28
No go still. I guess I could try the bluetooth-alsa stuff, but it seems like a big hassle to patch and build a kernel for something that seems so relatively trivial.

Here's what I did and the results-

fargo@darkseid:~$ sudo rm -r /var/lib/bluetooth/00\:0B\:0D\:06\:54\:0A/
Password:
fargo@darkseid:~$ passkey-agent --default /usr/bin/bluez-pin 
Can't register passkey agent
Passkey agent already exists
fargo@darkseid:~$ btsco -v 00:03:89:D6:CA:FB
btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: Connection timed out
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Operation now in progress

I am prompted for the pin, via the Gnome bluetooth applet, and it seems to accept it and says it's bonded, but I can't seem to really make any progress from there. If I press the button on my headset that would normally request a connection, post pairing, then hcitool con outputs this-
Connections:
        > ACL 00:03:89:D6:CA:FB handle 2 state 1 lm SLAVE
But I don't get any sound, and after a time the headset makes the timeout beep and the connection is no longer listed.

Anyone other ideas?

---

### Post by wieman01 on 2007-08-28
Could you possibly get ahold of another headset and test that one?

---

### Post by cfexrun on 2007-08-28
Good idea. I can try my roommate's this evening. He has a Voyager 510. I know that my headset was working under Windows, but I guess it could be something weird with it.

---

### Post by cfexrun on 2007-08-28
So... different problems.
I got the Voyager 510 to pair, but still no sound anywhere, and it still eventually timed out, dropping the connection. It was, however briefly, at least using SCO, but check out the info-

fargo@darkseid:~$ hcitool con
Connections:
        < SCO 00:03:89:FB:40:BE handle 0 state 5 lm SLAVE 
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm SLAVE 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 0 state 5 lm MASTER 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm MASTER 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm SLAVE ENCRYPT 

I can't begin to understand what's going on right now. Any other thoughts?

---

### Post by wieman01 on 2007-08-29
> **cfexrun said:**
> So... different problems.
I got the Voyager 510 to pair, but still no sound anywhere, and it still eventually timed out, dropping the connection. It was, however briefly, at least using SCO, but check out the info-

fargo@darkseid:~$ hcitool con
Connections:
        < SCO 00:03:89:FB:40:BE handle 0 state 5 lm SLAVE 
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm SLAVE 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 0 state 5 lm MASTER 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm MASTER 
fargo@darkseid:~$ hcitool con
Connections:
        < ACL 00:03:89:FB:40:BE handle 6 state 1 lm SLAVE ENCRYPT 

I can't begin to understand what's going on right now. Any other thoughts?
First you might also want to try another dongle if you happen to have one.

Second I really think you had it working, could it be that you have to turn up the volume? This is how you can test the device from command line:
> aplay -B 1000000 -D plughw:Headset /usr/share/sounds/login.wav
Source: [https://help.ubuntu.com/community/BluetoothAudio?highlight=%28bluetooth%29]("https://help.ubuntu.com/community/BluetoothAudio?highlight=%28bluetooth%29")

You're close.

---

### Post by cfexrun on 2007-08-29
I did actually try it with my roommate's dongle as well, though I didn't note the details. I'll try your suggestion when I get time tomorrow, thanks for all the guidance.

---

### Post by cfexrun on 2007-09-04
Well. Hot damn. Looks like my dongle would lockup after the initial connection, an issue I ran into under Windows but thought was just a software issue. The rest of the key was finding the right channel. Searching with sdptool gave me that, so i could tell btsco how to connect rather than guessing or letting it default to channel 2. The speaker part works great, tested it with Skype, but aside from the odd word my mic message seems to play back with huge bursts of static. Still, massive progress.

Thanks again!

---

### Post by wieman01 on 2007-09-05
> **cfexrun said:**
> Well. Hot damn. Looks like my dongle would lockup after the initial connection, an issue I ran into under Windows but thought was just a software issue. The rest of the key was finding the right channel. Searching with sdptool gave me that, so i could tell btsco how to connect rather than guessing or letting it default to channel 2. The speaker part works great, tested it with Skype, but aside from the odd word my mic message seems to play back with huge bursts of static. Still, massive progress.

Thanks again!
I had a similar issue with the latest version of Skype (v1.4?), so I reinstalled version 1.3 which works ok.

---

### Post by cfexrun on 2007-09-11
For anyone with similar issues, I used alsamixer (alsamixer -c 1 in my case) to raise the mic volume, and that seems to have resolved the static issues.

---


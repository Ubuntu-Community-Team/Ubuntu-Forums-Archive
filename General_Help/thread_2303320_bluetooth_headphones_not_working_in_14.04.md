---
title: "bluetooth headphones not working in 14.04"
date: 2015-11-17
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-11-17
Gateway laptop. 14.04 LTS, Trusty, 32 bit. Plain Openbox. Built in audio circuitry that controls the speakers is broken so all I can get from them is noise. I say it is the control circuitry rather than the speakers themselves because I tried plugging in headphones directly to an audio jack and got the same noise. Bluetooth speakers from a usb bluetooth dongle worked fine under Windows in June. Now I'm trying to use a new dongle ('cause I can't find the old one) and a new set of headphones (ditto, and also 'cause I want headphones, not a speaker). But I can't get them to work. I've installed blu this and blu that until I'm blu in the face.

With blueman-manager the headphones are shown as:
 
SPORT-S9
keyboard
00:00:00:00:3F:B0

When I right click and click "headset service" I get:
"Connection Failed: Connect failed"

When I right click and click "audio sink" I get:
"Connection Failed: Stream setup failed"

When I right click and click "setup" I get a window titled "Bluetooth Assistant" with "Connect to: headset service" preselected. When I click "forward" I get:
"Device added successfully, but failed to connect"

If I do setup and, instead of "headset service" I check "A2DP sink (lol, sounds like porn)" I get the same "Device added successfully, but failed to connect" message.

When I again, in the original window, right click and click "audio sink" I again get:
"Connection Failed: Stream setup failed"

From the "device" menu if I click "refresh services" I get:
"Host is down" What host is it talking about? This is all purely local stuff.

At some point, I think when I initially paired the usb bluetooth audio dongle with the headphones, the headphones went "beep beep". I looked all around and Road Runner wasn't there, so it must have been the headphones, but that is the only noise they've made.

Pavucontrol under "output devices", with "show:" set to "All", has never shown any choice in the dropdown menu but "speakers".

There are a lot of threads out there discussing similar problems, many of them attributing them to upgrading to 14.04. This thread:

seems most similar to my issue but
"pactl load-module module-bluetooth-discover"
didn't change anything for me.

INFO ADDED LATER:
I read this page:
[https://github.com/blueman-project/blueman/issues/158](https://github.com/blueman-project/blueman/issues/158)
and tried ```
pactl load-module module-bluetooth-discover
```and got ```
Failure: Module initialization failed

```Also tried ```
pactl load-module module-bluetooth-discover 23
```and got the same result. I haven't a clue what "23" means in this context but what I was copying had it after the command, albeit appearing to be on a separate line, so I thought it worth a try.
ADDENDUM #2:
In blueman-manager, I deleted the device, put it in pairing mode, and searched again, to re-list it. A few more steps I forgot to record - I think "setup" and "a2dp sink" - and next time I opened pavucontrol, and the headphones were listed, and then I fiddled with pavucontrol and the they started working.

BUT, after hearing them work, I rebooted and now I'm back to square 0. Pavucontrol doesn't see them. So either there is some way to explicitly write unsaved config settings to a config file somewhere that is consulted during boot or, if it supposed to be automatic (which I had assumed), it isn't happening, which makes me wonder if there is a permission issue somewhere.
ADDENDUM #3:
Running blueman-manager in a terminal when I get the "failed to connect" message in the gui and close the second blueman window (Assistant) with "ok", I get this in the terminal:
```
_________
save (/usr/lib/python2.7/dist-packages/blueman/plugins/config/File.py:117)
Saving config 
Exception AttributeError: "'NoneType' object has no attribute 'Bus'" in <bound method File.__del__ of <File object at 0xb5843acc (blueman+plugins+ConfigPlugin+ConfigPlugin at 0x9e0da80)>> ignored
_________
child_closed (/usr/lib/python2.7/dist-packages/blueman/Functions.py:153)
['/usr/bin/blueman-assistant', u'--device=00:00:00:00:3F:B0'] closed 

```When I run ```
stat /usr/lib/python2.7/dist-packages/blueman/plugins/config
```the line reflecting perms is ```
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
```I was thinking of chowning it to my plain user.

The command:```
pactl load-module module-bluetooth-discover
```usually fails with the error message:```
Failure: Module initialization failed
```but not always. Occasionally it will work and then it will output a 2 digit number (eg. "22") on the next line. When it does, I can then follow this procedure:
> * Right-click on the device in blueman, select "connect to audio sink"
* Open Puleseaudio volume control (pavucontrol), browse to  "configuration" , use the dropdown to turn the Built-in audio profile  "off"
* use the other dropdown to set the bluetooth device to use A2DP
as suggested by Luke Schlather             on 2015-06-07 here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1274613/comments/22](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1274613/comments/22)
That works for the remainder of that session but if I reboot I'm back to square 0 again.

I've also tried the version of blueman in this ppa:
[https://launchpad.net/~cschramm/+archive/ubuntu/blueman](https://launchpad.net/~cschramm/+archive/ubuntu/blueman)
which solved the problem for some people. But not for me.

 I have 2 gigs free on this partition (which the whole system is on, /, ~, and all), so I don't think this is one of those weird errors that come from running out of space.

UPDATE - SOME PROGRESS MADE:
I did this:

purged all blueman*

installed gnome-bluetooth

added this line:
Disable=Headset
to
/etc/bluetooth/audio.conf
just below "[General]"
(credit to Zuker - [http://ubuntuforums.org/showthread.php?t=1761433&p=10864337#post10864337](http://ubuntuforums.org/showthread.php?t=1761433&p=10864337#post10864337))
with the intent of forcing the headphones
to use a2dp by default. I don't
understand the logic of this but
it seems to work.
I put the following in a script that is called indirectly by
~/.config/openbox/autostart.sh:

pactl list | grep module-bluetooth-discover || pactl load-module module-bluetooth-discover
nohup pavucontrol &
nohup gnome-control-center bluetooth &

After a few rounds of settings and rebootings I now have to do this to start the headphones to working after relogging or rebooting:

In the "Bluetooth" window that comes from the command "gnome-control-center bluetooth", under "Devices" on the left, I click the name of the headphones (SPORT-S9 in my case) and on the right a line "Connection Off" appears. I click on "Off" and it changes to "On" & all is shiny. Headphones start working and are defaulting to the right "profile" - A2DP.

It looks like pavucontrol is no longer needed for this purpose (though it is still a dandy volume control of course).

If I can figure out the command line equivalent to the above point and click procedure I can automate it. Or maybe there is a config file somewhere that would do the same. Possibly /etc/bluetooth/audio.conf could do this. I need to find a manual for the settings possible there but so far I haven't.

This is my only working box atm, so I'd really like to get sound working somehow. If I have to buy my way to a solution I suppose somebody probably makes wired usb headphones, but I'd much rather get my wireless set working. Because, besides the merits of wirelessness and being paid for, they have the supreme virtue of being here now, as opposed to obtainable through UPS after a period of silent waiting.

I'd appreciate suggestions. Thanks for reading.

---


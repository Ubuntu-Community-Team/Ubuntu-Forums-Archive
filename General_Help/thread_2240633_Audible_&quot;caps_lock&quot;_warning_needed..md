---
title: "Audible &quot;caps lock&quot; warning needed."
date: 2014-08-21
forum: General Help
---

### Post by benawhile on 2014-08-21
I have 14.04
 

 I want an audible warning when caps lock is pressed accidentally.
 

 I have found two posts that recommend :
  System &#8594; Preferences &#8594; Keyboard &#8594; Accessibility &#8594; Audio Feedback and tick the "Beep when a toggle key is pressed" box.  
 But since 13.10 it seems keyboard accessibility was not available this way.


 There are recommendations to install &#8220;Gnome Tweak Tool&#8221; which I have done, it's just called &#8220;Tweak Tool&#8221; in my applications list, but I cannot find &#8220;accessibility&#8221; in Tweak Tool. There is a tab for &#8220;caps lock under &#8220;typing&#8221; but I don't think any of the choices are to do with audible warnings.
 In any case in Tweak Tool the full grammatical functions are not displayed properly, only the first few characters.
 

 The old solution looks nice and easy, can anyone help me achieve it?
 

 N.B. Since I installed 14.04 I can only use it on Gnome Flashback Metacity Desktop due to slow graphics presumably as my graphics card is too old. (2007)

---

### Post by CantankRus on 2014-08-21
I can set this in System settings > Universal access.
Gives a horrible thud sound but probably can be changed.

---

### Post by travis_mattila on 2014-08-22
anyone else able to make caps lock make a sound ? not workin over here

---

### Post by CantankRus on 2014-08-22
The method shown earlier only works in my flashback metacity session.
Compiz must interfere with it somehow.
There is another way to set a capslock sound in compiz if you're using the ubuntu/unity session.

Open compizconfig-settings-manager and enable the Commands plugin.
Add the path to the **capslock-notify.sh**(see below for script) to one of the command line entry boxes...
[ATTACH=CONFIG]255748[/ATTACH]

Then in the keybindings tab go to the corresponding command number and click on the "Disabled" box.
Enable and click on **grab key combination**
Press the capslock key.
It doesn't appear to have worked but you just need to close the small ccsm window and press ok.
[ATTACH=CONFIG]255749[/ATTACH]

When capslock is enabled a "ting" sound will play and a notification will appear.
[ATTACH=CONFIG]255750[/ATTACH]

If a sound doesn't play, check the following command in terminal and try different sounds from **/usr/share/sounds**
```
/usr/bin/canberra-gtk-play -f /usr/share/sounds/gnome/default/alerts/glass.ogg
```


Save as **capslock-notify.sh** and make executable...
```
#!/bin/bash
sleep 0.2
value=$(xset q | awk '/Caps Lock:/{print $4}' | grep -c on)

if [ "$value" -eq "1" ]; 
then
   notify-send -i  keyboard "                    Caps Lock:  ON" &
    /usr/bin/canberra-gtk-play -f /usr/share/sounds/gnome/default/alerts/glass.ogg
else
   notify-send -i  keyboard "                    Caps Lock:  OFF"
   
fi
```
The script uses xset to determine the status of capslock so a sound only occurs 
when capslock is enabled and the status is displayed by notify-send.
For just a simple sound when capslock is pressed you could replace the script path 
in the commands plugin with just a command to play a sound... ie **/usr/bin/canberra-gtk-play -f /usr/share/sounds/gnome/default/alerts/glass.ogg**

---

### Post by benawhile on 2014-08-23
Thank you all. The solution by CantankRus works perfectly in metacity for me, the only thing is how stupid I was not to see it. I thought I had looked at every available page of the system settings, but still I did not notice that "Univeral Access" was what I wanted, and even when you pointed me to that my brain still refused to see the relevant setting until I looked at your attached thumbnail. Thanks again. Marked as solved

---

### Post by CantankRus on 2014-08-23
Run this in terminal
```
/usr/bin/canberra-gtk-play -f /usr/share/sounds/gnome/default/alerts/glass.ogg
```
If you prefer that sound, run these two commands
```
sudo cp /usr/share/sounds/ubuntu/stereo/bell.ogg /usr/share/sounds/ubuntu/stereo/bell.ogg.bak
sudo cp /usr/share/sounds/gnome/default/alerts/glass.ogg /usr/share/sounds/ubuntu/stereo/bell.ogg
```

To revert back to the original sound, run
```
sudo mv /usr/share/sounds/ubuntu/stereo/bell.ogg.bak /usr/share/sounds/ubuntu/stereo/bell.ogg
```

---

### Post by tony-whelan on 2014-11-30
CantankRus, thanks for the script you provided.

When I have tried enabling "beep on caps/num lock" on Ubuntu 14.04 and Linux Mint 17, there is NO sound at all. Tested it on several different machines with same result. There are long-standing bug reports about this for Ubuntu and no indication that it's a priority.

In Mint the PC speaker is disabled (blacklisted) by default, because for many people its too loud. I tried un-blacklisting it, and yes it made an ugly beep when the Caps key was pressed, but that's pretty unsatisfactory.

Having a sound play when the key is pressed is fine, but we actually need two sounds. The way it SHOULD work is that pressing CAPS LOCK ON should play a "high" sound, and pressing it again to OFF should play a "low" sound. That way the user (esp if with dsability) can clearly tell the difference between CAPS ON and CAPS OFF. That's how it works in Windows.

The script provided by CantankRus may be a useful starting point for me. I run Linux Mint (which uses Metacity, not compiz). But I think I can still assign a a script to the CAPS key and have it play ON and OFF tones pretty easily. Going to try to find time to play with that soon. If I get somewhere I'll post the method.

---

### Post by coldcritter64 on 2014-11-30
> Having a sound play when the key is pressed is fine, but we actually need two sounds.
Try the next alteration,
> ```
#!/bin/bash
sleep 0.2
value=$(xset q | awk '/Caps Lock:/{print $4}' | grep -c on)

if [ "$value" -eq "1" ]; 
then
   notify-send -i  keyboard "                    Caps Lock:  ON" &
    /usr/bin/canberra-gtk-play -f /usr/share/sounds/gnome/default/alerts/glass.ogg
else
   notify-send -i  keyboard "                    Caps Lock:  OFF" [B]&
   /usr/bin/canberra-gtk-play -f /path/to/off/sound/file/file.ogg[/B]
fi
```

Try the bolded addition for the script  CantankRus provided above. _*Alter the path to the second "OFF" sound*_ to one you want or create one and address it to the canberra-gtk-play command.

The Caps Lock key press either turns "on" or "off" and the code "xset q | awk '/Caps Lock:/{print $4}'" returns the actual state. The "grep" command is specifically looking for on. So the second option of the script is for the "off" state, placing a command there when the key is pressed to the "off" state as well should play a (different) sound when turning it off and the compiz command plugin/keymapping is used. Try it out with Ubuntu, I'm on Debian and don't have the canberra-gtk-play command here _*Edit:*_ or compiz either :).

---

### Post by CantankRus on 2014-11-30
**coldcritter64**'s addition should work.
For the off sound you could use **/usr/share/sounds/gnome/default/alerts/sonar.ogg**
If system sounds are muted you wont hear sounds played using canberra-gtk-play.
So if muted or canberra-gtk-play is not installed use another command that works for you...
eg
[LIST]
[*]**aplay** from the alsa-utils package 
[*]**play** from the sox package (also install libsox-fmt-all to play different formats)
[*]**mplayer** from the mplayer2 package
[*]
[/LIST]
Some wont play certain sound formats.

---

### Post by tony-whelan on 2014-11-30
> **CantankRus said:**
> **coldcritter64**'s addition should work.
For the off sound you could use **/usr/share/sounds/gnome/default/alerts/sonar.ogg**
If system sounds are muted you wont hear sounds played using canberra-gtk-play.
So if muted or canberra-gtk-play is not installed use another command that works for you...
eg
[LIST]
[*]**aplay** from the alsa-utils package 
[*]**play** from the sox package (also install libsox-fmt-all to play different formats) 
[*]**mplayer** from the mplayer2 package 
[/LIST]
Some wont play certain sound formats.

Thanks folks, comments appreciated. On my machines canberra-gtk-play returns "Failed to play sound: Sound disabled" though I'm not sure where/what is disabled. But the 'play" command works fine. I'm going to have a go at setting this up now and will report on how I go.

---

### Post by tony-whelan on 2014-11-30
Using the suggestions above, this is how I have just set up CAPS LOCK notification on my Linux Mint 17 Cinnamon machine which uses Metacity not Compiz. 

In my home folder I created two files, **.bindkeysrc** and **capslock-notify.sh** 

File:  .bindkeysrc
```

"bash ~/capslock-notify.sh"
m:0x2 + c:66

```

File capslock-notify.sh
```

#!/bin/bash/
# capslock-notify.sh
# Original code from Ubuntu Forums by CantankRus, 
# with edit by coldcritter64
# and modified 1 Dec 2014 for Linux Mint 17 Cinnamon by Tony Whelan
# For visual indication as well as audible, remove the # in lines starting "notify-send"
# Requires: "play" program 
# Tested on Linux Mint 17 Cinnamon (64 bit)
sleep 0.2
value=$(xset q | awk '/Caps Lock:/{print $4}' | grep -c on)

if [ "$value" -eq "1" ]; 
then
    # notify-send -i  keyboard "                    Caps Lock:  ON" &
    play -f /usr/share/sounds/LinuxMint/stereo/dialog-information.ogg
else
   # notify-send -i  keyboard "                    Caps Lock:  OFF" &
   play -f /usr/share/sounds/LinuxMint/stereo/dialog-question.ogg
fi

```
Possibly not all keyboards have the same mapping code as mine (m:0x2 + c:66) but that can be checked in a terminal by installing xbindkeys and then execute it:
```
xbindkeys -k
```
and press the Caps Lock key, which will return the key code needed for file .xbindkeysrc 

After creating the above two files you will need to at least log out to make it work.

The two .ogg sound files I selected here are not necessarily the best ones to use, I just picked them as a quick test example.

In the above file capslock-notify.sh I have commented out the two lines starting "notify-send" as I don't need the visual indication; that can be re-enabled by removing the "#" in front of those commands.

For this arrangement to work, you obviously need the "play" program installed. If the sound plays louder than desired, you can drop the volume with "play -v" - so "play -v0.2" would be a lot quieter than "play -v1"

Thanks to CantankRus and coldcritter 64 for leading me to a solution that was effective and simple to achieve.

I have submitted a bug report for Linux Mint Cinnamon suggesting they dump the current non-working code for "Beep on Caps/Num Lock" and instead add code that achieves the above result, and add relevant sound effects in the Sound control panel.

---

### Post by tony-whelan on 2015-08-22
Better late than never ...
I put this modified script in my /home folder (Linux Mint 17):
#!/bin/bash/
# capslock-notify.sh
sleep 0.2
value=$(xset q | awk '/Caps Lock:/{print $4}' | grep -c on)
if [ "$value" -eq "1" ]; 
then
   # canberra-gtk-play -f ~/up.ogg    # use this or use 'play'
   play -v0.9 ~/up.ogg
else
   play -v0.9 ~/down.wav
fi

Then via Mint's settings for keyboard I assigned a custom keyboard shortcut for the CAPS LOCK key which executes that script (sh ~/caps-notify.sh) when the key is pressed.

My up.ogg and down.wav files are sounds I pillaged from various places & renamed - I needed two sounds that were very brief but well audible.

---


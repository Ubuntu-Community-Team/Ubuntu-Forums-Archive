---
title: "Bluetooth Headset: Can't set A2DP (High Fidelity Playback). Poor sound quality"
date: 2016-12-24
forum: General Help
---

### Post by fabriciobarretti on 2016-12-24
I'm trying to use my bluetooth headset (Bluedio, in the screenshot below) in  Ubuntu-Gnome 16.10, but I keep getting a horrible sound quality in  everything I try to listen.

Important note: I've just tested with a different device, a bluetooth **speaker**, and it gets the A2DP profile automatically, with a nice sound quality. The problem, then, is only happening with my bluetooth **headset** (Bluedio).


  I've read some posts and the given suggestions don't work in my case (Ubuntu-Gnome 16.10). These suggestions are:


  1) Under the Sound settings, change the headset profile to the A2DP  (High Fidelity Playback). Not only the sound quality didn't even change,  the profile keeps getting turned back to Headset Head Unit (HSP/HFP)  profile, in which the sound quality remains horrible. So, even though  the A2DP profile shows up there, it doesn't take effect and goes back to  the HSP/HFP profile everytime.


  2) Changes in the /etc/bluetooth/audio.conf file, like uncommenting  the line "AutoConnect=true line". First of all, there isn't such file in  Ubuntu-Gnome 16.10. Instead, there is the /etc/bluetooth/main.conf  file, which seems pretty similar to the first one in terms of  parameters. But, the line is already uncommented in my S.O., just as the  suggestion tells me to do. So, it seems that there's nothing to do here  with this suggestion.


  Here's the screenshot of the Sound Settings' screen. You can see that  there's an arrow for the dropdown list, where the A2DP profile shows up  (even though it's not appearing in the shot. It's there though), but it  gets back to the HSP/HFP profile everytime. Here's the link for the  screenshot: [https://i.stack.imgur.com/fIfG5.png](https://i.stack.imgur.com/fIfG5.png)


*** Edited with the solution! ***

I've managed to fix it before I saw your post in a different way.

Even though I'm not sure if the following  steps are in the exactly  order to do it, I'm pretty sure it was the  combination of them that  fixed it. Here they are:

  1) I've installed Blueman (Bluetooth Manager, I suppose): sudo apt-get install blueman

  2) I've edited the /etc/bluetooth/audio.conf file: sudo gedit  /etc/bluetooth/audio.conf and add this line in the end of it:  Disable=Headset

  Note: I've also intalled something called "pavucontrol" via terminal  with the command sudo apt-get install pavucontrol,  but I'm really not  sure if it was this or the Blueman that solved it. I  suspect it was the  Blueman, but if it doesn't help, try the pavucontrol  and see if it  solves.


  Hope this helps!

---

### Post by jeremy31 on 2016-12-24
Download [https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip](https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip)
```
cd Downloads
unzip d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
cd 
cp ~/Downloads/d68be364adac5f946887b85e6ed6e7ae-d698974910bbb7d016ec0ad08c1bf41b4b524364/a2dp.py a2dp.py
```

Then you should be able to run ```
./a2dp.py
```
And select the headset from the menu-- the menu may not appear if the headset is the only paired bluetooth device

---

### Post by fabriciobarretti on 2016-12-24
Thanks for the help! But I've managed to fix it before I saw your post in a different way.

Even though I'm not sure if the following  steps are in the exactly order to do it, I'm pretty sure it was the  combination of them that fixed it. Here they are:

  1) I've installed Blueman (Bluetooth Manager, I suppose): sudo apt-get install blueman



  2) I've edited the /etc/bluetooth/audio.conf file: sudo gedit /etc/bluetooth/audio.conf and add this line in the end of it: Disable=Headset


  Note: I've also intalled something called "pavucontrol" via terminal with the command sudo apt-get install pavucontrol,  but I'm really not sure if it was this or the Blueman that solved it. I  suspect it was the Blueman, but if it doesn't help, try the pavucontrol  and see if it solves.


  Hope this helps!

---

### Post by Bucky Ball on 2016-12-24
If you open Pulseaudio Volume Control (pavucontrol) you will probably find that the bluetooth device is now set as the output device in the output tab. Your problem may come if you want to hear audio through anything else. You may then need to go to PAVControl and change the output device.

Just throwing that in. ;)

Please see last blue link in my signature and mark this thread as solved to help others and save the rest some time.

---


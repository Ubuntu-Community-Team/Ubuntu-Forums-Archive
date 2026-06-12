---
title: "Bluetooth audio A2DP mode stopped working after 21.10 update"
date: 2021-11-18
forum: General Help
---

### Post by PABlanche on 2021-11-18
After updating to Ubuntu 21.10 that includes Pulseaudio 15, my Bluetooth headphone (Skullcandy Hesh 2 wireless) are muted when set on A2DP. 
When on A2DP setting, no sound comes out. It is still working with HFP and HSP though, but  with low quality of course. 
The headset was working with A2DP before the update.


 I followed the instruction from the post below that were for 16.04,  but when I did that the headphone could not connect with Bluetooth  anymore:
[After updating to 16.04, bluetooth audio A2DP mode stopped working]("https://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working")

 
I also followed these instruction but without improvement: [URL="https://askubuntu.com/questions/904423/bluetooth-headphones-refuse-to-use-a2dp-high-quality?rq=1"]
Bluetooth Headphones refuse to use A2DP High Quality[/URL]

 
Additionally, when the Bluetooth headset received sound, my Bluetooth  mouse was sluggish (has reaction delay). 
I solved that problem by changing the bluetooth coexistence parameter with:
echo "options iwlwifi bt_coex_active=0" | sudo tee /etc/modprobe.d/iwlopt.conf 

 and reboot

 Thanks: [URL="https://ubuntuforums.org/showthread.php?t=2372916"]https://ubuntuforums.org/showthread.php?t=2372916
[/URL]for the solution.


     
 The sound problem happens both on Wayland and Xorg sessions.

---

### Post by PABlanche on 2021-11-18
Solution:
Open sound setting and put the headset on A2DP. 
Then open pavucontrol and mute/unmute the headset.

And voila it works as it should.
I don't know why it was automatically muted in pavucontrol though, and only for A2DP.

---


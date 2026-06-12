---
title: "Pairing a device automatically"
date: 2023-11-07
forum: General Help
---

### Post by angel mike on 2023-11-07
I have a device ( Cochlear Implant ) with Bluetooth which I can pair with my laptop which has Ubuntu 22.04. At present I have to re-pair the device each day but from searching the net I believe it is possible to automatically pair once you have set it up. See link    [https://techwiser.com/fix-bluetooth-device-doesnt-auto-connect-in-linux/](https://techwiser.com/fix-bluetooth-device-doesnt-auto-connect-in-linux/)
How do I setup the conf file?

---

### Post by dragonfly41 on 2023-11-07
I have a number of devices and I find Bluetooth Manager to be useful rather than command line.

[https://github.com/blueman-project/blueman](https://github.com/blueman-project/blueman)

P.S. it is found in Synaptic repo

---

### Post by #&amp;thj^% on 2023-11-07
> **dragonfly41 said:**
> I have a number of devices and I find Bluetooth Manager to be useful rather than command line.

[https://github.com/blueman-project/blueman](https://github.com/blueman-project/blueman)

P.S. it is found in Synaptic repo

+1
It's not fool proof but if you only connect with the same system daily it should satisfy your request.
```
apt policy blueman
blueman:
  Installed: 2.3.5-3
  Candidate: 2.3.5-3
  Version table:
 *** 2.3.5-3 500
        500 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by angel mike on 2023-11-08
Thanks all for your links - will give them a try and put some feedback in post with hopefully success

---

### Post by angel mike on 2023-11-08
Thanks 1Fallen - put the code in the terminal all at once but got command not found - so could you expand on this. Looked at Synaptic repo but not sure what to do with it. The blue-man project is a bit beyond me! Thanks all the same.

---

### Post by tea for one on 2023-11-08
> **angel mike said:**
> Thanks 1Fallen - put the code in the terminal all at once but got command not found - so could you expand on this.
What code did you enter?

---

### Post by dragonfly41 on 2023-11-08
read here ..
[https://embeddedinventor.com/apt-install-y-command-explained-for-beginners/](https://embeddedinventor.com/apt-install-y-command-explained-for-beginners/)
then ..
sudo apt install -y blueman
then ..
[https://devicetests.com/running-blueman-command-line-connecting-recent-connections](https://devicetests.com/running-blueman-command-line-connecting-recent-connections)
then ..
blueman-manager

---

### Post by #&amp;thj^% on 2023-11-08
> **dragonfly41 said:**
> 
```
sudo apt install -y blueman
```
then ..
[https://devicetests.com/running-blueman-command-line-connecting-recent-connections](https://devicetests.com/running-blueman-command-line-connecting-recent-connections)
then ..
```
blueman-manager
```

+1 Again it's that easy

---

### Post by angel mike on 2023-11-09
I pursued with 1Fallen and loaded the blueman manager which showed my device listed but then did nothing else as far as I could make out.
Will look at links provided by others - thanks for the contributions.

---

### Post by angel mike on 2023-11-10
I have the Bluetooth Manager installed and it shows my device but the problem is the Auto Connect on the list is 'greyed out'. How do I fix this. None of the links above mention this.

---

### Post by dragonfly41 on 2023-11-10
From vague memory on connecting to a new device I received a security number to type in.
Click on device > connect.

---

### Post by angel mike on 2023-11-10
I found a link about auto connect problems dated July 2020 so should be current  [https://techwiser.com/fix-bluetooth-device-doesnt-auto-connect-in-linux/](https://techwiser.com/fix-bluetooth-device-doesnt-auto-connect-in-linux/).
Will see if this solves the problem

---

### Post by #&amp;thj^% on 2023-11-12
Late reply, 
That should help but I'll stick to my original statement, if booting one system only it works fairly reliable. (Prone to switch disabled with updates)
```

tac /etc/bluetooth/main.conf AutoEnable=true

AutoEnable=true
# in later on. Defaults to 'true'.
# This includes adapters present on start as well as adapters that are plugged
# AutoEnable defines option to enable all controllers when they are found.
```

---

### Post by angel mike on 2023-11-13
Thanks 1Fallen - I put the code in which gave me a text file bit no opportunity to enter  Using the link I gave the code 'sudo nano /etc/bluetooth/main.conf' I have put AutoEnable=true which does not solve the problem so I continued through the steps to section 5 Script which says    	 	 	 	  First of all, download the zip file from GitHub or use the following command to clone the repository to your home directory   	 	 	 	  

  
 git clone [https://github.com/jrouleau/bluetooth-autoconnect.git](https://github.com/jrouleau/bluetooth-autoconnect.git) 
Now that we have the repository downloaded we need to move the 
service.



   
  In my case, I am using systemd architecture, hence the file
destinations mentioned would be applicable to distros like ArchLinux,
Ubuntu, Debian, etc. In case you use non-systemd distros, kindly
google your service directories.



	
	
	
	

sudo cp bluetooth-autoconnect/bluetooth-autoconnect.service /etc/systemd/system/
sudo cp '/home/pratik/bluetooth-autoconnect/bluetooth-autoconnect' /usr/bin/ Once, we have successfully copied the service to the respective directories, let&#8217;s enable and start the service. To do that, use the following command.
 sudo systemctl enable bluetooth-autoconnect.service
sudo systemctl start bluetooth-autoconnect.service Now, that we have the service started, it&#8217;ll try to reconnect to every paired and trusted Bluetooth device. The only caveat with this method is that you won&#8217;t be able to pair your Bluetooth device with other systems without switching off your Linux machine&#8217;s Bluetooth. Since the device would always try to connect with your Bluetooth device.

I am trouble moving the download to the respective directories - how do I do that because running  the last two codes gives me an error saying no file found

---

### Post by angel mike on 2023-11-13
I am not sure what architecture I am using? - the link says systemd?

---

### Post by #&amp;thj^% on 2023-11-13
Goodness we are making this much harder than needed, I'm not sure what you have done thus far, but lets check what you have now:
please show this:
```
apt policy blueman

```
and this:
```
systemctl status bluetooth
``` 
There is no need to download anything outside of what is already in our sources
And please check that nothing shows here:
```
sudo bluetoothctl info mac_address

```
I hope it says "Device mac_address not available DeviceSet mac_address not available"

---

### Post by angel mike on 2023-11-13
Okay - hear we go
apt policy blueman
blueman:
  Installed: 2.2.4-1
  Candidate: 2.2.4-1
  Version table:
 *** 2.2.4-1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

 systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Mon 2023-11-13 20:10:59 GMT; 18min ago
       Docs: man:bluetoothd(8)
   Main PID: 543 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18742)
     Memory: 2.3M
        CPU: 165ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;543 /usr/lib/bluetooth/bluetoothd

Nov 13 20:10:59 michael-XPS-13-9310 systemd[1]: Started Bluetooth service.
Nov 13 20:10:59 michael-XPS-13-9310 bluetoothd[543]: Bluetooth management inter>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
Nov 13 20:11:00 michael-XPS-13-9310 bluetoothd[543]: Endpoint registered: sende>
lines 1-22/22 (END)


sudo bluetoothctl info mac_address
[sudo] password for michael: 
Device mac_address not available

---

### Post by angel mike on 2023-11-13
You may find this of interest which shows that at the end of the conf file that Auto Enable is set to true. (I have not copied the text statements - only the end section.
sudo nano /etc/bluetooth/main.conf
 ReconnectIntervals define the set of intervals in seconds to use in between
# attempts.
# If the number of attempts defined in ReconnectAttempts is bigger than the
# set of intervals the last interval is repeated until the last attempt.
#ReconnectIntervals=1, 2, 4, 8, 16, 32, 64

# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true

---

### Post by #&amp;thj^% on 2023-11-13
Ok now open blueman-manger:
```
blueman-manager
```
pair your device, and after it's connected, right click on your device, and mark as trusted.
Note you will have to pair it first for all this to work.
Now you can look at:
```
sudo bluetoothctl info
Device F8:DF:15:7F:64:73 (public)
	Name: SRS-XB22
	Alias: SRS-XB22
	Class: 0x00240414 (2360340)
	Icon: audio-card
	Paired: yes
	Bonded: yes
	Trusted: yes
	Blocked: no
	Connected: yes
	LegacyPairing: no
	UUID: Vendor specific           (00000000-deca-fade-deca-deafdecacaff)
	UUID: Serial Port               (00001101-0000-1000-8000-00805f9b34fb)
	UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
	UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
	UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
	UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
	UUID: Vendor specific           (b9b213ce-eeab-49e4-8fd9-aa478ed1b26b)
	Modalias: bluetooth:v0039p1582d2203
	ManufacturerData Key: 0x<snip> (21321)
	ManufacturerData Value:
  53 43                                            SC              

```

---

### Post by angel mike on 2023-11-14
Yes I had this output before but does not work - no permanent pairing.
~$ sudo bluetoothctl info 
[sudo] password for michael: 

Sorry, try again.
[sudo] password for michael: 
Sorry, try again.
[sudo] password for michael: 
Device 70:66:1B:C9:BE:B0 (public)
    Name: R Sound Processor
    Alias: R Sound Processor
    Class: 0x00240404
    Icon: audio-headset
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Advanced Audio Distribu.. (0000110d-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000

---

### Post by angel mike on 2023-11-14
Just to check again I pared this morning and then closed the laptop then tried to automatically pair this afternoon with no result. So to pair I have to put the device(Cochlear Implant) into a pairing mode (30secs) to pair.

---

### Post by angel mike on 2023-11-14
The author of the link had the same trouble until he used the coding from Github - see section 5 of the link

---

### Post by dragonfly41 on 2023-11-14
this is what I read ..

[https://github.com/jrouleau/bluetooth-autoconnect/issues/15](https://github.com/jrouleau/bluetooth-autoconnect/issues/15)
[h=3] If you aren't concerned about battery life, you could configure a cron job or similar to continually probe.
[/h]

---

### Post by #&amp;thj^% on 2023-11-14
EDIT this has some merit:
> **dragonfly41 said:**
> this is what I read ..

[https://github.com/jrouleau/bluetooth-autoconnect/issues/15](https://github.com/jrouleau/bluetooth-autoconnect/issues/15)
[h=3] If you aren't concerned about battery life, you could configure a cron job or similar to continually probe.
[/h]


Yep I hear a lot about headsets and hands-free devices. that won't work on Auto Connect.
Give some time today or tomorrow, I'll try to help if I can, I'm just not familiar with your device.
maybe something along the lines of:
```
pactl set-card-profile $BLUETOOTHCARDNAME $profile
```
A quick example for a script would be:
```
#!/bin/bash

ldac=`pactl list | grep Active | grep ldac`
card=`pactl list | grep "Name: bluez_card." | cut -d ' ' -f 2`

if [ -n "$ldac" ]; then
    echo "Switching $card to msbc..."
    pactl set-card-profile $card headset-head-unit-msbc
    echo "...done"
else
    echo "Switching $card to ldac..."
    pactl set-card-profile $card a2dp-sink-ldac
    echo "...done"
fi
```
That script will fail for you until it is adjusted to a proper codec and device.

---

### Post by angel mike on 2023-11-15
Thanks for all that info 1Fallen - I am afraid I am just not up to the coding required so will call it a day. I have Advanced Bionics looking at this but not hopeful!

---

### Post by yancek on 2023-11-15
The only bluetooth device I use is a set of earbuds.  I paired them once.  They need to be connected each time I use them and must be in range.  I am using 20.04 so don't know if you have the same options.  I open System Settings and click on the Bluetooth tab and see a list of devices in the right main window.  If I left click on the device name in the main window, another window opens with info including connection (this shows off) and Paired which shows Yes.   If you click Connection and the device is in range and on, it should connect.  Can you do this manually and does it work?  You should not have to pair continuously but should have to connect whenever the device goes out of range and comes back.  If this works for you then you are trying to auto-connect and failing, correct?  From what I have read, that is an ongoing problem and I don't have a solution, if there currently is one.

---

### Post by #&amp;thj^% on 2023-11-15
> **yancek said:**
> You should not have to pair continuously but should have to connect whenever the device goes out of range and comes back.  If this works for you then you are trying to auto-connect and failing, correct?  From what I have read, that is an ongoing problem and I don't have a solution, if there currently is one.
+1 that's how i see it as well.

@ angel mike I've used that script in your link, and it actually broke my bluetooth....so there's that.
And i probably use a different sound server than you use currently. NOTE: I'm not recommending you change your current sound stack though.
```
 wpctl status
PipeWire 'pipewire-0' [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, cookie:<snip>]
 &#9492;&#9472; Clients:
        32. pipewire                            [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4028]
        34. WirePlumber                         [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4027]
        35. WirePlumber [export]                [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4027]
        87. xdg-desktop-portal                  [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4630]
        89. pipewire                            [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4028]
        90. pipewire                            [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:4028]
       126. xfce4-pulseaudio-plugin             [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:5448]
       129. wpctl                               [0.3.84, me@lvm-ThinkPad-X1-Carbon-7th, pid:168033]

Audio
 &#9500;&#9472; Devices:
 &#9474;      43. UOEOS Laptop Dock                   [alsa]
 &#9474;      44. Comet Lake PCH-LP cAVS              [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      33. Comet Lake PCH-LP cAVS HDMI / DisplayPort 3 Output [vol: 1.00]
 &#9474;      48. Comet Lake PCH-LP cAVS HDMI / DisplayPort 1 Output [vol: 1.00]
 &#9474;      49. Comet Lake PCH-LP cAVS Speaker + Headphones [vol: 0.41]
 &#9474;      50. Comet Lake PCH-LP cAVS HDMI / DisplayPort 2 Output [vol: 1.00]
 &#9474;      51. UOEOS Laptop Dock Analog Surround 5.1 [vol: 1.25]
 &#9474;  *   91. combined                            [vol: 0.55]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      47. Comet Lake PCH-LP cAVS Headphones Stereo Microphone [vol: 1.00]
 &#9474;  *   52. Comet Lake PCH-LP cAVS Digital Microphone [vol: 1.00 MUTED]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        92. output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
            100. output_FL       > UOEOS Laptop Dock:playback_FL	[paused]
            101. output_FR       > UOEOS Laptop Dock:playback_FR	[paused]
            102. output_RL       > UOEOS Laptop Dock:playback_RL	[paused]
            103. output_RR       > UOEOS Laptop Dock:playback_RR	[paused]
            104. output_FC       > UOEOS Laptop Dock:playback_FC	[paused]
            105. output_LFE      > UOEOS Laptop Dock:playback_LFE	[paused]
        93. output.combined_alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink
            106. output_FL       > HDMI / DisplayPort 3 Output:playback_FL	[paused]
            107. output_FR       > HDMI / DisplayPort 3 Output:playback_FR	[paused]
        94. output.combined_alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink
            108. output_FL       > HDMI / DisplayPort 2 Output:playback_FL	[paused]
            109. output_FR       > HDMI / DisplayPort 2 Output:playback_FR	[paused]
        95. output.combined_alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
            110. output_FL       > HDMI / DisplayPort 1 Output:playback_FL	[paused]
            111. output_FR       > HDMI / DisplayPort 1 Output:playback_FR	[paused]
        96. output.combined_alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink
            112. output_FL       > Speaker + Headphones:playback_FL	[paused]
            113. output_FR       > Speaker + Headphones:playback_FR	[paused]

Video
 &#9500;&#9472; Devices:
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;      42. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   45. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    combined

```

---

### Post by angel mike on 2023-11-16
Thanks yancek - my cochlear implant does reconnect automatically when in range but after time like next day I have to re-pair. The attached unit sends signals to the probe inserted into my cochlear from two microphones so not quite like ear buds but I guess the Bluetooth is, Using Ubuntu 22.04.

---

### Post by angel mike on 2023-11-16
Thanks 1Fallen for trying - not with very encouraging results - ah well that's life - win some lose some !

---

### Post by yancek on 2023-11-16
>  my cochlear implant does reconnect automatically when in range but after time like next day I have to re-pair. 

You should not have to pair more than once.  I paired the earbud 3 months ago and have not had to do that again.  They are almost always in another room across the house and when I want to use them with the computer I just go to System Setting/Bluetooth and there is a list of devices in the main window and it will show Disconnected to the right of the device.  Do you have the same settings as I am on 20.04?  When I click on the device a small windows opens and there is info on the window, it shows paired and there is a circle to click to connect to the right of connect.  If you don't see that, I'm not sure what the problem would be.  Have you used any other bluetooth devices without problems?

Is the link below what you are using?

[https://www.cochlear.com/us/en/home/products-and-accessories/cochlear-nucleus-system/nucleus-sound-processors/nucleus-8?utm_source=google&utm_medium=cpc&utm_campaign=prosp_brnd_ci_n8_can_ci-prog_nuc-ev&utm_content=nucleus8_rsa&utm_term=cochlear%20n7&gclid=Cj0KCQiAmNeqBhD4ARIsADsYfTfjhN3MoLwu64cGH78B6JRCXWypGilRWiYrn0J0-p--SzufNdO59bYaAtGKEALw_wcB](https://www.cochlear.com/us/en/home/products-and-accessories/cochlear-nucleus-system/nucleus-sound-processors/nucleus-8?utm_source=google&utm_medium=cpc&utm_campaign=prosp_brnd_ci_n8_can_ci-prog_nuc-ev&utm_content=nucleus8_rsa&utm_term=cochlear%20n7&gclid=Cj0KCQiAmNeqBhD4ARIsADsYfTfjhN3MoLwu64cGH78B6JRCXWypGilRWiYrn0J0-p--SzufNdO59bYaAtGKEALw_wcB)

---

### Post by angel mike on 2023-11-17
Yes yancek I have the same setup- which I use to pair. As I mentioned sometimes the CI device pairs automatically on logging on again the next day without me doing anything  but mostly it does not for some strange reason. The only other Bluetooth Device I have listed in the Settings is my mobile phone which I rarely pair but seems to pair ok - will keep it under review. Thanks for your info about the length of time staying paired so there is hope yet!

---

### Post by yancek on 2023-11-17
It could be the device itself not being compatible on Linux but that is just guessing.   I don't know if that matters with bluetooth.  Did you see anything regarding that in the manual for it (if you have one) or on the page at the link I posted, that is if it is your device?

---

### Post by yancek on 2023-11-17
It could be the device itself not being compatible on Linux but that is just guessing.   I don't know if that matters with bluetooth.  Did you see anything regarding that in the manual for it (if you have one) or on the page at the link I posted, that is if it is your device?

---

### Post by dragonfly41 on 2023-11-17
Wild thought .. does your device connect properly in:
(a) another created new user account
or
(b) a liveUSB session?

Just thinking through options to offer more clues.

---

### Post by angel mike on 2023-11-18
Thanks for the latest options - will investigate. In the meantime the cochlear implant is pairing automatically for the second day which is good news.

---

### Post by angel mike on 2023-11-19
The CI device  seems to be pairing better especially with the Bluetooth manager so I will put this as solved. Thanks for all your contributions to the problem.

---


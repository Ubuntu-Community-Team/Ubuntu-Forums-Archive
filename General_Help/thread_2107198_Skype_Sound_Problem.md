---
title: "Skype Sound Problem"
date: 2013-01-21
forum: General Help
---

### Post by Wolfgange on 2013-01-21
Hello, I recently installed skype on my ubuntu 12.04Lts desktop computer. The only microphone I have is a Bluetooth headset. The headset's speakers, and mic work well in other applications, but in skype (which is the latest version) it says something like "audio problem" and it won't make calls.
     I've reinstalled pulse audio, I made sure the headphones are on something like tcp/agp which allows the use of mic input. I have pulse audio config/ mixer it something, and I made sure the defaults were the headset. Under the recording tab, where it shows all the programs using mic input, skype never appears there. And lastly, in the skype audio options i've put all the options to default, sysdefault, pulse, rawbluetooth, and bluetooth.
     Any suggestions? Please help, and thanks in advance.

---

### Post by Wolfgange on 2013-01-21
Anyone?

---

### Post by dannyboy79 on 2013-01-21
make sure that some other application isn't taking control of the mic input first. not sure entirely how to ensure that BUT have you tried skype's test call feature? when you try to make a call, skype should show up as an app within the recording tab. also, you have made sure that the bluetooth mic is the only one choosen within the input tab? I am using skype 4.1 I believe and I use a logitech c260 (only $19 refurbished from newegg) for my skype calls and it works flawlessly.

---

### Post by Wolfgange on 2013-01-21
Thank you for the reply, I was using the skype test call and it doesn't work or show up in the recording tab. But there were multiple things in the inPut tab; how do I unselect them?

---

### Post by Wolfgange on 2013-01-21
So, does anyone know how to deselect inputs in the input tab of pulse audio preferences?

---

### Post by Wolfgange on 2013-01-21
Does anyone know?

---

### Post by dannyboy79 on 2013-01-21
ok, slow down man. we're all just volunteers helping others for free, if someone doesn't answer right away sit tight otherwise maybe go on IRC chat on freenode.net using xchat and go to the #ubuntu channel for help.
go to the configurations tab and i think you can turn off devices but otherwise you can "mute" other inputs. It was just a guess that maybe someother app took control of your headset mic and maybe not even what the problem is. see if you can launch from the command line with verbose output so that you can maybe see what the errors are in the terminal. maybe they are more descriptive then just "audio problem"

UPDATE: have you checked out the various google searchs out there, there seems to be a ton of them about ubuntu skype and bluetooth headsets. here's one
[http://www.ossramblings.com/skype_bluetooth_headset_64_bit_ubuntu](http://www.ossramblings.com/skype_bluetooth_headset_64_bit_ubuntu)

---

### Post by Wolfgange on 2013-01-21
Thank you! I followed the first instructions of the web page and it worked!

---

### Post by dannyboy79 on 2013-01-21
awesome!

---


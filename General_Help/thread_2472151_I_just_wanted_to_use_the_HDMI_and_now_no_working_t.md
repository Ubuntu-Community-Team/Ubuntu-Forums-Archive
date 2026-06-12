---
title: "I just wanted to use the HDMI and now no working trackpad, wifi, or bt."
date: 2022-02-18
forum: General Help
---

### Post by sparky-code on 2022-02-18
Hello,

I recently started using Ubuntu so theres a lot I don't know.

I was having issues with Ubuntu drivers...and now everything.
- Windows 10 // Linux Duel setup on an HP Spectre
- Running Ubuntu 20.04 LTS
- SecureBoot enabled / disabled make no difference. 
- booting from a LiveUSB gives me full access to wifi/bt and keyboard/mouse, as does logging into the Windows side of things.
-- When logging into the windows side of things, after everything locked up on the Ubuntu side I did get bitlocker starting to add a further layer of issue to getting into windows. I believe this may be related but I don't know how.


My Issue:
--> tried to connect to external display, Ubuntu didnt see the HDMI port.
--> found through google that nvidia drivers may need to be updated.
--> updated drivers, and agreed to MOK setup on next startup without quite realizing what I was agreeing too.
--> close laptop casually and hibernation mode fails, kicks me to a restart, enroll MOK...keyboard wont work, mouse wont work.
-->further reading, work around through BIOS, enter passphrase, think it went fine...computer restarts and...
--> mouse wont work, keyboard wont work, BT and WIFI modules are not detected.
--> Now I cant activate the drivers I tried to download earlier, I can't USB tether for internet for some reason (unknown).
--> tried resetting MOK > new passphrase,  ran through that cycle a number of times and have had heavily variable luck with my BIOS work around even getting me to a stage i can input the new passphrase. stuck with a neutered laptop and idk what to do. 

* I was able to eventually get the keyboard working, and can connect external mouse and keyboard so I do now have access to the desktop terminal. I've tried a few things from rooting around in the forums but I don't really know enough to gauge if its the correct info and since it hasn't solved anything I think starting from base with troubleshooting would be best.

---

### Post by TheFu on 2022-02-18
Don't update drivers on Ubuntu by getting them from the vendor. Only use the versions provided through Ubuntu tools.  That was the first problem. There is a tool, called ubuntu-drivers which will get the current, correct, GPU drivers for the version/kernel you are running. It is best to run this from a tty in the installed OS. There is a GUI, but I've never used it.  It might be called "Additional Drivers", but running that when trying to replace GUI drivers seems like a really bad idea.  New GUI drivers require a reboot. It is one of the few times a reboot is needed for updated software on Unix-like systems.  Other drivers can be unloaded and the newer one loaded without a reboot, just the GPU drivers have this catch-22 issue.

Are you and expert in Linux and just new to Ubuntu or are you new to everything Linux? We need to know to provide relevant help.

Hibernation probably shouldn't be used.  Use standby mode.
Also, I don't think using drive encryption on either Windows or Linux is a "beginner level" task for someone new to Ubuntu.  I stopped dual booting over a decade ago, due to all the problems. Now I run Windows in a VM for about 1 hr a week, to handle those remaining things that aren't easier to accomplish on Linux.  We're all different.

Rooting is a bad idea.  Best not to do that. Never run a GUI program using sudo (as root).

---


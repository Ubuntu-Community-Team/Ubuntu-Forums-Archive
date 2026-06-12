---
title: "Issues with computer lag esp during gaming in steam; possible NVIDIA driver problem?"
date: 2022-01-09
forum: General Help
---

### Post by gangliaghost on 2022-01-09
Hello, I clean installed Ubuntu from flash drive last week. I come from Windows, but I have some experience with a terminal in Mint. I will list hardware and then details on what I have done to the system since install. Then I will elaborate on the problem, which is that my entire computer slows and lags when I have games running.

Hardware: 
spci | grep VGA 
25:00.0 VGA compatible controller: NVIDIA Corporation TU104 [GeForce RTX 2060] (rev a1)
AMD Ryzen 5 3600 6-Core Processor
1 TB SSD, which OS is installed on
2 TB HDD, which contains the games in my steam library

After installing Ubuntu, I saw the screen resolution was incorrect and my second monitor was not being detected. I followed a guide that showed me how to install my NVIDIA driver from a .run file. Unfortunately, later, I learned that installing from .run is problematic compared to apt-get command. Anyway, it seemed to work alright. I installed steam and ran 7 Days to Die in Linux (not through Proton/Wine) with no issues for several hours that night. The next day, I set my HDD to auto mount using the terminal fstab files. Then, I tried running Arma 3 through Proton. After about 40 minutes, I experienced severe lag in the game. I first tried switching from experimental version of Proton to 6.3, but I still lagged. I then tried to update the NVIDIA driver through terminal apt-get. Did not fix problem. Later, I attempted to run my other game, 7 Days to Die, which worked the other night. I cannot even move the camera due to lag. I thought it might again be the driver, so I did some reading. But while reading about the NVIDIA driver, I kept seeing people say that install from .run can cause graphics driver problems. I used this thread: 
[https://itectec.com/ubuntu/ubuntu-nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal/](https://itectec.com/ubuntu/ubuntu-nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal/) 

And I booted in recovery mode and attempted to wipe the NVIDIA driver using my file name as he suggests at the bottom. I got an error message saying it didn't exist, so I attempted to use apt-get remove --purge nvidia-current and then reinstall using apt-get. I autoinstalled recommended NVIDIA driver. I attempted to run 7 Days in Linux again, still with lag. I run nvidia-smi to find version to include in this post, but I get: 

Command 'nvidia-smi' not found, but can be installed with:

sudo apt install nvidia-utils-435         # version 435.21-0ubuntu7, or
sudo apt install nvidia-utils-440         # version 440.82+really.440.64-0ubuntu6
sudo apt install nvidia-340               # version 340.108-0ubuntu5.20.04.2
sudo apt install nvidia-utils-390         # version 390.144-0ubuntu0.20.04.1
sudo apt install nvidia-utils-450-server  # version 450.156.00-0ubuntu0.20.04.2
sudo apt install nvidia-utils-460         # version 460.91.03-0ubuntu0.20.04.1
sudo apt install nvidia-utils-470         # version 470.86-0ubuntu0.20.04.2
sudo apt install nvidia-utils-470-server  # version 470.82.01-0ubuntu0.20.04.2
sudo apt install nvidia-utils-495         # version 495.46-0ubuntu0.20.04.1
sudo apt install nvidia-utils-418-server  # version 418.226.00-0ubuntu0.20.04.2
sudo apt install nvidia-utils-460-server  # version 460.106.00-0ubuntu0.20.04.2

The GUI in Software&updates>additional drivers says I am using a manually installed driver, and does not let me change driver from GUI. In GUI about page, the driver is listed as NV164. I suspect that messing with the graphics drivers and initially improperly installing them has caused issues with my games. How do I fix this? I don't currently have any crucial data to keep, as I backed it up when first installing Ubuntu, so I am considering just reinstalling the OS and starting over. If any more info is needed please let me know.

---

### Post by TheFu on 2022-01-09
The easy method to get the current, approved, nvidia driver is to only install using 

```
$ sudo ubuntu-drivers autoinstall
```

Probably want to have NO other nvidia drivers installed before running that, so be prepared to ssh into the system when there isn't any GPU driver installed. Don't uninstall GPU drivers without having a way to get back in -be that with the FLOSS GPU driver or ssh or use a different TTY (<alt>-<ctl> F2 - F6 )

If you've never installed using direct package manager interfaces (dpkg, apt, apt-get, aptitude, synaptic, or the software center), then don't worry about removing the prior packages.  But if you did, then be careful and remove the all.

Never directly download GPU drivers from vendors on Linux.

---

### Post by gangliaghost on 2022-01-09
Thank you for response!

So would the fix be to uninstall any nvidia drivers and then run in GRUB menu in recovery start
$ sudo ubuntu-drivers autoinstall

if I used apt-get to update, and I originally installed off a .run file I downloaded from nvidia, how hard would it be to completely remove them? When I originally tried to fix in recovery terminal, I tried to ferret out the run file using the file name and --uninstall but I just got error message. 
Should I attempt earlier fix of  

> apt-get remove --purge nvidia-current  



and then 
> 
$ sudo ubuntu-drivers autoinstall

in the recovery terminal? if --purge nvidia-current  does not remove the original .run file installed, would it be more efficient to wipe and reinstall OS on the SSD? 
I will try putting .run file in home folder and run
> sudo ~/installation_file.run --uninstall`



from recovery terminal and then run purge and autoinstall commands. Then I will see if lag issue is fixed.

---

### Post by TheFu on 2022-01-09
If it was me, I'd use 
```
sudo apt-get remove --purge nvidia*
```

I'm comfortable using different ttys or just using ssh. Anything other than that, I honestly do not know.

**_Never directly download GPU drivers from vendors on Linux. _**

---

### Post by gangliaghost on 2022-01-09
Turns out that Nvidia drivers that are installed using the nvidia installer (i.e. through .run file) have a separate command to uninstall their files: sudo nvidia-uninstall

SO from recovery mode terminal I used:

> sudo nvidia-uninstall

Which took me through several prompts and loading bars. Then:
> sudo apt-get remove --purge nvidia*

Which should have got all the rest of any files I installed. Then

>  	 		 			 			 				sudo ubuntu-drivers autoinstall 			 		

 	
 


Which did something...but then gave me several error messages saying that some archives couldn't be fetched. I rebooted. In GUI I go Settings>Software&Updates>Additional Drivers. It says I am currently using X.Org X Server -- Nouveau etc. The options do allow me to select another driver. Is it safe to use the settings GUI to select the NVIDIA driver metapackage 470? That would install from Ubuntu and not the vendor right? Or do I need to use terminal for further fix?

> **_Never directly download GPU drivers from vendors on Linux. _**

Yeah talk about a lesson learned haha. Never making that mistake again. Thanks for all your help so far.

---

### Post by gangliaghost on 2022-01-09
UPDATE: 
I used terminal to switch drivers by using the autoinstall command. sudo reboot. Then I used sudo lshw -c display to confirm that Nvidia driver is being used. I also checked GUI Settings and the graphics now list my GPU card with the correct name. 

Just ran the Linux version of 7 Days to Die and it worked like a charm -- no lag or stuttering, the rest of the system ran fine as well. So, I guess my main issue has been solved! Thanks for your timely responses!

---


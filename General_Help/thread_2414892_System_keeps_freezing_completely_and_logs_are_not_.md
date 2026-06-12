---
title: "System keeps freezing completely and logs are not being written"
date: 2019-03-16
forum: General Help
---

### Post by jorgeblasio on 2019-03-16
Hi.

I've been having this issue for over a year, basically since I first installed ubuntu on this PC I built. It happens on all flavors I've tasted (Mate, vanilla and Kubuntu). Someone suggested I change the sysctl.conf to allow the kernel.sysrq more range in what it can capture.
I did (kernel.sysrq=438) and now Alt+Sysrq+R E I S U B did something, but not what it's supposed to do.

My system halted, except for the mouse cursor. I waited a couple of seconds between each REISUB key press and after pressing B, the screen went black and my video card's fans starting spinning at max and the LED on it turned red. You'd say, well, it's re-booting. But no, it did not reboot, I had to press the power button after 3 minutes to turn it off.

Now I thought, well the command worked somewhat this time, maybe logs were written. No. Logs were not written, instead I have the logs of the booting up after manually turning it on. There is no information of what halted my system in the first place.

This is very frustrating since I just don't know what the problem is and the system made to catch problems is not working.

My system:

Kubuntu 18.10 with kernel 4.20.13-042013-generic (upgraded through Ukuu)
AMD Ryzen 5 1600
16 Gb RAM 3000 Mhz CL15
Crucial MX300 275 Gb SATA mounted as / and as /boot/efi
Seagate Barracuda 2Tb SATA mounted as /home
Asrock AB350 Pro4
Radeon RX 580 Series (POLARIS10, DRM 3.27.0, 4.20.13-042013-generic, LLVM 9.0.0)

I appreciate any help.

---

### Post by jorgeblasio on 2019-03-21
Echo...

---

### Post by mastablasta on 2019-03-21
> **jorgeblasio said:**
> 
Now I thought, well the command worked somewhat this time, maybe logs were written. No. Logs were not written, instead I have the logs of the booting up after manually turning it on. There is no information of what halted my system in the first place.
.
how did you check the logs? there should be some in the folder with the ending *.old* that are from previous sessions. the rest are from latest session.

common things that completely freeze the system (but in your case it seems to be a new one so... :-k ):

[LIST]
[*]bad capacitors (check them visually) -though this shouldn't happen with new boards, but you never if they cut any corners in production to save some costs
[*]bad ram or improperly inserted RAM (run memtest) - usually other symptoms are present, but not necessarily or not until certain capacity is reached
[*]overheating in CPU or GPU - badly assembled heatsink/fan or badly applied thermal paste (install psensor and monitor the temp.)
[*]bad or improperly installed GPU (do a visual check)
[*]failing PSU or PSU lacking enough power (though other symptoms could be on display here)
[/LIST]

aside from all this, make sure you have all latest updates and that correct GPU drivers are properly installed.

---


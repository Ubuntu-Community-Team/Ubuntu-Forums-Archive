---
title: "Enable Sound Output Hyper-V"
date: 2022-12-02
forum: General Help
---

### Post by matthew-cats-dogs on 2022-12-02
How do you enable sound output in a Ubuntu Desktop 22.04 virtual machine using Windows 11 Pro and Hyper-V?

---

### Post by MAFoElffen on 2022-12-02
> **matthew-cats-dogs said:**
> How do you enable sound output in a Ubuntu Desktop 22.04 virtual machine using Windows 11 Pro and Hyper-V?

> One of weaknesses of Hyper-V is that you cannot get sound from a linux guest unless the VM has an RDP server and you go through xrdp...


Although that was possible, through adding and configuring xrdp and PulseAudio and some Hyper-V VM setting through Powershell with 20.04... [s]It isn't possible with Ubuntu 22.04 (yet). Hyper-V doesn't see any virtual sound device hardware...[/s]

That is not an issue with Ubuntu, but with Hype-V itself. If you used VirtualBox or VMware player on Windows, then sound works just fine. But you cannot use either of those if the Hyper-V feature is enabled. Hyper-V takes over "things."

---

### Post by MAFoElffen on 2022-12-02
Update.

I got sound working on an Ubuntu 22.04 Desktop VM under Hyper-V... Not straight forward.

In Windows, in PowerShell:
```

Get-VM
Set-VM -VMName "The_VM_Name" -EnhancedSessionTransportType HvSocket

```

Then in the Ubuntu Guest
```

sudo apt update
sudo apt install pulseaudio pavcontrol xdrp
cd ~/
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh 
chmod +x ./install.sh
sed -i 's/20\.04/22\.04/g' ./install.sh
./install.sh
sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool
git clone https://github.com/netrinolabs/pulseaudio-modle-xrdp.git
cd ~/pulseaudio-module-xrdp
scripts/install_pulseaudio_sources_apt-warapper.sh
./bootstrap && ./configure PULSE_DIR=~pulseaudio.src
make
sudo make install
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'
sudo reboot

```
Then when it gets to the 'xrdp" login dialog, go to "Show Options" > "Local Resources" Tab > "Remote Audio" > Settings > Select "Play on This Computer".

Have fun.

---

### Post by matthew-cats-dogs on 2022-12-04
Thanks!

---

### Post by jessian2 on 2023-02-26
hey guys

thanks for the tips

actually found some typos, take a look at my version below, please check before running it

happy coding !

```
[COLOR=#000000][FONT=Arial]sudo apt update[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo apt install pulseaudio pavcontrol xdrp[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]cd ~/[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]chmod +x ./install.sh[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sed -i 's/20\.04/22\.04/g' ./install.sh[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]./install.sh[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool

[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]git clone https://github.com/neutrinolabs/pulseaudio-module-xrdp.git[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]cd ~/pulseaudio-module-xrdp[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]
scripts/install_pulseaudio_sources_apt-wrapper.sh[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]./bootstrap && ./configure PULSE_DIR=~/pulseaudio.src[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]
make[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo make install[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'

[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo reboot[/FONT][/COLOR]



```

---

### Post by jonvel2 on 2023-05-04
So this had a few mistakes that I noticed:
1. there is no `[FONT=lucida console]pavcontrol[/FONT]` or `[FONT=lucida console]xdrp[/FONT]` packages (but there is a `[FONT=lucida console]pavucontrol[/FONT]` and a `[FONT=lucida console]xrdp[/FONT]` package)
2. the script in neutrinolabs' git repo is `[FONT=lucida console]install_pulseaudio_sources_apt_wrapper.sh[/FONT]` (and appears to hang on the "Creating <distro> buildroot ..." step.  But for me, it took a LOOOOONG time to run - about 55 minutes, much longer than I thought it would, and with no output - tail the log file in another window to see it doing something)

But other than that, this works a treat.  Now watching some guy mow abandoned properties on YouTube with full sounds ;)

---

### Post by ddcatgg on 2023-12-11
> **jonvel2 said:**
> So this had a few mistakes that I noticed:
1. there is no `pavcontrol` or `xdrp` packages (but there is a `pavucontrol` and a `xrdp` package)
2. the script in neutrinolabs' git repo is `install_pulseaudio_sources_apt_wrapper.sh` (and appears to hang on the "Creating <distro> buildroot ..." step. But for me, it took a LOOOOONG time to run - about 55 minutes, much longer than I thought it would, and with no output - tail the log file in another window to see it doing something)


But other than that, this works a treat. Now watching some guy mow abandoned properties on YouTube with full sounds 




I succeeded, thank you everyone upstairs!


According to @jonvel2's revision, the final correct code in the Ubuntu Guest should be:


```

sudo apt update
sudo apt install pulseaudio pavucontrol xrdp
cd ~/
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh 
chmod +x ./install.sh
sed -i 's/20\.04/22\.04/g' ./install.sh
./install.sh
sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool
git clone https://github.com/netrinolabs/pulseaudio-modle-xrdp.git
cd ~/pulseaudio-module-xrdp
./scripts/install_pulseaudio_sources_apt_wrapper.sh

```


The script "install_pulseaudio_sources_apt_wrapper.sh" will take a long time (approximately 10 minutes for me) to complete, but it won't produce any output. You can open a new SSH window and use the "tail -f /var/tmp/pa-build-dev-debootstrap.log" command to monitor the progress.


Then continue with the remaining:


```

./bootstrap && ./configure PULSE_DIR=~pulseaudio.src
make
sudo make install
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'
sudo reboot

```

---

### Post by cschmack on 2024-01-12
[FONT=arial]I just ran through this process and identified more typos in the latest set of commands. Here is the version that worked for me.
* Github account is neutrinolabs, not netrinolabs
* PULSE_DIR definition in configure call needs ~/pulseaudio.src, not ~pulseaudio.src
[/FONT]
```
[FONT=courier new]sudo apt update
sudo apt install pulseaudio pavucontrol xrdp
cd ~/
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh 
chmod +x ./install.sh
sed -i 's/20\.04/22\.04/g' ./install.sh
./install.sh
sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool
git clone https://github.com/neutrinolabs/pulseaudio-modle-xrdp.git
cd ~/pulseaudio-module-xrdp
./scripts/install_pulseaudio_sources_apt_wrapper.sh

./bootstrap && ./configure PULSE_DIR=~/pulseaudio.src
make
sudo make install
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'
sudo reboot[/FONT]
```

---

### Post by aneschakroun on 2024-02-16
[FONT=arial]I found another typo hope that help. Here is the version that worked for me.
* Github account is module and not modle
[/FONT]
```
[FONT=courier new]sudo apt update
sudo apt install pulseaudio pavucontrol xrdp
cd ~/
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh 
chmod +x ./install.sh
sed -i 's/20\.04/22\.04/g' ./install.sh
./install.sh
sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool
git clone https://github.com/neutrinolabs/pulseaudio-module-xrdp.git
cd ~/pulseaudio-module-xrdp
./scripts/install_pulseaudio_sources_apt_wrapper.sh

./bootstrap && ./configure PULSE_DIR=~/pulseaudio.src
make
sudo make install
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'
sudo reboot[/FONT]
```[/QUOTE]

---

### Post by aneschakroun on 2024-02-16
Finally nothing works, I don't know what happened
I see in setting the sound bar chart is moving but no sound and the output is through "Dummy Output"
can any one advice me

---

### Post by mazur-jefferson on 2024-06-01
> **aneschakroun said:**
> [FONT=arial]I found another typo hope that help. Here is the version that worked for me.
* Github account is module and not modle
[/FONT]
```
[FONT=courier new]sudo apt update
sudo apt install pulseaudio pavucontrol xrdp
cd ~/
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh 
chmod +x ./install.sh
sed -i 's/20\.04/22\.04/g' ./install.sh
./install.sh
sudo apt install build-essential dpkg-dev libpulse-dev git autoconf libtool
git clone https://github.com/neutrinolabs/pulseaudio-module-xrdp.git
cd ~/pulseaudio-module-xrdp
./scripts/install_pulseaudio_sources_apt_wrapper.sh

./bootstrap && ./configure PULSE_DIR=~/pulseaudio.src
make
sudo make install
ls $(pkg-config --variable=modlibexecdir libpulse) | grep 'xrdp'
sudo reboot[/FONT]
```


Hey guys, I followed the steps and it worked for me. Thank you
Do not forget to do the changes on windows side using powershell.

---


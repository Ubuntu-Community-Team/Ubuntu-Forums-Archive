---
title: "3 finger right click NON-persistence,"
date: 2015-03-24
forum: General Help
---

### Post by ken51 on 2015-03-24
Hi in order not to provide more information than needed - 
Hardware = Asus eeepc 901, 1 X 70mm 32GB Runcore SSD and 1 X 50mm  MFactor 64GB SSD, 2GB Ram 
Software =Multibooting - Grub default 
32GB = 3 partitions: 118MB GrubBoot EXT4; 12GB Ubuntu 14.04 LTS EXT4;  and 20GB SL 10.6.0 HFS+ (bootable) 
64GB = 6 partitions: 2.5GB XP NTFS (bootable); 14GB Win7 NTFS; 2.1GB  Linux Swap; 5.9MB free space; 30GB shared partition NTFS; 16GB Ubuntu  "home" partition EXT4. 
I have installed a number of desktop environments but generally log-in to Gnome (metacity)

xinput list =
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; CNF7129                                     id=10    [slave  keyboard (3)]
    &#8627; Asus EeePC extra buttons                    id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]



I cannot make 3 finger right click persistent... I have tried 
[http://askubuntu.com/questions/306412/how-can-i-setup-my-touchpad-multi-finger-tapping-functionality](http://askubuntu.com/questions/306412/how-can-i-setup-my-touchpad-multi-finger-tapping-functionality)  - 
sudo gedit AND/OR nano 50-synaptics.conf - but it seems like the correct settings are already there
  GNU nano 2.2.6           File: 50-synaptics.conf                              

Section "InputClass"
        Identifier "pad-config"
        MatchDriver "synaptics"

        # Enable runtime configuration of the touchpad
        Option "SHMConfig" "true"

        # One-finger tap = button 1
        Option "TapButton1" "1"
        # Two-finger tap = button 2
        Option "TapButton2" "2"
        # Three-finger tap = button 3
        Option "TapButton3" "3"
EndSection

I have also tried "If editing the 50-synaptics.conf file doesn't work, do the following: open dconf-editor and navigate to org/gnome/settings-daemon/plugins/mouse. Uncheck the box marked "active" and restart again. This will allow the synaptics settings to take precedence."

I have tried creating a touchpad.sh file 
[http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click/156545#156545](http://askubuntu.com/questions/130393/how-to-configure-the-touchpad-middle-click/156545#156545)

synclient TapButton2=2
synclient TapButton3=3 

then 
chmod +x ~/touchpad_settings.sh

then using my own user name and path to the file...

gsettings set org.gnome.settings-daemon.peripherals.input-devices hotplug-command "/home/user/touchpad_settings.sh"I have also tried the below

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) 

The weird thing is I have had this working before and the changes have been persistent. As I am compiling this I am wondering if it is an Elantech/Synaptics issue? Any ideas please? :confused:

---

### Post by slickymaster on 2015-03-24
Hi ken51, welcome to the forums.

I'm moving your thread to the General Help sub-forum, since it's a support request and chances are you'll get better help over here.

---

### Post by ken51 on 2015-03-24
Thanks V Much for moving it for me, as I posted it I thought B*l!cks it's in the wrong place...

---

### Post by anaconda on 2015-03-24
Does it work untill next time you boot your machine, if you run these 2 commands in the terminal?

synclient TapButton2=2
synclient TapButton3=3 

Editing the 50-synaptics.conf file should work, BUT iif not and f you can get  it working by running those 2 commands from terminal, THEN you could just add the script, that you already made (touchpad_settings.sh)  to startup programs (Application autostart in xfce)
That will work, IF it works when you run those commands from terminal...

---

### Post by ken51 on 2015-03-26
Hi Thanksvmuchly for taking the time to answer my question. I have set up synclient TapButton2=2 && synclient TapButton3=3 commands to run from a custom keyboard shortcut. Have found startup applications and will reboot now :-)

---

### Post by ken51 on 2015-03-26
Hoorah that worked, thanks very much for taking the time to reply :-D I am now going to try the same principle for mounting an NTFS that has my music folder on it...

---

### Post by slickymaster on 2015-03-26
ken51, please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---


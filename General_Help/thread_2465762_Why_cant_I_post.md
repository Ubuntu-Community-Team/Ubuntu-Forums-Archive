---
title: "Why cant I post?"
date: 2021-08-10
forum: General Help
---

### Post by raul-mccai on 2021-08-10
[h=1]Forbidden[/h] You don't have permission to access this resource.
 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by QIII on 2021-08-10
In which sub-forum are you attempting to post?  Which thread?  Are you attempting to start a new thread?

---

### Post by themarkw2 on 2021-08-11
Same here, I am a new account. But I just want to post a question about the advantage and disadvantage of having ubuntu as the OS of my laptop. Hopefully, someone can help us address the problem.

---

### Post by guiverc on 2021-08-11
> **themarkw2 said:**
> Same here, I am a new account. But I just want to post a question about the advantage and disadvantage of having ubuntu as the OS of my laptop. Hopefully, someone can help us address the problem.

Can you please provide the URL used where you got an error.

If you don't have it, try creating a new post, and if it fails, report the URL for the problem (that and the time it occurs allows investigations to be done on the actual cause).

Thanks for reporting your issue, Sorry it occurred though

---

### Post by raul-mccai on 2021-08-11
> **QIII said:**
> In which sub-forum are you attempting to post?  Which thread?  Are you attempting to start a new thread?

THIS ONE
I am trying to post a questions about installing an ethernet  driver   with the long sad tale of drunkness and cruelty  articulating my efforts to date.  I've tried like 5 times and I get the same damn error message each time
 I tried  posting it to this OP  as an EDIT and f got the same eror message
It's nothing but text  no attachments no special fonts  no colors   just plain text

---

### Post by raul-mccai on 2021-08-11
THIS IS WHAT I HAVE TRYING TO POST
       Trying to install an SH file to drive a Pcle Ethernet Card It uses       Realtek drivers. The box says linux but the installation CD only       has       windows drivers
     
    
     From within the       pertinent folder I ran 
     bash autorun.sh
     To install a       Realtek       ethernet driver this is what I got. I think it&#8217;s saying that it       was unable to remove the old driver.
     
    
     My mainboard had a       failure in the onboard ethernet component so I got a Pcle card I       have       three operating systems on three hard drives that I use for       various       purposes. One is Win 7 another is Ubuntu 20.04 and another       Ubuntu20.04.
     I got he Driver       installed on two but the third is giving me fits. So I backed       everything up and reinstalled the OS and this is what (infra) Bash       gave me when I ran it: 
     
    
     Check old driver       and       unload it.
     rmmod r8169
     rmmod: ERROR:       ../libkmod/libkmod-module.c:799 kmod_module_remove_module() could       not       remove 'r8169': Operation not permitted
     rmmod: ERROR: could       not remove module r8169: Operation not permitted
     Build the module       and       install
     autorun.sh: line       31:       make: command not found
     
    
     So I tried
     ./ autorun.sh
     and got the same       result
     
    
     I&#8217;ve seen people       talking about dragging the SH file to the terminal, but I have no       idea how they accomplish this. I tried cut and pasting the       contents       of the SH file to the terminal.
     When I do it runs       something so fast that I can&#8217;t see what&#8217;s happening and then       closes the terminal. 
     
    
      I right clicked       the       SH file and in properties I made sure the box to allow it to llow       it       to run as an executable. 
     Nothing happened       when I Dbbl Click it
     HOWEVER that was       how I ran it on my other ubuntu installation. Double clicking let       it run as an executable file
     
    
     
    
     I ran 
     nano autorun.sh
     **chmod           +x script autorun.sh**
     
    
     The result &#8220;seemed&#8221;       to run the code in the SH file Lots of colored Font with spacing       very much identical to the script in the SH file, but the program       ran and ran and ran. Minutes later I clicked the Button to close       the       terminal and got a message that the program was still running. I       could hear occasional read write cycles on the Hard Disk.
     It&#8217;s been an hour       and nothing had changed so I&#8217;m shutting it down.
     
    
     I&#8217;m stuck Any       ideas?

---

### Post by ActionParsnip on 2021-08-11
Run:
```

sudo apt install build-essential

```
Then retry

---

### Post by Holger_Gehrke on 2021-08-11
First: normally the drivers included with Ubuntu are quite close to current. So unless this is a completely new network chip on the card you're using - it isn't, Realtek has been making variants of this chip since at least 2012 - you should try to just use the card without trying to install drivers from some CD. Quite often these drivers are actually older than the ones already installed (check the file dates; if the files are older than the version of Ubuntu you're running, than installing them is probably a downgrade).

'rmmod' - the command to unload a kernel module - needs full administrative privileges to run. So you either need to run 'sudo rmmod r8169' or run the script with 'sudo bash autorun.sh'. Much more problematic is the missing 'make'. If 'make' - a tool to control compilation of programs according to a file full of rules - is missing, then you probably don't have a compiler installed, either. If you have some working network connection you can just run 'sudo apt install build-essential' and get make,the Gnu Compiler Collection (gcc) and some basic libraries, but if you don't have any network connectivity thinks might get interesting.

'nano' is an editor that runs in a terminal. The coloured text you saw when running 'nano autorun.sh' is syntax colouring; basically the editor colouring different parts of the script depending on their function. You should have seen some helpful hints for various functions of the editor at the bottom of the screen including '^X Exit' meaning 'hit ctrl-x to exit'. Obviously loading a file into an editor does not run it ...

Holger

---

### Post by GhX6GZMB on 2021-08-11
I have the same problem, and it's new.
Something has happened to the web site, but I can't pinpoint exactly when it happens.

---

### Post by raul-mccai on 2021-08-11
Thank you for that cogent and  educative post.
 
 
 &#8220;the drivers included with Ubuntu are quite close to current. &#8220;
 
 
 This is a fresh install of 20.04 from a thumb drive image.  I checked the box for third party and wi-fi options to be installed.  I have no idea if internet functionality is necessary to accomplish this.  So unless it was in the image on the thumb drive,  it ain&#8217;t there.
Think I should reinstall the OS and  hope?
Yah I think I shall.  What's the worst that can happen?
 
 
 
 
 &#8220;try to just use the card without trying to install drivers&#8221;
 I had no internet on my other two Operating systems until I installed the drivers.  I have none on the one in question.  I can not tell you whether  the card had  drivers pre-installed. But there is no internet.
 
 
 I thought it was interesting that my windows 7 install of the Win 7 Driver didn&#8217;t also facilitate the Ubuntu OS access to the web.  This MainBoard was running Win7 prior to my using it primarily as a linux box and I have never experienced  driver incompatibility issues when swapping the hard drives to swap operating systems.
 I&#8217;m stumped.
 
 
 I noticed the  line of commands available at the bottom of the screen when I ran nano.
 I did not understand that  ^X meant to hit Control X so I typed the carrot symbol and X  instead.  
 
 
 **So to your suggestions**
 I ran  the code you suggested:
 sudo rmmod r8169
 when I did it from the home folder nothing happened I got my prompt back is all
 then from within the pertinant folder the code returned &#8220;
 &#8220;rmmod: ERROR: Module r8169 is not currently loaded&#8221;
 
 
 So I ran :
 sudo bash autorun.sh
 it returned the following:
 &#8220;Check old driver and unload it.&#8221;
 &#8220;Build the module and install&#8221;
 &#8220;autorun.sh: line 31 make: command not found&#8221;
 
 
 I am guessing that refers to the line  in the SH script which  is as follows:
 &#8220;make $@ all 1>>log.txt || exit 1&#8221;
 
 
 It says make but the rest of it is gobbledy-gook to my eyes.  
 
 
 Ran sudo ./autorun.sh
 
 
 Same result as above but different syntax:
   Make not found line &#8220;Check old driver and unload it.&#8221;
 &#8220;Build the module and install&#8221;
 &#8220;./autorun.sh: 31: make: not found&#8221;
 
 
 Still no joy

---

### Post by raul-mccai on 2021-08-11
I re-installed the OS  hoping it'd install the drivers.
No Joy

---

### Post by raul-mccai on 2021-08-11
I did a call to get the network model

spci -knn | grep Eth -a3
    Subsystem: ASUSTeK Computer Inc. C600/X79 series chipset MEI Controller [1043:84ef]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
[B]00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 06)
    DeviceName:  Onboard LAN[/B]
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
09:00.0 USB controller [0c03]: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432] (rev 03)
    Subsystem: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432]
    Kernel driver in use: xhci_hcd
[B]0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 04)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:0123][/B]
    Kernel modules: r8169
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:859e]
    Kernel driver in use: r8169
    Kernel modules: r8169
0c:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
***********************************************************************************************************************************-
So it sees the ethernet card
It seems to see two of them.

Then I did a dmesg on the card
dmesg | grep r8169
[    1.053738] r8169 0000:0a:00.0: unknown chip XID 641
[    1.069225] libphy: r8169: probed
[    1.069418] r8169 0000:0b:00.0 eth0: RTL8168g/8111g, e0:3f:49:7d:28:df, XID 4c0, IRQ 66
[    1.069421] r8169 0000:0b:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.076283] r8169 0000:0b:00.0 enp11s0: renamed from eth0
[   38.542340] Generic FE-GE Realtek PHY r8169-b00:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-b00:00, irq=IGNORE)
[   38.667034] r8169 0000:0b:00.0 enp11s0: Link is Down
******************************************************************************************************-

---

### Post by ajgreeny on 2021-08-11
Do you actually have an internet connection whilst you are trying to install the OS?

If you do not, you will have to install without asking to install third party and wifi packages as without a connection there is no way that can be carried out.  If you can attach to an ethernet cable you can certainly select that option but if you have wiifi only then disable the option and sort out the problem, whatever it may be, after installing.
There is no real need to have or use a network connection while installing the system; I have never done so in the 16 years that I've been using Ubuntu.

---

### Post by dragonfly41 on 2021-08-11
You could confirm through another route by installing hardinfo

sudo apt install hardinfo

Then run .. hardinfo .. for an HTML report.

---

### Post by raul-mccai on 2021-08-11
Then I did a little script to try to force the module to load:
rmmod r8169
sleep 2
modprobe r8169

 rmmod r8169
rmmod: ERROR: ../libkmod/libkmod-module.c:799 kmod_module_remove_module() could not remove 'r8169': Operation not permitted
rmmod: ERROR: could not remove module r8169: Operation not permitted
raul@raul-System-Product-Name:~$ sleep 2
raul@raul-System-Product-Name:~$ modprobe r8169



I  don't know what that error message means. Other errors say there is no  such module  Can I install it with out trying to remove  anything?             
*****************************************-

---

### Post by raul-mccai on 2021-08-11
I tried 
sudo apt purge r8169-dkms
The Error was that it could not find any such package

---

### Post by raul-mccai on 2021-08-11
It did a lsmod to list the drivers  realtek is mentioned a few times but I don't know what the designations mean but they look like audio codecs to me.
```
lsmod
Module                  Size  Used by
rfcomm                 81920  4
cmac                   16384  3
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 24576  6 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  2
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
btusb                  57344  0
btrtl                  24576  1 btusb
btbcm                  16384  1 btusb
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
btintel                24576  1 btusb
bluetooth             581632  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
ecdh_generic           16384  2 bluetooth
snd_seq_midi           20480  0
x86_pkg_temp_thermal    20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
ecc                    28672  1 ecdh_generic
intel_powerclamp       20480  0
joydev                 24576  0
input_leds             16384  0
coretemp               20480  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
usblp                  24576  0
kvm_intel             286720  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
kvm                   663552  1 kvm_intel
snd                    90112  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
eeepc_wmi              16384  0
soundcore              16384  1 snd
asus_wmi               32768  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mei_me                 40960  0
video                  49152  1 asus_wmi
mei                   106496  1 mei_me
intel_cstate           20480  0
intel_rapl_perf        20480  0
wmi_bmof               16384  0
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
dm_crypt               40960  1
uas                    28672  0
usb_storage            77824  2 uas
hid_logitech_hidpp     40960  0
hid_logitech_dj        24576  0
hid_generic            16384  0
usbhid                 57344  1 hid_logitech_dj
hid                   131072  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
radeon               1474560  12
mxm_wmi                16384  0
aesni_intel           372736  6
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
crypto_simd            16384  1 aesni_intel
drm_kms_helper        184320  1 radeon
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  90112  0
lpc_ich                24576  0
i2c_i801               32768  0
drm                   491520  6 drm_kms_helper,radeon,ttm
e1000e                258048  0
realtek                24576  1
ahci                   40960  3
libahci                32768  1 ahci
wmi                    32768  3 asus_wmi,wmi_bmof,mxm_wmi
```

---


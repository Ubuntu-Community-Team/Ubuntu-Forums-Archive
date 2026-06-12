---
title: "No Sound"
date: 2007-05-20
forum: General Help
---

### Post by djbenny on 2007-05-20
there is no sound comiong out of my laptop at all using ubuntu 7.04

i have alsa installed too

---

### Post by mbradlcu on 2007-05-21
could you tell me what model make the laptop is?, I'll need more info to be of further assistance.
thanks!

---

### Post by vikramsharma on 2007-05-21
Try "lspci -v" and please post the results here , so we can have a better idea of the hardware.

---

### Post by djbenny on 2007-05-21
the laptop is a toshiba satellite pro P100 (PSPA4E)

---

### Post by djbenny on 2007-05-21
> **vikramsharma said:**
> Try "lspci -v" and please post the results here , so we can have a better idea of the hardware.

this was the only thing i could see under audio:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


in the asudio preferences it says "Conexant High Def audio"

---

### Post by vikramsharma on 2007-05-21
> **djbenny said:**
> this was the only thing i could see under audio:



in the asudio preferences it says "Conexant High Def audio"

You can try installing the latest drivers available at [Alsa]("http://www.alsa-project.org/").  You can also look for info about your sound card [here]("http://www.alsa-project.org/alsa-doc/").  You would have to compile them.  Download alsa-drivers, alsa-libs, alsa-lib-plugins and alsa-utiities and then compile them.  I am presuming that you have windows installed on your laptop goto the Device Manger and find info about the laptop's sound card.

---

### Post by djbenny on 2007-05-21
i dfo not understand how todo that lol, im new to linux you see and am bit confused...

---

### Post by vikramsharma on 2007-05-21
> **djbenny said:**
> i dfo not understand how todo that lol, im new to linux you see and am bit confused...

My bad, when you are booted into Windows right-click on "My Computer" goto "Manage" a new window titled "Computer Management" would open goto "Device Manager".  Once you have chosen the "Device Manager"  w would on the right hand side there would a list of hardware device on you computer go into the section of "Sound video and game Controllers",  double click on the title and in there you would find info on your sound card.  After you find out what sound card you have, you can go [here]("http://www.alsa-project.org/alsa-doc/") and look for info on your sound card or ask here in case of confusion.

---

### Post by Merras on 2007-05-21
I've the same problem, too... latest drivers, Sound Blaster Live 5.1 soundcard. Yesterday I had sound, tomorrow I haven't, and I didn't change anything.

---

### Post by DoctorMO on 2007-05-21
> My bad, when you are booted into Windows right-click on "My Computer" goto "Manage" a new window titled "Computer Management" would open goto "Device Manager". Once you have chosen the "Device Manager" w would on the right hand side there would a list of hardware device on you computer go into the section of "Sound video and game Controllers", double click on the title and in there you would find info on your sound card. After you find out what sound card you have, you can go here and look for info on your sound card or ask here in case of confusion.

Why not use the device manager in Ubuntu? Settings > Hardware Information (Device Manager in gnome)

you should also be ok with running this:

```
lspci -nn | grep Audio
```

example output:

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
PCI-bus-id, Hardware Type [CODE], Manufacturer, Model Name [MAKER:MODEL] (revision)

the parts in the [] are important, MAKER:MODEL in my case 1106:3059 is the specific model that my card is and I can search on that to find further support.

Please use these methods.

---

### Post by djbenny on 2007-05-21
hardware info says "82801G (ICH7 Family) High Definition Audio Controller"

if that helps i know its manufactered by conxant too...i got vista so i dont know how todo it lol its s**t lol

---

### Post by DoctorMO on 2007-05-21
did you try the new lspci command I gave? please post full output.

---

### Post by djbenny on 2007-05-21
this is what it says in vista:

> CONEXANT HIGH DEFINITION AUDIO

DRIVER:Conxant Systems Verson: 4.0.15.0 

thats all it says

---

### Post by djbenny on 2007-05-21
> **DoctorMO said:**
> did you try the new lspci command I gave? please post full output.


i did n this was the audio bit unless you want the full list of everything?

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: Toshiba America Info Systems Unknown device ff31
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

---

### Post by DoctorMO on 2007-05-21
> i did n this was the audio bit unless you want the full list of everything?

That wasn't the output from my command that is the output from lspci -v not lspci -nn can you go back and re-read my post on page 1?

---

### Post by djbenny on 2007-05-21
> **DoctorMO said:**
> That wasn't the output from my command that is the output from lspci -v not lspci -nn can you go back and re-read my post on page 1?

my bad didnt see that

ok will do now gta reboot into linux now

---

### Post by djbenny on 2007-05-21
> djbenny@laptop:~$ lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)


thats the response

---

### Post by DoctorMO on 2007-05-21
try:

```
lsmod | grep hda-intel
```

then

```
sudo modprobe snd-hda-intel
```

then

```
lsmod | grep snd
```

post ALL output from these commands, also give your sound a test

---

### Post by djbenny on 2007-05-21
> **DoctorMO said:**
> try:



```
lsmod | grep snd
```

post ALL output from these commands, also give your sound a test

only got a responce from that command:

> snd_hda_intel          20504  1 
snd_hda_codec         204544  1 snd_hda_intel
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                76680  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  1 snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm



AND NO SOUND STILL

in the udio thing its using conexant CX20551 theres the option for alsa too

---

### Post by DoctorMO on 2007-05-21
looks fine, your sound should work. what do you get in the volume control applet?

---

### Post by djbenny on 2007-05-21
i do not get any sound still

what should i set my audio prefernces too?

conxant or alsa?

---

### Post by DoctorMO on 2007-05-21
> conxant or alsa?

Alsa is the sound system, what the hell is conxant and what does it do? if all the linux apps send sound to alsa and your using conxant instead then it's not going to work.

Does the sound card appear when you go to the sound preferences application?

---

### Post by djbenny on 2007-05-21
conexant is what the speakers drivers on windows are and there seems to be things about it in linux audio preferences

---

### Post by djbenny on 2007-05-21
i set everything to aslsa and still no audio

---

### Post by rax_m on 2007-05-21
Hi, 

I've got a Toshiba P100-429 with the same contextant hda sound setup.. 

In order to fix it I had to compile my own ASL file which I think tells Linux how to handle the ACPI settlings of the laptop.. 

This guide helped me a lot:
[http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100](http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100)
and I also created my own which has a couple of other pointers :

[http://ubuntuforums.org/showthread.php?t=412986&highlight=toshiba+p100](http://ubuntuforums.org/showthread.php?t=412986&highlight=toshiba+p100)

Cheers
Rax

---

### Post by djbenny on 2007-05-21
i do not understand how todo that.

sorry

---

### Post by djbenny on 2007-05-21
this is urgent, any help would be great!

---

### Post by rax_m on 2007-05-21
Hi,

It took me a little bit of searching and reading before I finally figured it out.

Do this from the terminal (all commands should NOT be typed with quotes). 
** Make sure you backup your system as recommended first tho' !! as specified here: 
Make a dir called backup: "mkdir backup"
Then go into the backup folder: "cd backup"
Copy the images to the backup folder: "cp /boot/initrd.img-* ./"
                                                              "cp /boot/vmlinuz-* ./"

Check this link: [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) and do some reading and it will give you a better understanding of what we're trying to do. 

Theres some info on DSDT's and link to a couple of HOWTO's. I used these as a basis for starting off.
I also had to install Intels ASL compiler on my laptop (which had some dependencies like bison).

So basically I followed these steps (if I remember correctly.. some of the other links can give you the details).
You can do these at the command line. You have to open gnome-terminal or konsole. 

1. Install Intel ASL compiler. Download from: [http://www.intel.com/technology/iapc/acpi/downloads.htm](http://www.intel.com/technology/iapc/acpi/downloads.htm) 
1.a. Then unzip the file (gunzip <filename.tar.gz) and untar it (tar -xvf filename.tar). This is like winzip
1.b. The you have to read the README file in the new directory created to read how to install it 
( you may have to additionally install bison and flex thru synaptic package manager. You can open this thru Administration->Synaptic Package Manager. By Searching for bison and flex one at a time you can click on them to install. You only have to do this if compiling the intel package fails and says you need them.)

2. Then do "sudo cat /proc/acpi/dsdt > dsdt.dat" (root power needed here) this gives you the compiled DSDT without the double quotes. Remember which directory you did this in. You may have to copy the dsdt.dat file created into the intel compilers directory). 
3. Decompile the DSDT using: "./iasl -d dsdt.dat" do this from the intel/compile directory from step 1.  
This gives you two files dsdt.asl and dsdt.hex
4. Try and compile the dsdt.asl file : ."/iasl -tc dsdt.asl"
This will generate some errors and warnings which you'll have to fix with the help of this site (tho' it's in french): [http://sle.homelinux.net/olive/?p=67#more-67](http://sle.homelinux.net/olive/?p=67#more-67)  
I'm sure you can post here again if you have questions when you get to this point. Till now we haven't done anything that can mess up your install. The following two steps are the dangerous bit so make sure everything else is working first. 
5. Once you've got a fully working compilation than you can install this new file:"sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml"
6. Then tell the kernel to use this file: "sudo dpkg-reconfigure linux-image-$(uname -r)"
7. Do a reboot of the computer. 

This should work. If it doesn't then when you get to the grub menu do a safe reboot. 
This will bring you to a command terminal. There do a:

"cp <your_backup_folder>/initrd.img* /boot/"
"cp <your_backup_folder>/vmlinuz-* /boot/"

Let me know if anything is unclear. Don't think I made any mistakes.. 

Rax

---

### Post by djbenny on 2007-05-21
which file on the intel site as there are about 10?

---

### Post by rturner on 2007-05-21
For the basics, to make sure you don't have anything just set wrong, type alsamixer and go in and make sure that (1) you sound card is correct (2) nothing is muted in alsamixer that counts.  In alsamixer, move to the last setting or so using the right arrow key and see if your sound card has "mm" in the box on the bottom.  If so, hit the m key and toggle it off mute.

Also go into System/Preferences/Sound and System/Preferences/Multimedia Selector to make sure nothing is set wrong.  Click around, change settings and see if the tests work.

I forget from your first post whether you are using the sound that was built into your motherboard and/or you have a separate sound card.  If you have both, you may have to turn off sound the the BIOS to get Ubuntu to recognize your sound card.  If you only have system sound *or* a sound card, then nevermind this option.

---

### Post by djbenny on 2007-05-21
here is what my alsa mixer looks like


attached: screenshot of alsamixer

---

### Post by rax_m on 2007-05-21
Sorry.. perhaps I was a bit hasty with my complex "difficult" solution.. definitely try all the other things suggested first as it may be something minor. 

If you do need to download the other file its this one: 
Unix
ACPI CA - Unix Build Environment (.TAR.GZ 819KB)
This provides the basic implementation, which OSV's may integrate into their products as they see fit.

---

### Post by djbenny on 2007-05-21
i have tried everything so far on this thread, i've look and looked for a solution but find nothing :(

---

### Post by djbenny on 2007-05-21
i really need sound :(

help appraciated!

---

### Post by djbenny on 2007-05-21
i found this thread:

[http://ubuntuforums.org/showthread.php?p=2695035](http://ubuntuforums.org/showthread.php?p=2695035)

but i dont understand how to edit the menu.lst file and install the p[atch?

---

### Post by rax_m on 2007-05-22
I'm not sure why you have to edit the menu.lst unless you need to change grub.. But this link has detailed instructions on how to install the latest alsa libraries:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I'm afraid that if you really want to get it working you're going to have to a bit of reading and get to understand some of how linux works. I settled for no sound for about 4 months before I learned of a solution. But now that it's working, its great.

---

### Post by djbenny on 2007-05-22
the sound worked after editing the menu.lst but then the internet stopped working though

---

### Post by rax_m on 2007-05-22
Glad you got your sound working djbenny, tho' I'm not sure why your internet would stop working. Sorry..

I think you'll have to give a bit more detail about your network setup before anyone can help.. Or perhaps see if others have experienced your problem. 

Sorry, I'm not an expert and haven't seen this issue before.

---

### Post by djbenny on 2007-05-22
ok, i have a thread going about his problem

[http://ubuntuforums.org/showthread.php?t=451243](http://ubuntuforums.org/showthread.php?t=451243)

---

### Post by beanfield on 2007-06-20
> **rturner said:**
> For the basics, to make sure you don't have anything just set wrong, type alsamixer and go in and make sure that (1) you sound card is correct (2) nothing is muted in alsamixer that counts.  In alsamixer, move to the last setting or so using the right arrow key and see if your sound card has "mm" in the box on the bottom.  If so, hit the m key and toggle it off mute.

Also go into System/Preferences/Sound and System/Preferences/Multimedia Selector to make sure nothing is set wrong.  Click around, change settings and see if the tests work.

I forget from your first post whether you are using the sound that was built into your motherboard and/or you have a separate sound card.  If you have both, you may have to turn off sound the the BIOS to get Ubuntu to recognize your sound card.  If you only have system sound *or* a sound card, then nevermind this option.

This worked for my own sound problem!  I have a "00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)" intel8x0 sound card and everything was extremely quiet.  I jacked up all the volume levels in alsamixer with no results...finally, I read your response and saw that the second to last option on the far right "Duplicate" was muted.  I un-muted it and now it works.  Thanks! :D

---

### Post by Guilden_NL on 2007-06-20
New to Ubuntu but have seem a lot of mixer/WiFi issues with .16 update.

Try installing madwifi-tools via Adept.  It got my Acer WiFi going.  One difference from Windows; you have to do a full hard reset with power off or you will waste hours like I did. ](*,)

Once WiFi was up, it is stinking lightning fast!  Running 802.11g and have a 22MB cable download.  WOW!

Good luck with that WiFi.  I am probably dropping back to .15 to get the mixer problem fixed.  I cannot run alsmixer command line in .16.

---


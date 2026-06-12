---
title: "CPU monitor??"
date: 2005-09-16
forum: General Help
---

### Post by 68Firebird on 2005-09-16
I managed to get gkrellm installed but the one thing I wanted it to do its not doing, and that is to display my CPU temps. It says, "No sensors detected"

Can I get this to work? Or do I need another program to display my CPU temps?

My set up is,

Intel Pentium 4 2.4C Northwood
ZALMAN CNPS7000B-ALCU
SOYO SY-P4I865PE PLUS v1.0
Antec Sonota case, 380 true power PSU
Seagate Barracuda 80gig, 8M Cache Serial ATA
CORSAIR ValueSelect 1GIG, PC3200
ATI 9600, non pro

---

### Post by 68Firebird on 2005-09-16
Maybe linux is not for me I don't know. All I want to do is get a cpu monitor to display my cpu temps. I am at this thread trying to learn how to do it, [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I installed the "Install lm-sensors" by copying and pasting " sudo apt-get install lm-sensors" to "Terminal" and I let it do its thing. 
Now I am stuck here, 
 2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:

I copyied the text to a text editor but HOW do I run "the mkdev.sh script"??? To save the text. 

I know this must be simple to most of you but I am just not getting the directions. I copyied and pasted the text to "Text edditor" but then what?? Where do I save it?? What file?? I feel like such a idiot asking these questions.

---

### Post by 68Firebird on 2005-09-16
Maybe linux is not for me I don't know. All I want to do is get a cpu monitor to display my cpu temps. I am at this thread trying to learn how to do it, [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I installed the "Install lm-sensors" by copying and pasting " sudo apt-get install lm-sensors" to "Terminal" and I let it do its thing. 
Now I am stuck here, 
 2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:

I copyied the text to a text editor but HOW do I run "the mkdev.sh script"??? To save the text. 

I know this must be simple to most of you but I am just not getting the directions. I copyied and pasted the text to "Text edditor" but then what?? Where do I save it?? What file?? I feel like such a idiot asking these questions. But its either that or give up being the directions are just not cutting it for me.

---

### Post by 68Firebird on 2005-09-16
Comon guys through a bone. I went to this step and this is what I get in terminal,

steven@antecireliveSTEVE:~$  sudo sensors-detect

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 IF THIS IS AN IBM THINKPAD, PRESS CTRL-C NOW!
 IBM Thinkpads have a severely broken i2c/SMBus implementation, just scanning
 the bus will break your Thinkpad forever!
 If this is a non-Thinkpad IBM, we still suggest you press CTRL+C. We have
 had users reporting system breakage on other IBM systems as well.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): YES
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Success!
    (confidence 8, driver `w83781d')
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8705F / IT8712F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (0x52)
Probing for `Winbond W83627HF Super IO Sensors'
  Success... found at address 0x0290
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0x52)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0x52)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0x52)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0x52)
Probing for `Winbond W83L517D Super IO'
  Failed! (0x52)

Do you want to scan for secondary Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `w83781d' (may not be inserted):
  Misdetects:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627HF' (confidence: 8)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627HF Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? ISA

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
w83627hf
#----cut here----

Do you wan't to add these lines to /etc/modules automatically? (yes/NO)yes
steven@antecireliveSTEVE:~$  sudo modprobe i2c-senso
FATAL: Module i2c_senso not found.
steven@antecireliveSTEVE:~$  sudo modprobe i2c-sensor
steven@antecireliveSTEVE:~$  sudo modprobe i2c-isa
steven@antecireliveSTEVE:~$ sudo modprobe w83627hf
steven@antecireliveSTEVE:~$  sudo depmod -a
steven@antecireliveSTEVE:~$  sudo update-modules
steven@antecireliveSTEVE:~$  sensors
No sensors found!
steven@antecireliveSTEVE:~$

---

### Post by escobar on 2005-09-16
Have you tried gdesklets? Maybe worth a try.

---

### Post by 68Firebird on 2005-09-16
[QUOTE=escobar]Have you tried gdesklets? Maybe worth a try.[/QUOTE]

Have not tried that yet. But I am pulling my hair out. Not much hair left, lol.

All I know is what I have been doing all day has not worked. Now when I reboot to see if I can get something to monitor my cpu temps I see "loading temp sensor fail". This is so frustrating.

I don't know what to do with the text "mkdev.sh" or how to run the script. I saved the text " chmod 755 mkdev.sh" to the desk top. But what do I do from there?? How do I run it? 



What does this mean? what do I do?
" c. Run mkdev.sh from the current directory

sudo ./mkdev.sh"

Is not anybody else that has been able to get this to work able to post a step by step instructions for somebody like me who has never done this before??

---

### Post by 68Firebird on 2005-09-16
I think if somebody could just answer this one question it might be all I need.

I have the text saved to my desktop as "mkdev.sh". What do I do with that file to get it to run???

Do I right click on the file? I do not know how to run this script.

---

### Post by skatedawe on 2005-09-18
Install theese packages;

 lm-sensors
 sensord
 libsensors3

 and then just type sensors in term.

 It worked for me after struggeling with lm_sensors detect.

---

### Post by astoltz on 2005-09-18
[QUOTE=68Firebird]I think if somebody could just answer this one question it might be all I need. I have the text saved to my desktop as "mkdev.sh". What do I do with that file to get it to run??  Do I right click on the file? I do not know how to run this script.[/QUOTE]

Right click on the file and pick "properties".  From the Properties dialog, pick the "Permissions" tab.  Make sure the checkboxes by "Execute" are checked then press "Close".  Now open a terminal and type ```
cd Desktop/
sudo ./mkdev.sh 
``` That's assuming the mkdev.sh file really is on your desktop.  If it's located someplace else, you'd have to put the correct path in the cd command.

---

### Post by LOBONCA on 2008-02-29
I tried gDesklets CPU monitors but do not like them very much. They are pretty much the same and I don't think they give an accurate reading of what my CPU is really doing. Is there anything else out there to use? I am using Ubuntu

---

### Post by LOBONCA on 2008-02-29
I tried gDesklets CPU monitors but do not like them very much. They are pretty much the same and I don't think they give an accurate reading of what my CPU is really doing. Is there anything else out there to use? I am using Ubuntu

---


---
title: "Fan is not running. Yoga X1 Lenovo Thinkpad Ubuntu 20.04"
date: 2020-05-08
forum: General Help
---

### Post by lovix on 2020-05-08
ThinkPad Yoga X1 3rd generation

I have installed thinkfan. From what I've read this seems to be the best solution but the information is old.

I'm following
[https://www.linux-magazine.com/Online/Blogs/Productivity-sauce/Tame-ThinkPad-s-Fan-with-thinkfan](https://www.linux-magazine.com/Online/Blogs/Productivity-sauce/Tame-ThinkPad-s-Fan-with-thinkfan) 


And getting an error trying to change the configuration:

sudo echo "options thinkpad_acpi fan_control=1" > /etc/modprobe.d/thinkpad_acpi.conf bash: etc/modprobe.d/thinkpad_acpi.conf: Permission denied

thinkpad_acpi.conf is not in that folder and I don't find it anywhere on the system.

---

### Post by CatKiller on 2020-05-08
I have no experience of either that hardware or that software, but the command that you ran will always fail. In your command you're running echo as root (which is unnecessary) but not the redirection (so you don't have the correct permissions).

```
echo "options thinkpad_acpi fan_control=1" | sudo tee /etc/modprobe.d/thinkpad_acpi.conf
```

is the form that you're after.

---

### Post by CelticWarrior on 2020-05-08
Welcome.

How did you install thinkfan?

---

### Post by lovix on 2020-05-08
Ultimately, I am not too sure. I know I had to change the location where Software and Updates downloads from.  Then I am pretty sure I used:  sudo apt install thinkfan

And I might have: sudo apt install lm-sensors afterwards because I was getting errors about that package not being available.

---

### Post by lovix on 2020-05-08
That worked. I dont understand the bit about redirection and permissions but am looking into it.

The next step in the guide fails:  Module thinkpad_acpi doesn't seem to support fan_control

sudo thinkfan -n 

WARNING: Using default fan control in /proc/acpi/ibm/fan.

WARNING: Using default temperature inputs in /proc/acpi/ibm/thermal.

WARNING: You're using simple temperature limits without correction values, and your fan will only start at 55 °C. This can be dangerous for your hard drive.

Module thinkpad_acpi doesn't seem to support fan_control
Cleaning up and resetting fan control.

---

### Post by CelticWarrior on 2020-05-08
Well, two things: 1. CatKiller is right, the guide you followed is wrong and 2. I've made a simulation and it has no dependencies, i.e., only the thinkfan package is installed (0.9.3-2 in Ubuntu 20.04).

---

### Post by lovix on 2020-05-08
All right, I will abandon that source.

I'm trying this as a replacement:
[https://wiki.archlinux.org/index.php/Lenovo](https://wiki.archlinux.org/index.php/Lenovo)_ThinkPad_X1_Yoga_(Gen 3)#EC_Fan_issues_under_Linux

And following the updated instructions, not the original instructions (to revert to a previous version of the BIOS).  The updated instructions look to be requesting to install the latest version of the BIOS, by first installing fwupd, But fwupd already installed and this is a fresh install of Ubuntu 20.04.

The page references  [https://wiki.archlinux.org/index.php/Fan_speed_control#ThinkPad_laptops](https://wiki.archlinux.org/index.php/Fan_speed_control#ThinkPad_laptops)
Following those instructions, I'm back to where I started. 
But with the correction of not using sudo and | instead of >
I was able to make it to the next step.

(For the benefit of other newbies, I'm going to leave every little detail, more or less.)

The command su requires authentication. I'm using a live version of Ubuntu and it was resolved by

Sudo -i
Passwd

I then follow the directions on the Arch Linux page involving su, modprobe thinkpad_acpi and
cat /proc/acpi/ibm/fan

I'm still not hearing my fan come on.

So I stressed out the CPUs with this:
[https://cpux.net/cpu-stress-test-online](https://cpux.net/cpu-stress-test-online) 

Still not hearing the fans.

Following the directions on that Arch Linux page further....

I'm getting an error I saw before:
 (doesn't seem to support fan_control 
Cleaning up and resetting fan control)

root@ubuntu:/home/ubuntu thinkfan - n

WARNING: Using default fan control tn /proc/acpi/Lbn/fan.

WARNING: Using default temperature inputs tn /proc/acpl/by/thermal.

WARNING: You're using simple temperature limit without correction values, and your fan will only start at 55 C. This can be dangerous for your hard drive.

Module thinkpad_acpi doesn't seem to support fan_control 
Cleaning up and resetting fan control.

Arch Linux page suggests playing around with the config files, but I just am after having this being taken care of automatically. But it doesn't seem to be doing that.

I figured I try the last line. 

start/enable thinkfan.service

I guess that start or enable? I tried all three, none of them worked.

I also tried as root or not.

Any suggestions?

---

### Post by lovix on 2020-05-08
After running the CPUs hard for a long time, the fan did start up.  So I guess its working. Seems like its waiting longer than it should be, but the processors did respond to the load request, so maybe all is well.

Thank you CelticWarrior and CatKiller

---

### Post by lovix on 2020-05-09
On my 8th hour of problems with the fan!!  :(

Restarted the mancine and the fan is running full speed all the time.
Attempting to 
$ echo "options thinkpad_acpi fan_control=1" | /etc/modprobe.d/thinkfan.conf

Results in
bash: /etc/modprobe.d/thinkfan.conf: No such file or directory

Yet 
# Thinkfan -n

states that Thinkfan is running

At a loss, going to the next steps:

$ su
# modprobe thinkpad_acpi
# cat /proc/acpi/ibm/fan

I see the fan level is not set to auto, but the highest level (7) since Thinkfan configuration was not able to be located

The next directions are 
"You should see that the fan level is "auto" by default, but you can 
echo a level command to the same file to control the fan speed manually.
 The thinkfan daemon will do this automatically."

The man page for Thinkfan references the thinkfan.conf:  
"Thinkfan  sets the fan speed according to temperature limits preconfigured in /etc/thinkfan.conf."

There is not thinkfan.confin modprobe.d but there is one in /etc/

Maybe I shoud uninstall reinstall?
I uninstalled Thinkfan and now my machine is finally quiet!

Reinstalling via the button on 
[https://www.ubuntuupdates.org/package/core/focal/universe/base/thinkfan](https://www.ubuntuupdates.org/package/core/focal/universe/base/thinkfan)

Apparently it auto starts.  Seems weird I didn't need to authenticate to install or start up, but maybe that is since I am running a live version of Ubuntu?

Its running the same way

echo "options thinkpad_acpi fan_control=1" | /etc/modprobe.d/thinkfan.conf

produces the seame error No such file or diretory

PLEASE - CAN ANYONE HELP ME OUT ?

---

### Post by lovix on 2020-05-09
etc/modprobe/d'thinkpad_acpi.conf now exists

It is read only and empty

this will change to everyone but  should be requiring authentication:
$ sudo chmod a+rwx /etc/modprobe.d/thinkpad_acpi.conf

$ echo "options thinkpad_acpi fan_control=1" | /etc/modprobe.d/thinkfan.conf
Same error: No such file or directory.   But /etc/modprobe.d/thinkfan.conf exists.  And now has the line about options (although to see it, I had to switch out of dark mode)

this will change to everyone but should be requiring authentication:
$ sudo chmod a+rwx /etc/thinkfan.conf

$ echo "options thinkpad_acpi fan_control=1" | /etc/modprobe.d/thinkfan.conf
Same error: No such file or directory. 

WHAT IS GOING ON?? 
Now there isnt such a file    modprobe.d has thinkPAD_acpi.conf but not thinkfan.conf

Trying to copy it over into the correct directory: Permission denied

Maybe thinkfan cant be running.?

I cant see how to stop it.  cant kill the pid, which makes sense, so probably thinkfan can be running in order to copy its files

H E L P

---

### Post by lovix on 2020-05-09
exited the terminal window and sometime later my fan speed is zero, verified by

$ cat /proc/acpi/ibm/fan 

Status is disabled !!

How to turn thinkfan back on?

$ thinkfan 
does not work

previous output:
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
cat: enable: No such file or directory

$ enable 
does not work

$ enable thinkfan 
does not work

$ thinkfan enable
does not work and does not produce an error message

I am going to reboot.

---

### Post by lovix on 2020-05-09
I am slowly figuring this thing out. 

Final result., After rebooting and running the cat command referenced earlier, it appears to be running correctly.

I have put in about 10 hours, so far.

I'm working with a live distribution that I will need to repeat when i install on this machine after this test period.

---

### Post by lovix on 2020-05-09
As to what is expected with cat /proc/acpi/ibm/fan

Status will toggle from enabled or disabled
Disabled  does not mean that the fan will not come on and your hardware will  fry.  it will under suitable load. See below for how to check that it  does.
fan speed will register as "level: 5" or whatever.  Goes from 0-7

you can test that thinkfan is working by loading your cpus, and  using the System Monitor to verify. CPUs can be loaded with  [https://cpux.net/cpu-stress-test-online](https://cpux.net/cpu-stress-test-online) 

Some summary notes:
I didn't figure out how to use the commands listed in the cat comment
I  didn't figure out how to use the thinkfan.conf file to edit settings  (and I did not find out what safe settings would be for my machine,  anyway)
I had to give permission to edit the thinkpad_acpi.conf file,  although attempts to edit resulted in error messages which suggested  that it had not been done. Checking the file proved otherwise.

---

### Post by CatKiller on 2020-05-09
> **lovix said:**
> 
$ enable 
does not work

$ enable thinkfan 
does not work

$ thinkfan enable
does not work and does not produce an error message

I haven't really been following along (don't have the hardware, don't have the software, not really keen on reading tutorials on my phone for where those things apply) but the form you'd want would be something like ```
sudo service <service name> start
``` or ```
sudo systemctl enable <service name>.service
``` depending on how you've set things up.

---

### Post by lovix on 2020-05-10
Thanks, Catkiller. I can understand why you might not be following along. And being on a phone only is tough! 

I realized I might be going this alone.  Decided to document as much as I can, for the next person.

I was having some other troubles with this version of Ubuntu.  Tried a bunch of others and distributions.  

Ubuntu
19.10
Touchscreen barely worked
18.04.04
would not boot
16.04.6
would not boot

Mint
19.3 cinnamon
would not boot
18.3 cinnamon
would not boot
18.1 cinnamon
would not boot

[ Edit: Fedora Workstation works very well, few glitches. Fedora KDE might not have been as smooth. Fedora's handling of temperature management seems to surpass Windows ]

Returned to Ubuntu 20.4
Determined that the fan will run, eventually, without installing thinkfan.  Well, that is good.
But the machine was sluggish for a while after startup.  Maybe that is to be expected?  Figured I would compare to using Thinkfan...

Well, I didn't find how to get it.  

$ sudo apt-get install thinkfan 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package thinkfan

I had no luck with changing the "Download from" field in Software & Updates. Each time I got the same result above.  I have no idea what I did differently last time.

I downloaded from Sourceforge, but after reading the Readme, I decided I probably don't know enough to be using Thinkfan.   Took me reading it 100x to get to this point.  Will I accidentality fry my computer?!

20.04 seems workable. But its disappointing that there are not more OS choices. Especially if it were ever to break for my computer.  Didn't want to try Fedora (also certified by Lenovo). And stories online suggests that I will need to use thinkfan.

I did tons of research before buying this computer.  I believed Lenovo would be the best choice since I read they are the best company for long term Linux compatibility.  I really want to have a 2 in 1. The only other reasonable choice was the Thinkpad Yoga 260, but I think its too small.  I am not sure what to do. I could return the computer but what would replace it? 

I've used Ubuntu and Mint for years without too much trouble.  Not sure Linux is ready for the 2 in 1s. 

I'd be interested in any opinions on these matters.

---

### Post by CatKiller on 2020-05-10
In general my feeling is that fan control should ideally be done by the hardware itself, so in the BIOS/UEFI. Only if that's not workable - because it's not very good, say - should a software solution be used. The next best solution is to have standard (or at least well understood) interfaces so you can use standard software like lm-sensors/fancontrol to control the fans. Having an interface that's so weird and non-standard that it needs its own special application is an entirely terrible outcome.

This is also true for other hardware like mice, RGB, and so on: no software >> standard software >>>> specialised software.

Lenovo are now producing their own laptops with Linux on and have committed to upstreaming everything to make them work, as Dell have done for ages, so hopefully the situation will improve. It's possible that the situation has already improved, and you can use standard interfaces to control those fans, rather than still being the situation when thinkfan was created. I've never had a Lenovo or IBM machine to have needed to find out about it.

For the specific bit that you're stuck on at the moment, thinkfan is in the 20.04 repositories in the universe section so you'll need to enable that section before it will show up. And update afterwards.

---

### Post by lovix on 2020-05-10
Cool. Philosophy and  design logic are interesting.

If Dell had a linux ready 2 in 1, I might do that..

  	 	 	 	   I didn't find an alternative for Thinkfan, from within 2016 and later, on Google.

 
 
 
Thanks for the advice regarding universe repositories, CatKiller.

 
 
 
$ sudo add-apt-repository universe

 'universe' distribution component is already enabled for all sources.

 $ sudo apt install thinkfan

 Reading package lists... Done

 Building dependency tree        

 Reading state information... Done

 The following NEW packages will be installed:

   thinkfan

 0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.

 Need to get 35.9 kB of archives.

 After this operation, 102 kB of additional disk space will be used.

 Get:1 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) focal/universe amd64 thinkfan amd64 0.9.3-2 [35.9 kB]

 Fetched 35.9 kB in 1s (53.8 kB/s)

 Selecting previously unselected package thinkfan.

 (Reading database ... 187343 files and directories currently installed.)

 Preparing to unpack .../thinkfan_0.9.3-2_amd64.deb ...

 Unpacking thinkfan (0.9.3-2) ...

 Setting up thinkfan (0.9.3-2) ...

 Processing triggers for man-db (2.9.1-1) ...

 Processing triggers for systemd (245.4-4ubuntu3) ...

 $

 
 
  
$ echo "options thinkpad_acpi fan_control=1" | sudo tee /etc/modprobe.d/thinkpad_acpi.conf

 options thinkpad_acpi fan_control=1

 $  

   
 
$ su

 # sudo -i

 # passwd

 New password:  

 Retype new password:  

 passwd: password updated successfully

 
 
 
# su

 # modprobe thinkpad_acpi

 # cat /proc/acpi/ibm/fan

 status:		enabled

 speed:		0

 level:		auto

 #  

 
 
 # sudo systemctl enable thinkfan.service

 Synchronizing state of thinkfan.service with SysV service script with /lib/systemd/systemd-sysv-install.

 Executing: /lib/systemd/systemd-sysv-install enable thinkfan

 Created symlink /etc/systemd/system/multi-user.target.wants/thinkfan.service &#8594; /lib/systemd/system/thinkfan.service.

 #  

 
 
 Yay!

 
 
 
But behavior of the fan and performance are not noticeably different to me.

 
 
 
I will test some more and then may be looking into throttling and and possibly reverting the BIOS.

---

### Post by lovix on 2020-05-10
[SIZE=4][https://wiki.archlinux.org/index.php/Fan_speed_control#ThinkPad_laptops](https://wiki.archlinux.org/index.php/Fan_speed_control#ThinkPad_laptops)[/SIZE]

 
 
 [SIZE=4]This page (and other sites) suggest copying over a sample to thinkfan.conf. But, [/SIZE]/usr/share/doc/thinkfan/examples/thinkfan.conf.simple)  [SIZE=4] is exactly the same as the original file and the &#8220;complex&#8221; one is [/SIZE][SIZE=4]totally[/SIZE][SIZE=4] different.  [/SIZE] 

 
 
 [SIZE=4]$ sudo chmod a+rwx /etc/thinkfan.conf[/SIZE]

 [SIZE=4]T[/SIZE][SIZE=4]his will change to everyone but should be requiring authentication (which I don&#8217;t know how to do)
[/SIZE]
 
 [SIZE=4]R[/SIZE][SIZE=4]eading from thinkfan [/SIZE][[SIZE=4]https://gist.github.com/Yatoom/1c80b8afe7fa47a938d3b667ce234559[/SIZE]]("https://gist.github.com/Yatoom/1c80b8afe7fa47a938d3b667ce234559")

 
 
 [SIZE=4]$ find /sys/devices -type f -name "temp*_input"[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp6_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp13_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp3_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp10_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp7_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp14_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp4_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp11_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp8_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp1_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp15_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp5_input[/SIZE]
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp12_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp9_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp2_input[/SIZE]

 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp16_input[/SIZE]

 [SIZE=4]/sys/devices/platform/coretemp.0/hwmon/hwmon6/temp3_input[/SIZE]
 [SIZE=4]/sys/devices/platform/coretemp.0/hwmon/hwmon6/temp4_input[/SIZE]
 [SIZE=4]/sys/devices/platform/coretemp.0/hwmon/hwmon6/temp1_input[/SIZE]
 [SIZE=4]/sys/devices/platform/coretemp.0/hwmon/hwmon6/temp5_input[/SIZE]

 [SIZE=4]/sys/devices/platform/coretemp.0/hwmon/hwmon6/temp2_input[/SIZE]

 [SIZE=4]/sys/devices/virtual/thermal/thermal_zone0/hwmon1/temp1_input[/SIZE]

 [SIZE=4]/sys/devices/virtual/thermal/thermal_zone9/hwmon7/temp1_input[/SIZE]

 
 
 [SIZE=4]I copied all of that into my thinkfan.conf file[/SIZE]
 
 
 [SIZE=4]It didn't work.[/SIZE]

 
 
 [SIZE=4]I tried also [/SIZE] 

 
 
 [SIZE=4]$ find /sys/devices -type f -name "temp*_input"|sed 's/^/hwmon /g'[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp6_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp13_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp3_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp10_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp7_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp14_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp4_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp11_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp8_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp1_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp15_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp5_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp12_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp9_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp2_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp16_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon6/temp3_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon6/temp4_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon6/temp1_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon6/temp5_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon6/temp2_input[/SIZE]

 [SIZE=4]hwmon /sys/devices/virtual/thermal/thermal_zone0/hwmon1/temp1_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/virtual/thermal/thermal_zone9/hwmon7/temp1_input[/SIZE]
 [SIZE=4]hwmon /sys/devices/virtual/thermal/thermal_zone6/hwmon4/temp1_input[/SIZE]
 
 
 [SIZE=4]copied that instead.[/SIZE]

 
 
 [SIZE=4]Also didn't work:[/SIZE]
 
 
 [SIZE=4]$ sudo thinkfan -n [/SIZE] 
 
 
 [SIZE=4]WARNING: Using default fan control in /proc/acpi/ibm/fan.[/SIZE]
 
 
 [SIZE=4]/sys/devices/platform/thinkpad_hwmon/hwmon/hwmon5/temp2_input: No such device or address[/SIZE]

 [SIZE=4]readconfig: Error getting temperature.[/SIZE]
 [SIZE=4]Refusing to run without usable config file![/SIZE]
 
 
 [SIZE=4]Thinkfan maybe is not going to work for me.  Looking at something like 15 hours or more of working on getting this computer working.  Lenovo said it was ready to go (as theirs was configured).  Who knew it would be so different.  Maybe its just me though.  They might not have expected total novice to attempt this.[/SIZE]
 
 
 [SIZE=4]My next move is to decide between addressing throttling directly or downgrade the BIOS[/SIZE]

---

### Post by CatKiller on 2020-05-10
So, not going into the specifics of your particular computer, but general information to help you on your journey:

All those paths that start with /sys work like files, but aren't actually files (it's called [sysfs](https://en.wikipedia.org/wiki/Sysfs), if you're interested). They're an interface to the hardware, set up in a way that lets you do text-file-like operations on them. **cat** lets you read the contents of a text file, which in this case will allow you to read the temperature sensor readings and fan speeds, and so on. **echo** prints some text, and you already know the form of how to use echo to write some text somewhere, which for these pseudo files is setting values for your hardware - like how hard a fan should be working, for example. That's what that software control is doing - reading the temperature from whatever sensor you've set it to, and setting a fan input according to that value.

Since you don't seem to be having much luck with thinkfan, you could try the software alternative that I mentioned upthread. There are two parts, a part that identifies all the sensors and inputs that are available, and a part that controls the fans exactly as I've described above. The first part comes as a package called **lm-sensors**, and you run ```
sudo sensors-detect
``` to try to find interfaces to the sensor chips and fan controllers. Once you've done that, **sensors** will show you the outputs of everything that it's found. The second part is a service called **fancontrol**, which sets the fan speed (that you select) based on the output of a sensor reading (that you select). There's a utility called **pwmconfig** that will run a (text-based) wizard to start and stop your fans so that you can pick the right ones. If you don't like the results of the wizard it's just a text file to edit to change the behaviour.

thinkfan may be better, or they may complement each other, or they may conflict with each other: I have no idea, not having used it. I have used fancontrol, though, and it was fine.

Knowing about Tab-completion will probably make it easier to see what interfaces are actually called. You can start typing a path (or command) and press Tab to have the shell fill in as much as it can. If there's more than one way to complete it, pressing Tab twice will show you what the options are so that you can type as much extra as is needed for it to complete the rest. Some person on the Internet's interfaces may well not be called the same things as yours are.

---

### Post by lovix on 2020-05-11
$ sudo apt install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fancontrol read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
Need to get 87.4 kB of archives.
After this operation, 406 kB of additional disk space will be used.
Get:1 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) focal/universe amd64 lm-sensors amd64 1:3.6.0-2ubuntu1 [87.4 kB]
Fetched 87.4 kB in 1s (140 kB/s)    
Selecting previously unselected package lm-sensors.
(Reading database ... 187361 files and directories currently installed.)
Preparing to unpack .../lm-sensors_1%3a3.6.0-2ubuntu1_amd64.deb ...
Unpacking lm-sensors (1:3.6.0-2ubuntu1) ...
Setting up lm-sensors (1:3.6.0-2ubuntu1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594;
 /lib/systemd/system/lm-sensors.service.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3) ...

$ sudo sensors-detect
# sensors-detect version 3.6.0
# System: LENOVO 20LES1HL00 [ThinkPad X1 Yoga 3rd] (laptop)
# Kernel: 5.4.0-26-generic x86_64
# Processor: Intel(R) Core(TM) i5-8350U CPU @ 1.70GHz (6/142/10)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 17h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Hygon Family 18h thermal sensors...                         No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
/dev/port: Operation not permitted

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
/dev/port: Operation not permitted

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.4: Sunrise Point-LP (PCH)

Next adapter: SMBus I801 adapter at efa0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: Synopsys DesignWare I2C adapter (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Adapter doesn't support all probing functions.
Some addresses won't be probed.

Next adapter: i915 gmbus dpc (i2c-2)
Do you want to scan it? (yes/NO/selectively): y

Next adapter: i915 gmbus dpb (i2c-3)
Do you want to scan it? (yes/NO/selectively): y

Next adapter: i915 gmbus dpd (i2c-4)
Do you want to scan it? (yes/NO/selectively): y

Next adapter: DPDDC-A (i2c-5)
Do you want to scan it? (yes/NO/selectively): y

Next adapter: DPDDC-B (i2c-6)
Do you want to scan it? (yes/NO/selectively): y

Next adapter: DPDDC-C (i2c-7)
Do you want to scan it? (yes/NO/selectively): y


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK

$ sudo apt install fancontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fancontrol
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
Need to get 22.2 kB of archives.
After this operation, 96.3 kB of additional disk space will be used.
Get:1 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) focal/universe amd64 fancontrol all 1:3.6.0-2ubuntu1 [22.2 kB]
Fetched 22.2 kB in 0s (52.4 kB/s) 
Selecting previously unselected package fancontrol.
(Reading database ... 187396 files and directories currently installed.)
Preparing to unpack .../fancontrol_1%3a3.6.0-2ubuntu1_all.deb ...
Unpacking fancontrol (1:3.6.0-2ubuntu1) ...
Setting up fancontrol (1:3.6.0-2ubuntu1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/fancontrol.service 
&#8594; /lib/systemd/system/fancontrol.service.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3) ...

$ sudo pwmconfig
# pwmconfig version 3.6.0
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0 is AC
   hwmon1 is acpitz
   hwmon2 is BAT0
   hwmon3 is wacom_battery_0
   hwmon4 is pch_skylake
   hwmon5 is thinkpad
   hwmon6 is coretemp
   hwmon7 is iwlwifi_1

Found the following PWM controls:
   hwmon5/pwm1           current value: 255
hwmon5/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) n
There are no usable PWM outputs.

Thank you.  I don't if I did this right. I did not hear fans come on.  I will be testing.

---

### Post by lovix on 2020-05-11
I removed thinkfan.

Fan will kick on.  But less aggressively. I must have done something wrong.

---

### Post by CatKiller on 2020-05-11
> **lovix said:**
> Found the following PWM controls:
   hwmon5/pwm1           current value: 255

This would mean that it was going full tilt (it's a value from 0-255).

> hwmon5/pwm1 is currently setup for automatic speed control.

And this bit suggests that something else - probably the UEFI is in charge.

But since it says it's going as fast as it can, and you say that the fan isn't on, it seems that part isn't working properly for that hardware.

> I don't if I did this right. I did not hear fans come on.  I will be testing.

You didn't do it wrong. There's that one fan that it found that you told it not to try (because it's being controlled by something else), and it didn't find any more so it stopped. When it's got some fans to work with the next part is that it goes through a process of turning fans on and off so that you can decide which ones you want to come on when. But from the other output it probably wouldn't have worked, anyway.

sensors-detect found your processor temperature sensor, though, so you should at least be able to monitor that with the sensors command to see if the fans are having any effect.

---

### Post by lovix on 2020-05-12
Adding to the list of failed alternate OS attempts is Manjaro.  It would bounce right at selecting boot drive and cycle back to that menu. That happened a few of the other times too. Others times it would get stuck afterwards.

Starting with a fresh Ubuntu 20.04...

$ sudo add-apt-repository universe

 
 
 $ sudo apt install lm-sensors

 
 
 (takes a while without fans running)

 
 
 $ sudo sensors-detect

 
 
 (I answered &#8220;y&#8221; for everything)

 
 
 Run /etc/init.d/kmod start

 I missed this last time

 $ sudo /etc/init.d/kmod start  

 Starting kmod (via systemctl): kmod.service.
 $  
 
 
 $ sudo pwmconfig
 
 
 $ sudo apt install fancontrol
 
 
 [This is where my process here failing presently, no fan sound during the test]
 
 
 Machine after doing the above
 $ sensors -f

 coretemp-isa-0000
 Adapter: ISA adapter
 Package id 0:  +96.8°F  (high = +212.0°F, crit = +212.0°F)

 Core 0:        +95.0°F  (high = +212.0°F, crit = +212.0°F)
 Core 1:        +96.8°F  (high = +212.0°F, crit = +212.0°F)
 Core 2:        +96.8°F  (high = +212.0°F, crit = +212.0°F)
 Core 3:        +95.0°F  (high = +212.0°F, crit = +212.0°F)

 
 
 pch_skylake-virtual-0
 Adapter: Virtual device

 temp1:        +92.3°F   
 
 
 BAT0-acpi-0
 Adapter: ACPI interface

 in0:          16.15 V   
 
 
 iwlwifi_1-virtual-0

 Adapter: Virtual device
 temp1:        +86.0°F   
 
 
 thinkpad-isa-0000

 Adapter: ISA adapter
 fan1:           0 RPM
 temp1:        +96.8°F   

 temp2:            N/A   
 temp3:        +32.0°F   
 temp4:        +32.0°F   
 temp5:        +32.0°F   

 temp6:        +32.0°F   
 temp7:        +32.0°F   
 temp8:        +32.0°F   

 temp9:        +32.0°F   
 temp10:       +33.8°F   
 temp11:       +32.0°F   
 temp12:       +32.0°F   

 temp13:       +32.0°F   
 temp14:       +32.0°F   
 temp15:       +32.0°F   

 temp16:       +32.0°F   
 
 
 acpitz-acpi-0
 Adapter: ACPI interface

 temp1:        +96.8°F  (crit = +262.4°F)
 
 
 
 
 Now after stressing the cpu&#8217;s at 30% for 30seconds
 
 
 $ sensors -f
 coretemp-isa-0000

 Adapter: ISA adapter
 Package id 0: +138.2°F  (high = +212.0°F, crit = +212.0°F)
 Core 0:       +131.0°F  (high = +212.0°F, crit = +212.0°F)

 Core 1:       +131.0°F  (high = +212.0°F, crit = +212.0°F)
 Core 2:       +132.8°F  (high = +212.0°F, crit = +212.0°F)
 Core 3:       +138.2°F  (high = +212.0°F, crit = +212.0°F)
 
 
 pch_skylake-virtual-0
 Adapter: Virtual device
 temp1:       +117.5°F   

 
 
 BAT0-acpi-0
 Adapter: ACPI interface
 in0:          15.56 V   

 
 
 iwlwifi_1-virtual-0
 Adapter: Virtual device

 temp1:        +82.4°F   
 
 
 thinkpad-isa-0000
 Adapter: ISA adapter

 fan1:           0 RPM
 temp1:       +125.6°F   
 temp2:            N/A   

 temp3:        +32.0°F   
 temp4:        +32.0°F   
 temp5:        +32.0°F   
 temp6:        +32.0°F   

 temp7:        +32.0°F   
 temp8:        +32.0°F   
 temp9:        +32.0°F   

 temp10:       +33.8°F   
 temp11:       +32.0°F   
 temp12:       +32.0°F   
 temp13:       +32.0°F   

 temp14:       +32.0°F   
 temp15:       +32.0°F   
 temp16:       +32.0°F   

 
 
 acpitz-acpi-0
 Adapter: ACPI interface
 temp1:       +125.6°F  (crit = +262.4°F)

 
 
 
 
 And now 50% for 30 seconds

 
 
 $ sensors -f
 coretemp-isa-0000
 Adapter: ISA adapter

 Package id 0: +170.6°F  (high = +212.0°F, crit = +212.0°F)
 Core 0:       +168.8°F  (high = +212.0°F, crit = +212.0°F)
 Core 1:       +167.0°F  (high = +212.0°F, crit = +212.0°F)

 Core 2:       +167.0°F  (high = +212.0°F, crit = +212.0°F)
 Core 3:       +170.6°F  (high = +212.0°F, crit = +212.0°F)
 
 
 pch_skylake-virtual-0

 Adapter: Virtual device
 temp1:       +145.4°F   
 
 
 BAT0-acpi-0
 Adapter: ACPI interface
 in0:          15.17 V   
 
 
 iwlwifi_1-virtual-0
 Adapter: Virtual device
 temp1:        +82.4°F   

 
 
 thinkpad-isa-0000
 Adapter: ISA adapter
 fan1:           0 RPM

 temp1:       +163.4°F   
 temp2:            N/A   
 temp3:        +32.0°F   

 temp4:        +32.0°F   
 temp5:        +32.0°F   
 temp6:        +32.0°F   
 temp7:        +32.0°F   

 temp8:        +32.0°F   
 temp9:        +32.0°F   
 temp10:       +33.8°F   

 temp11:       +32.0°F   
 temp12:       +32.0°F   
 temp13:       +32.0°F   
 temp14:       +32.0°F   

 temp15:       +32.0°F   
 temp16:       +32.0°F   
 
 
 acpitz-acpi-0
 Adapter: ACPI interface
 temp1:       +163.4°F  (crit = +262.4°F)

---

### Post by lovix on 2020-05-12
I found a gui which I figured might help me understand whats going on.   

 
 
 [https://askubuntu.com/questions/1166768/gui-to-control-fanspeed-in-ubuntu](https://askubuntu.com/questions/1166768/gui-to-control-fanspeed-in-ubuntu)

 
 
 sudo apt install libkf5config-dev libkf5auth-dev libkf5package-dev&#8230;.[ many more]

 
 
 This took 10+ minutes

 
 
 I decided to try to speed things up by loading the CPUs with CPUx.net, while monitoring the internal temperatures with $ sensors -f   ,   to make sure I was staying well below high temperature levels   

 This did speed things up.

 
 
 $ sudo apt install git

$ git clone [https://github.com/Maldela/fancontrol-gui.git](https://github.com/Maldela/fancontrol-gui.git)
$ cd fancontrol-gui
$ mkdir build
$ cd build
$ cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_KCM=on -DBUILD_PLASMOID=on
$ make -j
$ sudo make install

I guess its not running yet?

$ ./fancontrol-gui
bash: ./fancontrol-gui: Is a directory

I searched through the directories but didn't learn enough
  $ ./fancontrol

 Loading configuration from /etc/fancontrol ...

 Error: Can't read configuration file

 
 
 I wasn't able to run either the gui or fancontrol  

Well apparenty fancontrol icon will launch.  It was an empty window for a while. But the window loaded.

---

### Post by lovix on 2020-05-13
With the gui I can watch some temps and fan speed in real time.  I can  change settings.  But it does not appear that I can change behaviour of  the fan.

This might relate ([http://thinkwiki.org/wiki/Embedded_Controller_Firmware#Firmware_Issues](http://thinkwiki.org/wiki/Embedded_Controller_Firmware#Firmware_Issues))
"The EC does not correctly initializes its 0x2f (fan control) register, so [thinkpad-acpi]("http://thinkwiki.org/wiki/Thinkpad-acpi") cannot determine the correct status of the fan control until something writes to the fan control register for the first time."

I think I may have tested that approach already by loading the CPUs until the fan kicks on. But afterwards the fan trigger doesn't seem to be operating correctly.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751689](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751689) might have some promise. I read there was a shelll script that helped another thinkpad, there.

---

### Post by lovix on 2020-05-13
Stress testing:

I can get about 200 hashes a second on all threads all processors at 100%, for suspended periods of time, which is about the same as Windows.  

The fan does go on and maintains about 80C highest of the displayed sensors (of what shows up for me in Fancontrol-GUI).  RPM maxes out around 6000 RPM.  Ambient room temperature is about 65F

I'm not sure, but I think the max temperatures permitted are 100C.

I folded the into tablet mode, as that restricts airflow, and aborted that test after seeing 86C rather quickly.

I don't know what else to do or maybe this is as good as it gets and possibly its running as designed.  I don't have the background to judge.  

But as I see it, the problem with the fan (if that's where the problem actually lies) is during boot (no fan, yet Windows will fan at boot) and also no fan right after startup (during this time the machine is extremely slow...but can be jolted into existence by loading the CPUs directly).

Thoughts, anyone?

---

### Post by lovix on 2020-05-13
Machine went into Suspend after some high temperatures were encountered under what otherwise should have been fine condidtions

Spent a week trying to make Ubuntu work. Its certified Linux ready by Lenovo. 

Thanks Catkiller, I appreciate your help and guidance.  

I may try to post a little differently on this same basic subject, unless someone has any suggestions?

---

### Post by CatKiller on 2020-05-14
I have been reading along, and it looked like you were making good progress. Sorry I couldn't be more help.

---

### Post by lovix on 2020-05-14
Thank you again for that help, plus the extras!

I was making progress?

Are there good options for adressing it at UEFI level on this forum? I have no idea what to do next with this machine. Arch possibly might have a solution but is intimidating.

---

### Post by CatKiller on 2020-05-14
> **lovix said:**
> I was making progress?
Sure. You were able to read the temperature and fan readings, and you seemed to have built up some in-depth knowledge of the quirks of the hardware.

---

### Post by lovix on 2020-05-14
True.  But I need the comptuer to be working shortly.  Do you have any ideas on who I might reach out to or where to post questions?

---

### Post by CatKiller on 2020-05-14
I'm afraid not. I think you're now our resident thinkfan expert.

---

### Post by lovix on 2020-05-14
I am proud. 

But maybe you can direct me towards the slew of Thinkpad experts?  Some of them might have some knowledge regarding the fan. 

I can't be the only one who has encountered this.  **To me, its more likely its an easy fix that no one but novices need post about.**

---

### Post by lovix on 2020-05-14
Well the easy fix maybe going to Fedora. It seems to be doing better for everything. I was testing the fan by covering it up and watching the temperatures. The fan does not work at boot up, though, as far as I could tell. But boot up was quick and the processors did seem to be free from throttling.  

I'm going to be concentrating my efforts with that distribution for a little bit at least.  

I'm sad to be moving my attention from Ubuntu but new is good and I'm learning more about Linux than I would staying with just Ubuntu and Mint.

Thanks again, Catkiller.

---

### Post by lovix on 2020-05-30
Related information: 

Ubuntu 20. 04 LTS, X1 Yoga, *gen4* *2020*. 

The fan operates properly in Ubuntu. 

This is my conclusion based on tests using LM-sensors and CPUX.net.  

It will throttle down the CPUs before starting up the fan, if going from idle to 100% in ambient temperatures of about 75°Fahrenheit.

---


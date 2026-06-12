---
title: "Ubuntu14.04 won't boot - black screen"
date: 2017-05-02
forum: General Help
---

### Post by hril230 on 2017-05-02
Hello

I have a dual-boot system with Windows 10 and Ubuntu14.04. Both were working fine yesterday, and Windows is still working, but today when I tried to boot Ubuntu I ran into errors.

The first time I tried it did boot, but wouldn't let me log in. Following some advice I found on the internet, I opened the TTY1 terminal and entered the two commands:
sudo .Xauthority .XauthorityBak
sudo reboot

When ubuntu rebooted, it did so to a black screen and nothing would load. I've tried turning my laptop off and on again dozens of times but the same problem keeps happening.
Grub is working; when I select Ubuntu as the operating system I want to run, grub loads fine. But then when I try to load ubuntu from the grub menu the black screen happens.

I am able to start recovery mode from the grub menu, and while it loads some error messages pop up that may give a clue as to what's going on; I get 'configuration error -110' and 'device not accepting address, error -71'.

I think the problem may have been caused by a failed installation; yesterday I attempted to install Esterel and it did something weird to my permissions and then wouldn't run, and wouldn't uninstall either. After that failed installation all my files were locked into read-only mode, so I think it is probably the cause of my not being able to login when I first turned on Ubuntu today.

Because of this I suspect that the 'dpkg' option on recovery mode should help, but when I try to run this I get a lot of 'failed to fetch' errors and 'Err archive could not be reached' or something (sorry for imprecise error descriptions, every time I do it the errors flash by so fast I can't really read them).

Please help.

---

### Post by Bashing-om on 2017-05-03
hril230; Ouch :

Bad things can and do happen.

We need to find out if ubuntu is still in existence ( yesterday I attempted to install Esterel and it did something weird to my permissions) .

Let's try booting 14.04 to a terminal.
Boot to grub.
In grub's boot menu highlight the latest ubuntu kernel as the boot option.
press the 'e' key for edit mode -> boot options screen
Arrow down to the line staring with linux and arrow across to quiet splash. Replace these terms with the term text.
Key combo ctl+x to continue to TTY1 .
Can you log in here with username and pass word ( no response at all to the screen when pass word is entered - enter blindly and hit the enter key) .

If you can not, then this install is not worth the effort to salvage - maybe we can copy off your personal data and prep to re-install??

[INDENT]just not a lot of options - yet
[/INDENT]

---

### Post by hril230 on 2017-05-03
Hi Bashing-om, thank you for assisting me with this problem.

I've followed your advice and was able to get to a terminal and I successfully logged in. Hopefully this means my Ubuntu operating system can be fixed. However it's not a disaster if I have to reinstall; I only use Linux for University work and I don't have any files on there that I need at the moment, the only issue would be having to reinstall all the software I'm using for a project.

I think it would take about a day to reinstall all my software, and my main focus at the moment is getting a working Ubuntu operating system on my laptop as quickly as possible, as I have a project I should be working on. I'd love your advice on what would be faster; reinstalling Ubuntu and then reinstalling the software I'm using, or trying to fix the broken Ubuntu.

If fixing is the better option, the error messages I got when I first accessed the terminal I used to log on may be helpful. I got a lot of *device not accepting address #, error -71* messages each with a different two-digit number in place of #. I also got *unable to read config index 0 descriptor *and *can't read configurations, error -110* and *device descriptor read/8, error -110*.

Thanks for your help :)

---

### Post by Bashing-om on 2017-05-03
hril230; Welp'

To soon to make a call on how long it will take to fix this install.
But, we do have it narrowed down to a likely issue in the X layer - as you can function at the terminal layer.

So, now, do you have the authority to access the desktop ?
what returns:
```

ls -al .ICEauthority .Xauthority

```

Is the graphic's card driver broke where also there is no starting the GUI ?
What shows:
```

sudo lshw -C display

```

Does X's log give us any hints ?
```

cat /var/log/Xorg.0.log

```
[ where we may resort to a pastebin to see that log file ?]
----------------------

I am about done for this session - will pick this back up tomorrow afternoon (22:00 GMT ??).
In the meantime, perhaps others here will pick up my slack .

[INDENT][INDENT]see what it ain't
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-04
Hi Bashing-om (or whoever else is reading this thread)

Here is the response I got for each of those commands.

For the authority one:
[I]-r--r--r-- 1 fuzzball fuzzball 37278 May 2 17:47 .ICEauthority
-rw-------- 1 fuzzball fuzzball 57 May 4 17:54 .Xauthority
[/I](Fuzzball is my Ubuntu login name)

For the graphics card driver one:
[I]*-display
[/I][I]        description: 3D controller
       product: GK20BM [GeForce GT 740M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33Mhz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=noveau latency=0
       resources: irq:46 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) memory:b2000000-b207ffff
*-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits 
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:6000(size=64)
[/I]
For the X log I'm not sure how to do a pastebin but I'll look that up now and figure it out

Edit: The terminal isn't letting me install fpaste, but I took a photo of the X log. I couldn't get all of it though because some of it was above the top of the screen and I couldn't scroll up, and I couldn't fit in the far right side of the screen either. Also the photo has pretty bad resolution, so if it isn't helpful let me know and I'll try to figure out another way of saving the information. Or I could try and take a better photo, maybe turning my phone to the side would work better :P

[IMG]https://fb-s-b-a.akamaihd.net/h-ak-fbx/v/t34.0-0/p280x280/18280812_10206852055100393_1594982812_n.jpg?oh=ad0e6f99947e554e56f29cf189041160&oe=590CB06D&__gda__=1494054724_9f91b105cb07c81713567fe7709bf8e8[/IMG]

---

### Post by Bashing-om on 2017-05-04
hril230; Hey ...

- Back sooner than I expected ( 12:50 GMT) -

Situation:
You do have the authority to access "your" desktop
You have hybrid graphic's; Intel/nVidia. The good thing here is that drivers are loaded .

So, are we looking at a config issue in your session ?
Let's see if we can isolate to your session.
Boot to the login screen and choose to start the guest session . What now results ?

And IF the guest session is functional ->
reboot to the F1 terminal - start the desktop :
```

sudo service lightdm start 

```
what errors does the system report here ?

We will save reading the various log files to a more opportune time :)

still
[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-04
Hi Bashing-om
Thanks for all your help so far!

I'm not sure what you mean by boot to login screen, as this is currently not working for me - I cannot get past the grub menu, except to go to TTY1.
I tried entering 'guest' and 'Guest' as login names in TTY1 but it prompted me for password and when I tried entering an empty password I was told 'wrong login' or something along those lines.
I also tried creating a new user with *adduser* from the root shell but got the following error message:
[I]Adding user 'newuser' ...
Adding new group 'newuser' (1001) ...
groupadd: cannot lock /etc/group; try again later.
adduser: '/usr/sbin/groupadd -g 1001 newuser' returned error code 10. Exiting.

[/I]When I entered the instruction *sudo service lightdm star**t* I got a black screen, same as what happens when I try to boot to Ubuntu the normal way. I returned to TTY1 with ctrl f1 and saw the following message:
[I][    76.093107] nouveau E[    PIBUS] [0000:01:00.0] GPCO: 0x4188ac 0x00000001 (0x1a70B22e)
lightdm start/running, process 1517


[/I]When I tried running the instruction again, I got *start: Job is already running: lightdm, *but all I had seen when it started was a black screen.

---

### Post by Bashing-om on 2017-05-04
hril230l Hummm ...

Read only file system ?

what results:
```

touch test
ls -al test

```

Not yet much much to go

[INDENT][INDENT]see what we can find
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-05
From that I get the output:
*-rw-rw-r-- 1 fuzzball fuzzball 0 May 5 17:07 test*

---

### Post by Bashing-om on 2017-05-05
hril230; Good .

The system it's self is consistent then .

So again, back to the GUI layer .

What all do we have to cope with for the installed GUI ?
show:
```

ls -al /usr/share/xsessions

```
And let's see what it will take to get a desktop functional . Make sure of what the focus is.

[INDENT][INDENT]aim and shoot
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-05
Hi Bashing-om

From that instruction I get this output:
[I]
total 20
drwxr-xr-x    2 root root   4096 Jun 17   2015
drwxr-xr-x 351 root root 12288 Apr 29 17:50
[/I]*-rw-r--r--      1 root root    213 Mar 27   2015 ubuntu.desktop*

---

### Post by Bashing-om on 2017-05-05
hril230; K ...

A gentle poke at the desktop activation:
```

sudo service lightdm stop
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

see then where we are.

[INDENT][INDENT]maybe
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-05
When I ran *sudo service lightdm stop* I got:
[I]stop: Unknown instance

[/I]Then the two reconfigure instructions ran with no output.

When I ran *sudo service lightdm start *I got a black screen like before. When I went back to TTY1 I saw the output: *&#8203;lightdm start/running, process 1675*

---

### Post by Bashing-om on 2017-05-05
hril230; Well !

Not all bad , lightdm is running and no errors reported .

Let's reset the desktop back to defaults.
```

rm -rf ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf ~/.dmrc

```

[INDENT][INDENT]any joy ?
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-06
I entered the instruction, and got no output so I assumed it worked with no errors. But nothing happened so I tried running *sudo service lightdm start *&#8203;and I also tried turning ubuntu off and on again and booting it the normal way, but both times I just got a black screen.

---

### Post by Bashing-om on 2017-05-06
hril230; Yuk ..

Not making a lot of sense to me yet .

What results :
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig

```

reboot.

Where I suppose that the driver config file is non-consistent and we re-build it,

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-05-06
hril230; Yukkie on me !

You are not running the nVidia proprietary driver - slipped my nind that we have nouveau here .
That " sudo nvidia-xconfig: will have no effect .
I am not even sure that nouveau uses the xorg.conf file .

As I am crossed brained now I am going to cease and desist .
Will again give my best efforts in the morrow.

[INDENT][INDENT]bad things can happen
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-06
Bashing-om haha that's okay, you're certainly doing better than I would if I had to figure this out by myself.

---

### Post by Bashing-om on 2017-05-06
hril230; Well ...

Still no closer to finding where the fault lies .
For a lack of a better thing to do, let's re-install the desktop .
```

sudo apt-get install --reinstall compiz ubuntu-desktop unity-greeter

```
looking for errors .

If the fault is within the user session these too will not be effective . But may give us some clues.

Failing here too, all I know to do is read the logs and see if we see the fault.

[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-06
When I tried *sudo apt-get install --reinstall compiz ubuntu-desktop unity-greeter* I got a lot of *Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main](http://archive.ubuntu.com/ubuntu/pool/main)... *errors (could this be because I'm not using an internet cable? I usually use WiFi so maybe my laptop can't connect to WiFi while Ubuntu isn't properly booted). I tried the same command with *--fix-missing *at the end but got the same errors. I also tried *sudo apt-get update *but got an error saying[I] Clearsigned file isn't valid, got 'NODATA'.
[/I]
Would it be easier to just delete Ubuntu from my laptop entirely and reinstall it from scratch?

---

### Post by Bashing-om on 2017-05-06
hril230; Yeah .

That do indicate no internet connection.

verify:
```

ping -c3 ubuntu.com

```

We for sure need to talk to mother to re-build the desktop.

[INDENT][INDENT][INDENT]ouch
[/INDENT][/INDENT][/INDENT]

---

### Post by hril230 on 2017-05-06
That command resulted in the output:
[I]3 packets transmitted, 0 received, 100% packet loss, time 2014ms

[/I]I'm guessing that my WiFi connection is only working in Windows.
I tried scavenging an ethernet cable from a nearby desktop that no one was using, but when I tested it in windows it didn't work ('no internet').
I could just wait till I get home and use an ethernet cable there, but I won't be home for about five hours.

If I reinstall Ubuntu from a USB will it need internet while it installs?

---

### Post by Bashing-om on 2017-05-06
hril230l Well .

No an internet connection is not required to install; however will sure want a connection to get the system updated as soon as you can connect . Security !

[INDENT][INDENT]the nuclear solution
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-05-09
hril230l ; Hey ----


Did you take that Nuclear Solution ?
Request to know a updated status .

[INDENT][INDENT]not over
[INDENT][INDENT]'til it is over
[/INDENT][/INDENT][/INDENT][/INDENT]

---


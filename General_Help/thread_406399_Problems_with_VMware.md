---
title: "Problems with VMware"
date: 2007-04-10
forum: General Help
---

### Post by Error47 on 2007-04-10
I am trying to install Windows XP Home Edition using VMware. I installed vmware, put the Windows CD in, and it started to install. While waiting for the long installation, I pressed on the "Full Screen" button because I thought it would be cool if I could run Windows on one part of the cube (beryl). It started acting up, and It didn't work, all I got was the same screen but it looked like 320 X 420 or something, it was really bad. At that point all I knew what to do was to shut off my computer by holding the power button.

After booting back up, I go to launch VMware server console, and it just says starting, then it quits. 

After typing "vmware" in a console I got this:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

This has happened before so I type in " /usr/bin/vmware-config.pl " , I get :


```
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

```


I don't understand what happened because it was working fine. 

So how do I get it to work again? And what are some of the basic things I should know about vmware, like how to exit full screen :) . Also I would like to have vmware running windows fullscreen on one part of the cube in my desktop so I can just rotate the cube to go back to linux again. 

Some of my system specs, I am running on a P4 HP desktop, 1gb ram, Nvidia graphics.

Oh and I am a beginner linux user, so I need some instructions that a newbie would understand, 

Thanks.

---

### Post by SishGupta on 2007-04-10
You need to run vmwware-config.pl as a super user

type:
sudo vmware-config.pl



to exit full screen you just hit ctrl+alt

---

### Post by Error47 on 2007-04-10
Yes, that is what I typed in before. I got the output that I wrote in my first post.

---

### Post by Error47 on 2007-04-12
It works now after I restarted my system. I had to go through the configuration again though, I hope I don't have to go through it every time.

---

### Post by Phrawm48 on 2007-04-12
VMware Player or Server?

I've only just gotten Server working on my Dapper unit.  As such, I have only a little knowledge.

What I'd try is to do a complete reinstall of VMware.  If using *sudo* doesn't work, try *sudo -i* to login as root and then install (I had to do that...)  Use the default options -- you'll be glad you did when you try to setup networking...

After reinstalling VMware, if the earlier, failed XP installation is still detected by the newly reinstalled instance of VMware, delete its files from whatever directory VMware keeps them in.

Then reinstall XP and get it running before playing with any VMware screen options.  

Finally, use VMware to install the VMware tools that add some GUI and screen resolution hooks to the virtual o.s.  The status area in the lower-left of VMware server reminds you to do that...

Cheers & hope this helps (at least a little),
Ric
SFO

---

### Post by Error47 on 2007-04-12
I am using VMware server. 

When I had posted my previous post, I had it working, with windows installed. After another reboot, vmware does not work again. It will not start, when I type " vmware " in the console, I get the error message I posted above. Then the config also gives me the same thing.  I do not understand what is wrong because I had it working. 

It took a few people to walk me through the installation of vmware. I don't think I could do it again, because if I mess something up again, I will not be able to fix it. It took me about 7 or 8 hours to get it working, basically the whole day.  I need a way to fix it without re-installing vmware , and windows all over agian.

---

### Post by Phrawm48 on 2007-04-12
In the Gnome menu bar (default location in top of desktop) try choosing **Applications** > **System Tools** > **WMware Server Console**.

Does that start VMware, or at least try to start VMware?

If you get a message about needing to be root, use **Applications** > **Accessories** > **Ala Carte Menu Editor** to modify the **VMware Server Console** menu item's **Command** text entry area to read [FONT=Fixedsys]gksudo vmware[/FONT].  When you use the menu item to start VMware it will prompt you for your password; supplying it will provide VMware with the temporary root privilege level it needs to modify system stuff...

By the way, as a relatively new Ubuntu user (about eight weeks), I found the O'Reilly book **[*Ubuntu Hacks*]("http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209")** to be really useful.  The book describes a lot of basic Ubuntu config and setup enhancements, including the installation and setup of VMware Server.  In fact, I used the book to get my VMware Server running...

Cheers & hope this helps,
Ric
SFO

---

### Post by Error47 on 2007-04-12
I do not have the program Ala Carte Menu Editor. 

Also I tried to run  gksudo vmware  directly in the console, I got the same result as I stated before, so perhaps that wont work?

As for the book, I'll look for it at my next visit to the book store.

---

### Post by M$LOL on 2007-04-13
You need to go to /etc/vmware and delete a file called not_configured (I think that's the name anyway). I spent ages trying to find the solution to this nagging little problem, and I finally found it on their forums.

---

### Post by Error47 on 2007-04-13
Thanks, deleting that file worked. Two new problems came up though. I never had sound before, which I want to get fixed. But I did have internet on my virtual machine, now I cannot get internet on there. I get an error message when I start up it up. 

"Could not open /dev/vmnet8: No such file or directory
Virtual device Ethernet0 will start disconnected."

And for the sound I get:

" Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected. "

Since one of the main reasons I installed windows was to work with itunes, I need both the sound and internet. How can I get these two problems fixed?

---

### Post by M$LOL on 2007-04-13
Try running vmware-config.pl again. When it gives you the option to leave the network settings as they are, don't, reconfigure the network instead. As for your sound problem, it sounds like the device is being used by something else. Make sure that you don't have any other applications using the soundcard at the same time (even something like Firefox can cause this sort of problem, say if you're on Youtube, even if it's not actually playing any sound FF may still be using the device).

---

### Post by Error47 on 2007-04-13
Thanks alot, Internet & Sound are both working now.

Another thing, how can I get these three devices to work in windows with vmware server.

1. External HD
2. iPod
3. USB flash drive

---

### Post by Error47 on 2007-04-14
I keep getting that problem with vmware, where it won't start. Deleting that file works, but everytime I want to use vmware I have to go in and delete that file? Sometimes it works, sometimes it doesn't. It keeps creating that not_configured file. And I have to do work just to open vmware. I still can't get my external HD to work.

Now after I open up vmware, and try to power on windows. I get this error message

"Unable to change virtual machine power state: The process exited with an error:
End of error message."

---

### Post by M$LOL on 2007-04-14
Right, well for your USB stuff, go to your VM and hit "Edit Settings". Under Hardware, click "add", and add the USB Controller. To allow the VM to use the devices, power it on and VM -> Removable Devices should do the trick.

If not_configured keeps appearing, this means that there is some service failing, so perhaps something is broken. Anyway, to stop it reappearing, go to /etc/init.d and find a file called "vmware". Right-click and change the permissions to allow root to write to it. Then fire up a Terminal and type "sudo gedit /etc/init.d/vmware and find a line that says "set the 'not configured' flag". Comment out every line from the **if** right down to the **fi**. Save and reboot to see if it works.

As for your last problem, check your /tmp/vmware-<username> directory for logfiles. They usually give info regarding why it's not working. I suspect it may be something to do with the configuration script screwing up the permissions of the VM, but that's just a guess. You could try creating a new VM to see if that's the case, but the logfiles should tell you anyway.

---

### Post by Error47 on 2007-04-14
Hello again, I have attached the files from /tmp/vmware-<username> . I couldn't make sense of them, perhaps you can tell me whats wrong. I can't start up windows because I still keep getting  " Unable to change virtual machine power state: The process exited with an error:
End of error message. "

---

### Post by M$LOL on 2007-04-15
Aha, the problem is that Vmware can't find vmmon (the monitor module) and fails. This could be caused by the vmware-config.pl script screwing up that module. Were there any errors the last time you ran it? Also, post the output of [COLOR="Red"]lsmod | grep vmmon[/COLOR] here.

---

### Post by Error47 on 2007-04-15
Aha, it's working now. I did nothing to fix it exept reboot. The thing is, I rebooted twice before to see if it would work, and It never did. Maybe it just needed a good night sleep? But anyway, it seems to be working now.

---

### Post by M$LOL on 2007-04-16
Hmm, not sure why that happened, perhaps the permissions on the vmmon were messed up... Anyway, glad it's working for you now :)

---

### Post by Error47 on 2007-04-16
I am still trying to get my external firewire hard drive to work thought. I am not sure if I need to add a hard drive in the settings or what. When I try that it asks me to allocate space or something, I just want to read it in windows.

---

### Post by jimbo99 on 2007-04-16
I recently installed vmware under ubuntu and found that unfortunately I was not able to actually play games under the VMware with Windows.  At this point, since I don't really  need any windows applications as the linux ones do the trick (or I can just dual boot), vmware is nothing more than a novelty item.  It really doesn't have a purpose for me.  If you haven't learned you can't run 3d accelerated apps--for the most part.

They are virtualizing the OS but not all the hardware.  They are simply redirecting to either their own drivers or through linux directly--which makes most of it just a novelty.

I don't recommend vmware  unless you have a very specific need for it.

---

### Post by Error47 on 2007-04-16
There are a few things I need with windows. None of them are heavy programs, things like nero, dreamweaver, and some other things that only work in windows. I have found it very usefull. I just need to get my damn HD to work on it.

---

### Post by M$LOL on 2007-04-17
> **jimbo99 said:**
> I recently installed vmware under ubuntu and found that unfortunately I was not able to actually play games under the VMware with Windows.  At this point, since I don't really  need any windows applications as the linux ones do the trick (or I can just dual boot), vmware is nothing more than a novelty item.  It really doesn't have a purpose for me.  If you haven't learned you can't run 3d accelerated apps--for the most part.

They are virtualizing the OS but not all the hardware.  They are simply redirecting to either their own drivers or through linux directly--which makes most of it just a novelty.

I don't recommend vmware  unless you have a very specific need for it.

VMWare Workstation has experimental D3D, still not good enough for graphic-intensive high-end games, but it's not designed for that. VMWare does an excellent job and can be used for a wide range of tasks, and I've never had a problem with it.

Anyway, for Firewire, I would mount the device in the host, and then point a shared folder in the VM to it.

---

### Post by Error47 on 2007-04-17
I have VMware Server, I think I need this workstation edition for the shared folder feature. I don't think I can share things between host and virtual machine in the server edition. How can I upgrade to workstation without loosing my installation of windows?

---

### Post by M$LOL on 2007-04-18
Uninstall Server and install Workstation. It won't delete your VM folder, but I'd backup just in case.

---


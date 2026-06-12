---
title: "having an issue booting while docked"
date: 2024-07-31
forum: General Help
---

### Post by nariub on 2024-07-31
This feels little but I am again at a loss


I just installed 24.04 onto a Dell 7490 which went well
I got a Dell WD19DCS USB-C docking station
and two external monitors


all kinda works except one thing


lid closed on the laptop
I don't see the bios boot, or the prompt for the disk encryption, or the user/pass screen they are all on the built-in laptop screen
I have to open the lid to the laptop and interact with the laptop directly
then..
I went into the displays and disabled the built-in screen
which moves the primary to one of the external monitors which is fine but none of this happens until after the boot process completes..


Oh and for the folks that want to know
I am cheap and buy mostly used refurbished laptops online so that's why i have an old/new 7490
even got it 24.04 to install on UEFI and enabled secure boot too..
but the boot thing is annoying..

---

### Post by nariub on 2024-08-01
And for the curious I have updated the BIOS on the laptop and the Docking station to the latest 

Is this just the new normal for docking stations?
I have an old 6520 connected to a PRO2X and when its docked it knows about it and shows the the post and login info on the docked external monitors like a workstation would..

---

### Post by nariub on 2024-08-12
ok progress
I read these URLs
[https://ubuntuforums.org/showthread.php?t=2473462](https://ubuntuforums.org/showthread.php?t=2473462)
[https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor](https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor)
[https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor](https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor)




and 
sudo cp ~/.config/monitors.xml /var/lib/gdm3/.config/monitors.xml
sudo chown gdm:gdm /var/lib/gdm3/.config/monitors.xml


and now after I unlock the hd encryption, which is still on the laptop screen, I do get my gnome login/pass on the external monitors..


anyone know how to get the HD encryption prompt to show on the external monitors, or even on all monitors.  I am not even seeing the external monitors have a signal until the HD is opened and OS boots..


I mean I can keep doing this work around, 
  waiting a suitable amount of time,  
  then blindly type in the HD password, and 
  hope I then get passed along to the GDM login
  
But it just feels cludgy, ya know?


Marion


same question posted here
[https://askubuntu.com/questions/1522239/behavior-when-connected-to-a-usb-c-docking-station]("https://askubuntu.com/questions/11738/force-gdm-login-screen-to-the-primary-monitor")
[https://ubuntuforums.org/showthread.php?t=2499566](https://ubuntuforums.org/showthread.php?t=2499566)
and 
[https://www.dell.com/community/en/conversations/latitude/7490-behavior-when-docked-to-wd19dcs/66abe87347effa74c4831ab2](https://www.dell.com/community/en/conversations/latitude/7490-behavior-when-docked-to-wd19dcs/66abe87347effa74c4831ab2)

---

### Post by nariub on 2024-08-13
and i can interrupt the boot process to look at the bios
hit Fn F8 and switch the bios screen to the external monitor
exit the bios
and the freaking bootsplash is now on the external monitor
but it doesnt keep doing that after I power off and reboot..
its like it knows 'how' to do it right but just won't for some reason..

it feels like I am talking to myself some days.. :-)

---

### Post by nariub on 2024-08-22
Weird that, I gave up on Ubuntu 24.04 and re-installed 22.04.4 and it all works as advertised.. I didnt have to do anything for it to display the HD password on all available screens.  Crazy ain't it..  I guess 24.04 is a work in progress huh?

---

### Post by nariub on 2025-01-07
So it turns out it is intentional and probably wont be fixed.
The developers pulled the drivers out of the boot for performance reasons and think nobody runs on docking stations anymore.. so .. there you have it..
suggestion was to
> [COLOR=#000000][FONT=&quot]You should be able to work around it by adding 'amdgpu' to '/etc/initramfs-tools/modules' and then run:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]  sudo update-initramfs -k all -u[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]or get the system to automatically insert all the modules you're currently using by changing the MODULES line in '/etc/initramfs-tools/initramfs.conf' to MODULES=dep and again:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]  sudo update-initramfs -k all -u

[/FONT][/COLOR]


[COLOR=#0C0D0E][FONT=-apple-system](Source: [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/2069039](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/2069039)[COLOR=#0C0D0E][FONT=-apple-system])


[/FONT][/COLOR]

---


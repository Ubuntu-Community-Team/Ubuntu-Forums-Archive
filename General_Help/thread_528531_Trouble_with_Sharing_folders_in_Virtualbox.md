---
title: "Trouble with Sharing folders in Virtualbox"
date: 2007-08-18
forum: General Help
---

### Post by kingleer on 2007-08-18
After doing the following

#install xp in virtualbox
#install the virtualbox additions
#made a folder in my home folder on ubuntu called virtualboxshare
#without xp running, went to settings in the xp machine, shared folders and navigated to this folder
#boot xp, then click start, run and entered the command:

Code:

net use x: \\vboxsvr\virtualboxshare



but I get the following error  -

Get the following error in Virtualbox Xp installation

System Error 53 has occurred.

The network path was not found.



When I try to add a transient folder with Virtualbox directly, Virtual box gives me the following error - 

When I try to add C:\doc I get the following error -


Shared folder path 'C:\doc' is not absolute.


Result Code:
0x80070057
Component:
SharedFolder
Interface:
ISharedFolder {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
Callee:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



I have consulted the Virtualbox manual with no luck. 
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
I also found a guide, through google, which was no help.
[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)

The other posts in this forum regarding this issue all gave similar solutions to my problem, which I had already tried unsuccessfully. 

Does anyone have suggestions as to what I may be doing wrong or alternative solutions?

---

### Post by kingleer on 2007-08-18
Nevermind, I found an alternative solution bymyself.

Source is: 

[http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html](http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html)

The solution is to just share a usb stick with Virtualbox and ubuntu. This is acceptable for me since I usually carry a usb stick with me everywhere. 

the solution: 




If you want to access usb devices from the virtual machine, follow these steps. You can omit them and directly reboot if you are not going to be using usb devices from the guest.

sudo addgroup usbfs
sudo adduser $USER usbfs

** For the next step you have to know the id for the usbfs group that you have created. To do this try

cat /etc/group | grep usbfs

and look for the number after "usbfs:x:". In the next command, replace 1002 in the next command with this number**
echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" | sudo tee -a /etc/fstab

Now reboot to allow the new group and user permissions to be updated.





I've decided not to delete my thread, because someone else might be having a similar problem.

---


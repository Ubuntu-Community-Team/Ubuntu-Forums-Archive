---
title: "Connecting to Ubuntu from Windows over the Web"
date: 2007-07-10
forum: General Help
---

### Post by jusmurph on 2007-07-10
What i want is to be able to connect to my home computer from work. I would like to be able to control the computer remotely and later be able to transfer files from my home to work.

My home computer does not have an External static ip (though it does internally) and it sits behind a nat router. My home computer runs Ubuntu and i am on Win XP at work.

Previously under windows i used to use logmein.com which was great. Now i simply don't have that option.

---

### Post by dkirk on 2007-07-10
Hey,

Click on System | Preferences | Remote Desktop.  Tick 'Allow other users to view your desktop' and make sure 'Allow other users to control your desktop' is ticked.  Set the security to ask for a password and not ask for your confirmation (because you will be at work, so you can't confirm).

You will need to forward port 5900 from your NAT device to your PC.

Now, on the Windows PC, install a VNC client and connect to your Internet address:5900.  If your Internet address changes often, then use some dynamic DNS service.

-- 
Later

David Kirk

---

### Post by jusmurph on 2007-07-11
Cheers :grin:

---

### Post by hooksie on 2007-07-11
Alternatively, if you just need terminal access, you can install and use SSH.

sudo apt-get install ssh

SSH uses port 22.  To connect, you can use [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") from the windows machine.  

Again, as dkirk said, if your IP is constantly changing, you should use some sort of dynamic DNS system.  Dyndns.org is compatible with Linux.

---

### Post by arrrghhh on 2007-07-12
i'm trying to either ssh or vnc into my ubuntu box at home... i can't figure out how to get it workin.  i'm using xfce, and i don't have that setting for remote desktop...

i'm on the original poster's side too - logmein was sweet.  i miss it...

---

### Post by dkirk on 2007-07-12
arrrghhh,

Install a VNC server.

-- 
Later

David Kirk

---

### Post by bsawler on 2007-07-16
Some other useful info. 

I'm not sure how to configure your work computer, as most offices I have been in, disabled any software installations, like a VNC Viewer or possibly you can use connect via your browser with the help of JRE, which would probably be installed at the office. 

1. On your home machine.  Set up a VNC server:
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

2.  Connect to your home computer using no-ip to track your dynamic ip:
[http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

NOTE: If you cannot "make" the executables.  Check that all "libc6" dependencies are satisfied.  I have a i386 machine and it would not make until I installed libc6-dev, which are found in Synaptic Package Manager.

I am a month into my Linux experience... love it.  I can follow the above, so anyone can!

Cheers,
Bradley

---

### Post by gtr225 on 2007-07-16
Hi this worked fine for me however I'm not able to switch users on the Ubuntu machine from the Windows Machine. Is there anyway to accomplish this?

---

### Post by Gruelius on 2007-07-16
If i were me i would setup ssh + X server forwarding. You would log in as the required user, then you can fire up individual apps or if you wanted you could fire up the whole WM desktop.

---


---
title: "Using oracle free cloud server and connecting shows blank screen"
date: 2023-09-30
forum: General Help
---

### Post by xboxhaxorz on 2023-09-30
So im a windows user but am trying the free cloud server and ubuntu was a free OS choice






I followed this guide to get everything going [https://www.youtube.com/watch?v=NKc3k7xceT8](https://www.youtube.com/watch?v=NKc3k7xceT8)
But after i set the passcode via ssh whenever i remote in using RDC, its a blank screen


I rebooted the server multiple times and its not working, prior to setting passcode via ssh it did show the login screen


So i deleted the saved passcode from RDC and now it shows me the ubuntu server JUST CONNECTING login screen, and when i enter the passcode there, it quits RDC


Any ideas? I am not experienced with linux but im in IT in relation to windows OS

---

### Post by TheFu on 2023-10-01
What's "RDC?"  That's a new term to me. Do you mean RDP?  I don't think RDP is installed/enabled by default on any Ubuntu release.

It is possible that Oracle changed their default install to be ubuntu server, not desktop.  Linux servers don't have any GUI.  ssh is how they are managed.  The learning curve it very steep and there won't be any point-n-click to control it.  I have to say, skimming that video, I saw a bunch of things I'd never seen before, but I don't really use a standard Linux desktop.  Mine is customized for performance.

I get the feeling you don't listen to me. That's fine.

As a beginner, I'd strongly suggest using a local virtual machine for at least the first 6 months as you learn the basics.  Making RDP available over the internet is crazy, especially if only a password is used to limit access.  Use ssh with ssh-keys for remote access.  Tunnel RDP through an ssh connection and only allow RDP to be accessed from "localhost", never any other IP.    

[https://ubuntuhandbook.org/index.php/2020/07/remote-desktop-sharing-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/07/remote-desktop-sharing-ubuntu-20-04/) shows how to enable a remote VNC daemon. Beware of any instructions that don't use ssh, since most other encryption is substandard when compared to ssh with a tunnel.

Or better, use a remote desktop that handles this security for you, like x2go.  Gnome and KDE don't really work with remote desktops, so everyone usually loads a lighter DE - say XFCE4 or Mate - and connects using that lighter GUI. 

Probably best to ensure that Wayland isn't the display server too. Choose xorg.  It is just easier to use x2go. There's an x2go client for Windows and you can setup ssh-keys to be used, which will make the connection 1000x more secure than using any password.

BTW, to learn Linux, work through this book: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  If you do 1 chapter each week, then in a few months, you'll have gone beyond "beginner" level knowledge.

---

### Post by MAFoElffen on 2023-10-01
Welcome to the Ubuntu Forums. I am here is help you as a new user.

I have experience with Windows OS (Desktop & Server), Linux (most Distro's including Ubuntu) and cloud services. I will try to assist you.

*** Note: That video was for Ubuntu 20.04, and Oracle Cloud at "that" point of time. In the description for that video, it said that he had updated the instructions in a different video....
> 
PLEASE NOTE : Since making this video, there are a couple of settings that I have found that speed up the responsiveness of this Videos Ubuntu VPS noticeably. The Video explaining what they are is only abound 4 minutes long, and can be found here : [https://cloudtechlinks.com/How-to-Spe](https://cloudtechlinks.com/How-to-Spe)...


I added an Oracle Free tier trial to my Oracle account, and was going through the instructions in that tutorial was telling you to do, so that we would be on the same page... And so I could have guided you through what was given you, BUT-- The Oracle Data Center that I selected, because it is near me, does not have the capacity to provision an instance for me. (Even though this is "Sunday" in this Geographic Region... And it has no other domains to choose from in that Datacenter. The home Datacenter is locked to the Datacenter you choose when setting up the account... So that was a big fail to be able to support me.
> 
Your home region is the geographic location where your account and identity resources are created. You select the home region for your tenant during sign-up, and it is not changeable after your tenancy is provisioned.

My interaction with their support was entertaining. They said to try back in a few hours. I asked if it was different for paid commercial accounts. They said yes. The home regions is still the same, but paid accounts can 'subscribe' to other regions... I am thinking that like other cloud service providers, if you subscribe to available resources in another region, those charges are incurred accordingly.

No matters. LOL

Note that Oracle Cloud has changed since that video was uploaded. When you go to pick the VM type Ubuntu, when you choose the type, it has minimal, and minimal aarch64... He picked an ARM processor for his shape, so that would mean you would have to select Ubuntu minimal aarch64 as the image to be able to run on it... When you select that in the Oracle control panel. You then have to set the shape to Ampheres, but the resource panel for that has changed.

You have to read the fine print that is elsewhere to stay within the "free" confines of the free tier or you will be charged. Which means 2 AMD or
> 
Ampere A1 Compute instances (Arm processor): All tenancies get the first 3,000 OCPU hours and 18,000 GB hours per month for free for VM instances using the VM.Standard.A1.Flex shape, which has an Arm processor. For Always Free tenancies, this is equivalent to 4 OCPUs and 24 GB of memory.

You get more resources with Ampheres, but still need to ensure you set the resources to 4 OCPUs & 24 GB memory. If you follow what the video says, and slide the sliders all the way to the right, you are easily trespassing into paid plan territory on allocated resources...

I went through "viewing" that video tutorial... I jumped through those hoops to support you...

He is "RDP", which means Windows OS'es Remote Desktop Protocol.

Since you are on a Windows 10 Host and trying to remotely connect to your Ubuntu Cloud instance hosted at Oracle Cloud, on a free tier... That that tutorial instructed how to open up RDP's port 3389 through the Oracle Cloud firewall... You did that right?

Then it gives instructions to ssh via putty to your Ubuntu Cloud instance using Putty... It connected via ssh right?

It gave these config commands:
```

THE FIVE CONFIGURATION COMMANDS :
---------------------------------
1. sudo apt update && sudo apt upgrade -y
2. sudo apt-get install ubuntu-desktop xrdp stacer -y
3. sudo cp /etc/iptables/rules.v4 /etc/iptables/rules.v4.bak && sudo truncate -s 0 /etc/iptables/rules.v4
4. sudo rm /usr/share/polkit-1/actions/org.freedesktop.color.policy
5. sudo passwd ubuntu      Example password : t6y1x9n6h7j1  so long,complex and not in a dictionary

```
The desktop and xrdp is installed...And for TheFu's benefit (because I know he isn't going to waste his time watching this video...) Oracle instances come with their own IP rule table in each instance. That is additional to the account oracle cloud firewall IP table rules to connect to the instance. To disable having to manage 2 sets of IP rule tables, he disables Ubuntu's IP table rules by truncating the file to 0 bytes, so that it just uses the Oracle Cloud instance IP table rules to connect to the instance...

He then proceeds to reboot, then connect from RDP from a Windows RDP session.

It skips a few vital xrdp configuration steps on the Ubuntu instance side... I'll get into that in another post.

---

### Post by MAFoElffen on 2023-10-01
Start putty and reconnect to your Oracle Cloud Ubuntu instance via ssh.

After logging in, then do this:
```

sudo systemctl enable xrdp
sudo systemclt start xrdp
sudo systemctl status xrdp

```
Since you are new to the Forum... Reply using the "Adv Reply" button to get to the Advance Post Editor. Select the "#" icon from the Tool Bar. That will insert Code Tags into the new post. Copy and paste the output of those commands between those Code Tags. Please post that output. It is a Forum policy to post all commands and raw output within CODE Tags.

---


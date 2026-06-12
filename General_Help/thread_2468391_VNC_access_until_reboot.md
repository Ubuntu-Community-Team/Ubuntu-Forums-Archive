---
title: "VNC access until reboot"
date: 2021-10-27
forum: General Help
---

### Post by itaki on 2021-10-27
I have a brand new installation of Ubuntu on a Raspberry Pi. I set up screen sharing by going into the sharing settings menu and turn it on and set a password. Then I go over to my mac, command+K to connect to server, type in the Raspberry Pi's name and password and BOOM I'm in.

Until I reboot. Upon reboot, I check all my settings again and they are all on. Go to my Mac, command+K, type in the name and password and it produces this error.

[FONT=&amp][B]Connection failed to “blinky”.

[/B]Unable to communicate with “blinky”.  Make sure the remote computer is available and the firewall is not blocking screen sharing.

[/FONT]This has been driving me crazy. What's even weirder is that if I use the raspberry pi os, which is a debian branch, it continues to work even on reboot. But not with Ubuntu. Not sure if it's an Ubuntu problem or a Mac problem. All Theories welcome.

---

### Post by ActionParsnip on 2021-10-27
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by gsahli on 2021-10-27
What VNC server do you have installed? On my pi with raspbian, it installed RealVNC server. I have to use VNC Viewer from RealVNC to connect.

---

### Post by HermanAB on 2021-10-28
Hmm, VNC is mostly a Windows thing.  With UNIX computers (Linux/Mac/BSD) SSH generally is much easier to get going and is secure and more powerful.

---

### Post by itaki on 2021-10-28
I'm developing a robot that opens and closes blast gates. I'm writing all the code on my mac, then wanting to run it on my raspberry pi which is in another part of the shop. Once I've gotten the code to a place where it kinda works, I'd like to bring up a VNC session of my pi. Then I can make small changes and run tests very quickly without having to transfer files over and then run them. Would SSH be a better option for this? I'm not fixed on any one solution, just looking for something that works.

---

### Post by itaki on 2021-10-28
Thanks, yeah, this is the problem, it works with Raspbian, but not with Ubuntu.

---

### Post by itaki on 2021-10-28
I was afraid someone would say this. Now I'm off to figure out how to SSH properly. Though I just don't see how I can be actively editing a script on my mac and run it on the pi without copying it over every time I make one tiny little change.

---

### Post by itaki on 2021-10-28
You were right. An hour of playing around with VS Code Remote connect and I have truly seen a better way. Thanks

---

### Post by TheFu on 2021-10-28
> **itaki said:**
> I was afraid someone would say this. Now I'm off to figure out how to SSH properly. Though I just don't see how I can be actively editing a script on my mac and run it on the pi without copying it over every time I make one tiny little change.

vim supports remote editing over ssh via rsync URLs.  There are many different ways if you don't like that.  sshfs is one.
ssh is how Unix-like OSes are connected. Know it. Learn it. Love it.  ssh includes scp, sftp, rsync, sshfs and about 50 other tools.  They all use the same ssh-keys/certs and honor the same ~/.ssh/config file.  Master those last 2 things and you'll seldom want to bother with a GUI again.

You can use **ssh -X userid@remotePi  {some terminal command}** to have a remote terminal or most other programs displayed on any X/Server - which would normally be the workstation you sit behind. On the same LAN, VNC is a complete waste.  Over the internet, VNC/RDP are complete security failures.

---


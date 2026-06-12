---
title: "Screen doesn't refresh whatever remote desktop solution I use - (15.04)"
date: 2015-07-09
forum: General Help
---

### Post by Stephan_Tual on 2015-07-09
Regardless of the remote desktop solution chosen (baked in vnc, 3rd party vnc server, teamviewer), I end up with a screen that never refreshes on the client side. 
The remote ubuntu screen appears then never refreshes.

I'm using fglrx-updates on 15.04 and ATI radeon 290x. Everything is stock, ie, short of the remote desktop software I haven't installed anything yet (clean install). 

What's different about my configuration however is that I have 2 GPUs instead of a single on in the machine.

---

### Post by DexVitalitY on 2015-08-26
I also have the same issue, w/e program I use for remote desktop (right now I am using Team Viewer) the Desktop screen does not refresh... but the actions are being sent through.. anyone have any solution to this? I am using Ubuntu 15.04

---

### Post by mickyman550 on 2015-09-06
I am having the same problem. I can connect to the vnc server but the remote desktop screen remains frozen at the point when I first connected. I can close the client and reconnect and see that my actions were registered. The same thing happens with the built-in vnc server and Teamviewer server. This is a clean install of Ubuntu 15.04 with AMD fglrx graphics driver installed. Remote desktop worked fine for me on 14.10.

---

### Post by mickyman550 on 2015-09-20
This is now fixed for me. I do not know what the cause was. All I have done since my message above was update Ubuntu. I usually perform updates from the terminal like this:

sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y

If I have everything saved I will run this command:

sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get autoremove -y && sudo reboot

I would suggest try the above and see if it gets remote desktop working for you.

---


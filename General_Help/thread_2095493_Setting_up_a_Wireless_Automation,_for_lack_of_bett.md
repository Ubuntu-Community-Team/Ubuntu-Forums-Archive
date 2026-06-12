---
title: "Setting up a Wireless Automation, for lack of better phrasing"
date: 2012-12-17
forum: General Help
---

### Post by Shikiru on 2012-12-17
So I've run into an odd problem with my wireless while running Ubuntu 12.04 and I'm trying to set up a quick workaround until further notice. As it stands, my wireless is cutting out after a few minutes of being on without disconnecting or losing signal strength. When I try to ping my router I get a constant response, but from, say, Google I get a response for a bit then out of nowhere the ping shoots up to 1k ms and eventually dies, stating 'Destination Host Unreachable' until I reset the connection. This is a problem for a few posters I've found through Google, but I have not found a real answer, nor am I all that concerned about it any more.

          As it is, I don't have much time to deal with the issue and will be reinstalling 11.10 at a later date, but for now I need to get back to my school work without taking up all the time I have. My solution is to hotkey a script that runs the following so I can quickly reconnect to my network(wlan0)
> sudo ifconfig wlan0 down          For now I can either jot this into the terminal every 3-10 minutes or hit my wireless network to reset, but that is getting on my nerves. I know how to hotkey a program but how would I set this up considering it is a sudo command and would want my password? I'd prefer not to have it hop into root every time I need to be lazy.

          I appreciate you're time and if I can be helped, that would be amazing!

~Critter

---

### Post by CapnKirk on 2012-12-18
Perhaps you could run the script at your required intervals using cron?

---

### Post by dino99 on 2012-12-18
you surely might have some usefull warnings/errors logged to help you.

if you are having this issue with network-manager, then try wicd. Maybe googling around your hardware used, you could find some users workaround too.

---

### Post by grahammechanical on 2012-12-18
Are you sure it is the wireless adapter in the computer and not the router that is disconnecting from the ISP?

I have had both happen recently. Network Manager does not give a 'wireless disconnected' message if it is still communicating with the router. But the web browser would give a 'page not found' error message. This was happening to me and it was the router that had lost connection to my ISP.

Then the other day I got the 'wireless disconnected' message and the router was still connected to the ISP. I wondered if someone was trying to gain access to the router. As I was not using the internet I switched off the router.

Regards.

---


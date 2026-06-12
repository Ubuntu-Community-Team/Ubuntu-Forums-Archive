---
title: "Best way to implement webcam monitor server"
date: 2015-01-05
forum: General Help
---

### Post by argentum2f@gmail.com on 2015-01-05
I'm setting some webcam monitoring in our lab so we can keep an eye on experiments that run over the weekend, etc., and I'm trying to do it in the simplest, cheapest, and least proprietary way possible. I got some fairly cheap hd webcams, and using yawcam on the windows machines, already have something working. I would like a more centralized setup though.
What I envision would be something like this (if it's possible):
1) I set up multiple webcams connected to computers all over the lab.
2) On each computer I run some software to turn the webcam into an 'IP' or 'Network' Cam (Is this possible?)
3) On a central server running Ubuntu and motion, I configure motion to receive the inputs from all of the webcams setup throughout the lab, and display them on one unified webpage, either side by side or individually accessible through a menu.
4) To check on things, I just remote login to a lab computer (or use vpn) and direct my browser to the single webpage where I can view everything that's going on.
5) We may even put the page on a public IP so it is easier to monitor from home. Probably would want to put a password on it at that point though.

I'm an experienced linux user, and I can do some amount of scripting and programming, but I don't have experience with webservers or any kind of video streaming, and I don't have much time to invent my own solution, so I'm just looking for suggestions, confirmation of whether or not I can do what I've listed above, recommendations of other software that may be of interest, etc. 

TLDR;
Whats the easiest way to remotely monitor various types of webcams connected to various computers in a unified and simple way? (excluding subscription services and non-free proprietary software)
Can I use motion with inputs from usb cams connected to other computers running various platforms?

Motion: [URL="http://www.lavrsen.dk/foswiki/bin/view/Motion"]http://www.lavrsen.dk/foswiki/bin/view/Motion
[/URL]
EDIT: In the absence of any ideas here, does someone have a suggestion of where I might have better luck asking about something like this?

---


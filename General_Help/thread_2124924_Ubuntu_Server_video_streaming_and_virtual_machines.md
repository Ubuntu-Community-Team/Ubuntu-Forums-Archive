---
title: "Ubuntu Server video streaming and virtual machines"
date: 2013-03-12
forum: General Help
---

### Post by amlwwalker on 2013-03-12
Hi,
I have been looking at getting a server for a while now. I just really want one...
I use Linux at work about 20% of the time, so Im reasonably familiar.
This is what Im thinking, however bear in mind Ive not done this before, so please comment constructively on the areas that I have either misunderstood or got incredibly wrong! I have read quite a few blogs on line but nothing quite like what Im imagining:

Something about as powerful as this as the server:
[http://www.ebuyer.com/430446-proliant-microserver-turion-2-2-2gb-250gb-nhpl-sata-lff-in-704941-421](http://www.ebuyer.com/430446-proliant-microserver-turion-2-2-2gb-250gb-nhpl-sata-lff-in-704941-421)

I was going to up the ram to 8gb, and put a solid state harddrive in for OS's and use the 250gb as a storage facility.
it would be headless - the idea is that I can have very low powered pc's around the house that connect to the server and RDP into VM's.
Install hypervisor on it to manage VM's.
One VM - Ubuntu server. This will take care of any tasks I set it such as manage downloads etc etc. Whatever I want the server to do
Some of the tasks would be file management (organisation), and in future home automation.
Second VM Windows. Would like a few of these so other people can also RDP into the VM's
Possibly a Mac VM if its possible, as my little sister uses mac.

This is where Im not so sure: I want to set up a media center on it but be able to stream the media to any of the devices around the house. I was thinking an XBMC VM which could be RDP'd into. HyperVisor gives that VM access to the file systems that contain media and allows it to read/write to there so XBMC can add artwork etc. I could use XBMCUbuntu. but as far as Im aware the only difference is the GUI is XBMC thats all?
What Im not sure about is whether XBMC will decode the video (lets assume HD - Im on wired network) on the server, then try and stream it decoded, in a VM and all of that has to be passed to the client, or it will be passed as data and handled on the client side. Im worried about a) bandwidth, and b) power of the server.

How does streaming/VM's work? how powerful does the server have to be to do the above?
Could anyone recommend me client pc's that are cheap and would cope with the tasks allocated to it?
How many VM's do you think I could run simultaneously?
Could anyone recommend a better server for the job?

When in idle mode, the server will be doing things like downloading, organizing (backing up etc)...
i dont want the clients doing much at all, except seamless streaming of the VM's and watching movies/listening to music.
Also Will Internet browsing/watching stuff online be ok in a VM - I dont want jitter jatter....

Thanks guys

---


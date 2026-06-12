---
title: "Yet Another Dial-Up Failure"
date: 2004-11-26
forum: General Help
---

### Post by sembazuru on 2004-11-26
"Frankly the average computer user would have lost it simply trying to setup dialup. This must change for Ubuntu to make it in the real world of users."

I found that quote in the forums while searching for an answer to my problem, one that is, apparently, fairly common among new users.

I waited anxiously for my CD of Ubuntu to arrive. I had read so many exciting reviews and user comments I was eager to give it a try.

The installation was painless, though I noticed at one point that the display said no network connection was detected. I didn't know if that meant a cable internet connection or what, but was afraid it was not detecting my Zoom external serial port modem. 

After installation I found, like others, that I could not create a dial-up connection to my ISP. I knew enough to go to Computer>System Configuation>Networking. But when I ran the connection wizzard I noticed that when I got to the second page, the "forward" button was greyed out. It didn't work even after I had entered my dial up number. I had no idea what to do. I went back to the main network window and entered DNS numberrs and my host name (Earthlink), but nothing changed.

I looked under the Device Manager for the external modem,  but most of what's in there is Greek to me. 

I know next to nothing about command line. I installed apt-get and Synaptic on Fedora last week, and that's the extent of my command line experience. If there isn't an easy way to configure my modem, I think I will have to go back to Fedora and wait until Hoary is released and hope this problem is more manageable. 

I  came to Ubuntu because I thought it  was a non-bloated user friendly distro. Please don't flame me or tell me to just edit some config file.  I don't think the die-hards appreciate how difficult it is for the average, non-technical person to learn Linux and command line. Especailly when you're like me, starting from ZERO and having to go at it entirely self-taught.

---

### Post by Arnb on 2004-11-26
Hmm I've been "Warholed!" Andy Warhol said many years ago that in the future everyone would be famous for 15 minutes, well this is about 5 nanoseconds.

That said I could only get dialup working by making sure everything was set accordng to the settings found at [http://www.wurd.com/instcon_linux_wvdial.php](http://www.wurd.com/instcon_linux_wvdial.php)  athough you obviously must change the network id.  

Be sure to edit and verify the wvdial.conf file. ( I prefer gedit)  The Ubuntu GUI network interface uses wvdial.conf but does a poor job (IMHO) cleaning up when a dialup connection is modified or deleted. 

Yes this is all done via the command console.  To make it more interesting on one install attempt I did not have my dialup PCMCIA card installed so the wvdial.conf file did not exist. Like you I started from zero, it was not fun.

---

### Post by calamari on 2004-11-27
I installed Ubuntu yesterday.  After my dial-up adventures, I made a DialupModemHowto on the wiki.  It guides you through pppconfig, and also making a script and launcher icon for it (I didn't like gpppon very much).  

[DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

HTH,
Jeff

---


---
title: "Viewing Live TV using Kaffeine"
date: 2018-01-23
forum: General Help
---

### Post by neutronforrest on 2018-01-23
Dear Forum,

My older computer was running 14.04 and I had Kaffeine install in which I recorded live TV.  I was also able to view the live tv on the screen.  I have recently built a new computer and installed Ubuntu 16.04.  However, I am unable to view the live TV with the kaffeine program running.  It records the programs fine and I can view them using mini-dlna on my TV.  This leads me to think the codecs are not installed correctly.  I have searched and install the unrestricted files as suggested by others.  I am still not able to get the live TV on the computer.  My questions are:

1:  How do I check which codecs I have currently installed.
2:  Which ones are needed to view the live TV with the TV-tuner card (Hauppauge WinTV-HVR-1250 NSTC/ATSC/QAM Internal HDTV Card PCI-E x1 - OEM).

CJ

---

### Post by managerceo1 on 2018-01-23
In my opinion the best software  for watching TV is Kaffeine! It is installed by default in Kubuntu! 
Launch the terminal and enter the following. This will install Kaffeine and the necessary CODECS for You

sudo apt-get install kaffeine libxine1-ffmpeg

sudo usermod -G video -a tom

sudo modprobe em28xx
sudo modprobe cx88-dvb
sudo modprobe dvb-bt8xx

Hope it helps...

---

### Post by neutronforrest on 2018-01-23
Thanks for the reply.  I have already installed Kaffeine and it works great.  Could you please explain what each of the following does?  

How do I check if I libxine1-ffmpeg installed already?
What do the "usermod -G video -a tom" do?

Also,
What does,

sudo modprobe em28xx
sudo modprobe cx88-dvb
sudo modprobe dvb-bt8xx

do?

Sorry for the questions.  Just curious as to what these files actually do.

CJ

---


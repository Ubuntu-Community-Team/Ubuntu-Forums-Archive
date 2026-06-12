---
title: "PVR-150 Fails To Tune To Channel 3"
date: 2006-11-24
forum: General Help
---

### Post by wjston on 2006-11-24
I have recently built a new system using Ubuntu Edgy for my OS. It's main purpose is to serve as a pvr using MythTV 20. All-in-all, the install was relatively simple and I love the overhaul to both Edgy and MythTV. Initially, I had placed ivtv-tune -c 3 -d /dev/video0 into section 4 of MythTV setup (where an external channel change script goes). This is the only way I can get the Hauppauge PVR-150 to tune to channel 3 on boot. However, I purchased a MyBlaster to control my ExpressVu satellite receiver and I needed to remove the ivtv-tune script in order to control the satellite with an external channel change command. Consequently, it is necessary to type the ivtv-tune command into a terminal everytime there is a need to reboot the system.](*,) ](*,) 

I would appreciate any advise on where to place the ivtv-tune script so that it tunes my capture card on system restart. This is the only thing holding me up from putting the system into my entertainment centre. I really don't want to have to rely on a keyboard every time I shut down and restart. I have tried putting the script in rc.local and making the file executable but this did not work (maybe I did something wrong). Any help would be greatfully accepted.

Regards

---

### Post by wjston on 2006-11-26
A fine person with the user name anomie, over in the Linux Forums was able to resolve this issue for me:
  Log in as the mythtv user and then in a terminal -
   echo 'ivtv-tune -c 3 -d /dev/video0' >> ~/.profile 
On login to mythfrontend, this command will automatically be run this time and consecutive future logins. 

Worked for me in Ubuntu Edgy 6.10 and I am off to enjoy my MythBuntu entertainment system.

Regards

---


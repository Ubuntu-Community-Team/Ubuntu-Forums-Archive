---
title: "Resuming from Hibernate Sometimes results in a Black Screen of Death"
date: 2015-05-27
forum: General Help
---

### Post by alikazmi-2040 on 2015-05-27
Hello Everyone,

The system hibernates successfully every time (there are no errors/failures/faults in /var/log/pm-suspend.log) and usually it resumes successfully as well but when it fails, the system goes completely unresponsive with the 'Caps Lock' key not lighting up when pressed and Ctrl+Alt+F1 (etc) not doing anything. Also, the resume from hibernate only fails if the system has been hibernated for over 6 hours, I can resume the system from hibernation every time if it has been hibernated for only 2/3 hours or less. The failure occurs after the image has been loaded from the swap partition (can I find out if there were any issues with loading the image from the swap partition, like for instance if the image was corrupt of if there were any other issues?).

I am on a fully up-to-date Kubuntu 15.04 installation. My system has an Intel i7-4700qm processor, dual Nvidia geforce gt-740m and Intel 4600M GPUs, 8GB of RAM, a 16GB  swap partition and a dual monitor setup (1366x768 and 1440x900). I have tried using Nouveau display drivers and Nvidia binary drivers 346.59 (with the Prime profile set to the Intel card and the Nvidia card) and every thing results in the same outcome (black screen of death on resume if system has been hibernated too long).

There don't seem to be any hardware defects (as far as I can tell) and since the problem occurs only under very specific conditions, I can't reproduce it deliberately to test out various solutions (despite the fact that it reproduces itself on a daily basis) :confused::?:-s](*,).

I am unsure how to debug the problem and find what the culprit is, any help/guidance will be greatly appreciated [-o

---

### Post by hnr2k6 on 2015-05-30
Wow! Same problem for me. I have a Lenovo T450s/intel 5500/i7-5700. Hibernates work fine if resumed within a few hours. All durations for longer hours like the OP mentions have resulted in a black screen. 

On a correct wakeup, I see the thawing process. 

Sat May 30 10:38:27 PDT 2015: performing hibernate
Sat May 30 10:39:45 PDT 2015: Awake.
Sat May 30 10:39:45 PDT 2015: Running hooks for thaw

On a failure,  the last line is just "performing hibernate". The splash  screen shows resuming from swap partition, but after that nothing. Only a  cold boot brings it back up. I wonder if there is data in the memory which remains for a few hours, but goes away and creates a bug when it wakes up after a longer time. I have to try leaving it on charge during the hibernating phase to see if that keeps the memory "refreshed".

---

### Post by leunam12 on 2015-05-30
Try a different video driver. System Settings> Software and Updates go to the last tab on the right "Additional Drivers" and see if there are other drivers.

---

### Post by hnr2k6 on 2015-05-30
No other drivers for the intel 5500. I wonder if there is some 'clock' that runs into a bug when resuming after 'X' hours. The OP has a graphics card. Different hardware but the same issue.

---

### Post by kuddel-mail on 2015-06-05
I've had similar experiences with a Thinkpad X1 Carbon 3rd (core i7-5500u Intel HD5500 Graphics). 
Sometimes hibernate works. Sometimes not. I can try it several times and it succeeds. Thereafter not. And almost always when i try it the next day (after some hours in hibernation) it fails. Screen is blank or shows a Console cursor that stops blinking (depending on the kernel). The system is completely frozen. Unfortunately nothing can be found in the logs

---

### Post by ddurdle on 2016-05-20
I have the same problem as everyone else, but I'm on Debian.  So the problem is more far-reaching.  Very frustrating.  Has been occurring on my Carbon X1 2014 on kernel 3.16 and 4.5 (haven't tried any other kernels recently).

---

### Post by ddurdle on 2016-06-04
This issue is probably more likely related to this - [https://bugzilla.kernel.org/show_bug.cgi?id=104771](https://bugzilla.kernel.org/show_bug.cgi?id=104771)

---

### Post by oldos2er on 2016-06-04
Old thread closed.

Debian's support forums are [here]("http://forums.debian.net/").

---


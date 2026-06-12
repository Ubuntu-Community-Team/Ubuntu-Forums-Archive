---
title: "AMD Legacy Drivers in Ubuntu 13.04?"
date: 2013-04-13
forum: General Help
---

### Post by mclark87 on 2013-04-13
Are the Legacy drivers from AMD going to be able to be installed in the new 13.04 version of Ubuntu? I searched but was unable to find an answer. I currently have 12.1 and while the open source driver works OK I would like to resolve the sleep/boot issue and maybe get my fps up to a reasonable level on the only game I play on my laptop, World of Tanks. If not, I guess I should look into downgrading to 12.04.

---

### Post by 3rdalbum on 2013-04-13
No, you can't use old graphics drivers on a new version of X. ATI's legacy drivers will never work with anything newer than 12.04. Sorry.

---

### Post by mclark87 on 2013-04-13
OK. I was hoping that something had been worked out for 13.04. Guess I'll do a clean install of 12.04 so I can use AMDs driver.

---

### Post by elliotn on 2013-04-14
install liquorix kernel

---

### Post by Scoobin on 2013-05-13
I'm in the same boat. Does this liquorix kernel get legacy ATI cards to work with 13.04?

---

### Post by ephryn on 2013-05-29
NEVER say NEVER. I love Linux, as we have heard we are not able to install AMD's legacy drivers past 12.04, I've found that this is not true, xserver needs to be downgraded to 1.12 before you are able to install the legacy drivers, I found directions on [dotTech]("http://dottech.org/105987/how-to-install-amd-13-1-legacy-drivers-on-ubuntu-13-04-guide/"), I had some issues with the directions but I think that has to do with me. Also you may want to look into liquorix kernel like previously mentioned.I hope this helps some one.

I have a HP Pavilion DV7-1245DX which comes with an ATI Mobility Radeon HD 3200.

---

### Post by Mark Phelps on 2013-05-29
I join others who advise AGAINST doing this sort of X-server downgrade just to restricted drivers installed.  

You are asking for problems down the road if you do this.

---

### Post by Scoobin on 2013-05-29
> **ephryn said:**
> NEVER say NEVER. I love Linux, as we have heard we are not able to install AMD's legacy drivers past 12.04, I've found that this is not true, xserver needs to be downgraded to 1.12 before you are able to install the legacy drivers, I found directions on [dotTech]("http://dottech.org/105987/how-to-install-amd-13-1-legacy-drivers-on-ubuntu-13-04-guide/"), I had some issues with the directions but I think that has to do with me. Also you may want to look into liquorix kernel like previously mentioned.I hope this helps some one.

I have a HP Pavilion DV7-1245DX which comes with an ATI Mobility Radeon HD 3200.
I used this method with my HP Compaq 8510p (Mobility HD 2600), and it worked quite nicely until the Legacy x-server PPA was updated and then it rendered Unity useless (I could login but Unity couldn't load). This meant doing a fresh reinstall of 12.04 LTS. I couldn't even use 12.04.2 because it used the 3.5 kernel. And I had to create a new user because the upgrade had modified my /home settings meaning a broken system if used with 12.04 install.

So personally I think a PPA is the wrong way to go about it. An update which I was hoping would fix the loud fan issue was actually the thing that broke it.

---

### Post by Mark Phelps on 2013-05-29
> **Scoobin said:**
> I used this method with my HP Compaq 8510p (Mobility HD 2600), and it worked quite nicely until the Legacy x-server PPA was updated and then it rendered Unity useless (I could login but Unity couldn't load). This meant doing a fresh reinstall of 12.04 LTS. I couldn't even use 12.04.2 because it used the 3.5 kernel. And I had to create a new user because the upgrade had modified my /home settings meaning a broken system if used with 12.04 install.

So personally I think a PPA is the wrong way to go about it. An update which I was hoping would fix the loud fan issue was actually the thing that broke it.

Thank you for posting your experience with this.

This is a good example of my warning about > ... problems down the road if you do this.

---

### Post by QIII on 2013-05-29
This

---

### Post by Cheesemill on 2013-05-29
+1

Don't do it.

---

### Post by QIII on 2013-05-29
How long have I been saying just this?

---

### Post by The Squig on 2013-05-29
hi, just thought i would chip in with my own experiance regarding the legacy drivers. I recently setup my old computer as a htpc running ubuntu 13.04 and using a radeon hd4850 graphics card for video out. I used the downgrade script to get the closed legacy drivers to install and it worked alright.. until i performed a system update which broke the driver. Annoyed, I ended up removing it and installing the free drivers which worked a lot better then i thought they would. 1080p video playback was no problem so unless you need the extra 3d performance id recommend you to try them out first, its nice not having to use a hack to get the drivers running. 

all in all though not having the legacy drivers support new distro's is beyond annoying and if the open driver hadnt worked as well as it did i would have been seriously crossed.

---

### Post by Scoobin on 2013-05-30
Fair enough if you have a high-end card. I couldn't get the Open Source drivers to work on my system with Unity.  I guess I will avoid Radeon like the plague in future.

---

### Post by mastablasta on 2013-05-30
> **Scoobin said:**
> Fair enough if you have a high-end card. I couldn't get the Open Source drivers to work on my system with Unity. I guess I will avoid Radeon like the plague in future.

nvidia is not that much better on notebooks. and also elsewhere. proprietary drivers cause issues in linux that's the bottom line.

i mean ubuntu could also choose to support older x server, only security patching old kernels... but it doens't. it expects the manufacturers to do the work and constantly update drivers. 

my AMD card moved into legacy on windows systems as well (in beginning of this year). only i have no problem there with old XP. not sure what would happen if i tried windows 7. anyway i have latest version of programmes on that OS. and it works on that mashicne. if i wanted ubuntu i would have to go with 12.04.

---


---
title: "(RESOLVED) Ubuntu does not start anymore, please help !!"
date: 2017-05-30
forum: General Help
---

### Post by rob141 on 2017-05-30
Yesterday when i came home after work, i knowdess that there had been a power outtage in my block because my microwave and oven clock where flashing but my laptop was still on.  I always or most of the time leave it on. 

So when i rebooted my ubuntu, i could not login again and before the login screen, there is a black screen with only this that show:  /dev/sda6 clean numbeers/numbers files numbers/numbers blocks    

then i get to the login screen. When i try to login, it look like it will work but then i fall back into the login windows and i have to login again and it just goes round and round like that. I cannot open my session at all.

i wrote numbers/numbers because it actually were numbers but i did not write then down but it appears as i put it here.

The only thing i manage to do was to open ubuntu in the recovery mode in command prompt and then i did a df -h  to know what was the /dev/sda6  and it is my root folder.

So since i am able to get in the recovery mode, is there anyone that can help me please to solve that problem ??   

Thank you very much in advance.

---

### Post by #&amp;thj^% on 2017-05-30
Are you using Nvidia drivers?
And also see if you can get to a TTY session and and run:
```
sudo apt update
sudo apt upgrade
```
If there are Errors, Please try to paste back here.

---

### Post by rob141 on 2017-05-30
> **1fallen said:**
> Are you using Nvidia drivers?
And also see if you can get to a TTY session and and run:
```
sudo apt update
sudo apt upgrade
```
If there are Errors, Please try to paste back here.


No i dont have Nvidia on my laptop, i have ATI so it is fglrx drivers but the problem is not the image, it is the session that i cant get into.

I will try to do a update then upgrade as soon as i can and let you know if that helped or not.

Thx.

---

### Post by #&amp;thj^% on 2017-05-30
> **rob141 said:**
> No i dont have Nvidia on my laptop, i have ATI so it is fglrx drivers but the problem is not the image, it is the session that i cant get into.

I will try to do a update then upgrade as soon as i can and let you know if that helped or not.

Thx.

Login Loops can be caused by Video Drivers!
 See this: [https://askubuntu.com/questions/793885/fglrx-driver-causing-login-loop-radeon-hd-6470m-ubuntu-14-04](https://askubuntu.com/questions/793885/fglrx-driver-causing-login-loop-radeon-hd-6470m-ubuntu-14-04)
 And this: [https://askubuntu.com/questions/625271/ubuntu-15-04-login-loop](https://askubuntu.com/questions/625271/ubuntu-15-04-login-loop)
 And more if you need....and I'm **not** saying that this is for sure your problem...but keep it in your back pocket for trouble shooting. ;)

I will wait for you to see if this gets sorted out with updates. 
If needed you can remove these drivers by booting into recovery mode and running:

       
```

    sudo apt-get purge fglrx 
```

---

### Post by rob141 on 2017-05-30
> **1fallen said:**
> Login Loops can be caused by Video Drivers!
 See this: [https://askubuntu.com/questions/793885/fglrx-driver-causing-login-loop-radeon-hd-6470m-ubuntu-14-04](https://askubuntu.com/questions/793885/fglrx-driver-causing-login-loop-radeon-hd-6470m-ubuntu-14-04)
 And this: [https://askubuntu.com/questions/625271/ubuntu-15-04-login-loop](https://askubuntu.com/questions/625271/ubuntu-15-04-login-loop)
 And more if you need....and I'm **not** saying that this is for sure your problem...but keep it in your back pocket for trouble shooting. ;)

I will wait for you to see if this gets sorted out with updates. 
If needed you can remove these drivers by booting into recovery mode and running:

       
```

    sudo apt-get purge fglrx 
```


Thank you very much, i will try that if update and upgrade does not solve the problem.

---

### Post by rob141 on 2017-05-30
Hi, i have tryed all these and nothing work because it seem that my hdd does not get mounted somehow.

I have started with the ubuntu 15.10 live cd and i still can see my internal hdd and browse in it with the live cd but when i start it does not. 

I have tryed also the upstair boot and this is where it is telling me that the /mnt/usb  wdc numbers   is not ready yet or not present

I am not sure it is exactly wdc but it was surely wd something as i can recall and i know it is my internal laptop hdd as it is a western digital.

Is there anything i could do beside re-installing ubuntu 15.10 with the live cd the upgrade to the latest ubuntu by doing a dist-upgrade ??

the errors in the recovery mode where mostly about unable to fetch something even when i connected it with the network cable. 

I even had some error trying to do the 
sudo apt-get purge fglrx

as of now the only thing i can do is to boot live cd of ubuntu 15.10 or go in the recovery mode but i am not sure i can do much in the recovery mode since it does not seem to mount the internal hdd !!!

the one i have installed was originaly ubuntu 15.10 but i had done a dist-upgrade when it came out so i think i still were not the the newly or latest ubuntu because i have not done a dist-upgrade for a long time

---

### Post by #&amp;thj^% on 2017-05-31
Well my friend...this is obviously not good. :(
Power outages with a system still up can be a problem to diagnose.
And with out exact error messages, well we are just guessing now.
Power surges can be very hard on harddrives/psu's/gpu's/cpu's.
Or even possibly caught in the middle of installing updates.
Corrupting the OS.
If you have access to another computer, you can download a properly supported version of Ubuntu (IE:14.04 16.04 or even 17.04)  

The errors you were seeing...(about unable to fetch something)
is due to the fact that 15.10 is no longer supported...so nothing to find.
If you do this method with a proper version, try to pull the data you need off first with the Live installer.
One method is found here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And if needed another way here: [https://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/](https://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/)

---

### Post by rob141 on 2017-05-31
> **1fallen said:**
> Well my friend...this is obviously not good. :(
Power outages with a system still up can be a problem to diagnose.
And with out exact error messages, well we are just guessing now.
Power surges can be very hard on harddrives/psu's/gpu's/cpu's.
Or even possibly caught in the middle of installing updates.
Corrupting the OS.
If you have access to another computer, you can download a properly supported version of Ubuntu (IE:14.04 16.04 or even 17.04)  

The errors you were seeing...(about unable to fetch something)
is due to the fact that 15.10 is no longer supported...so nothing to find.
If you do this method with a proper version, try to pull the data you need off first with the Live installer.
One method is found here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And if needed another way here: [https://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/](https://www.howtogeek.com/howto/17044/move-files-from-a-failing-pc-with-an-ubuntu-live-cd/)

Thank you and yes i know and i was affraid of that when i got home and discovered there had been a power outtage  :(

Now i am up for an new installation of ubuntu 17.04.  I guest it may be the best solution, a fresh start. 

I will now make this post as resolved but it will be after i install the new version of ubuntu.

Thank you very much for all your help, it is very appreciated ;)

---

### Post by #&amp;thj^% on 2017-05-31
I'm not sure how much help I was...but thanks for the kind words..:D
Best Regards

---

### Post by rob141 on 2017-05-31
> **1fallen said:**
> I'm not sure how much help I was...but thanks for the kind words..:D
Best Regards


there is 1 more thing i would like to be sure. As i want to istall ubuntu 17.04 i am at the instalation type part and i i select erase disc and install or whatever i am choosing, the install now button stay greyed out :(   

does this mean my hdd is really dead ?

---

### Post by mörgæs on 2017-06-01
> **rob141 said:**
> 
I will now make this post as resolved but it will be after i install the new version of ubuntu.


Good, please use Thread Tools for that (when you consider it solved).

Could you post a screen shot showing the install problem?

---

### Post by rob141 on 2017-06-01
After all, it is all fine, i clicked once the button back then next again then i could install it.  So now everything seem to be fine   ;)

---


---
title: "Xauthority question"
date: 2015-04-29
forum: General Help
---

### Post by free10 on 2015-04-29
I crashed my 14.04 Ubuntu drive while trying to get a Sega Saturn game emulator working and had to kill the computer to reboot, and then on reboot instead of automatically logging me in it to me to the login screen, and of course it did not recognise my password.

Well digging around looking for how to get back in and reading a lot of post here or on the net Xauthority was sometimes blamed. So I booted into the 14.04 live DVD, so I could take a look over at the files on the hard drive for Xauthority, and found not one but two.

The first and seemingly suppose to be there file

/media/ubuntu/ef703578-a140-47b2-a44f-809e167e0e47/home/toyforce/.Xauthority

And also this one. 

/media/ubuntu/ef703578-a140-47b2-a44f-809e167e0e47/home/toyforce/.Xauthority.2NJPDX 

I am the only user on this computer and use automatically login normally anyway on reboot.  I have no reason to establish a second user and no one here has even used it, but me. I live alone and people that have come over have not gotten on it. So I was wondering if the .Xauthority.2NJPDX file is suppose to be there too, or if it represents an outside entry??

Thanks if anyone knows or has a good guess.

---

### Post by Bucky Ball on 2015-04-29
*Thread moved to **General Help**.*

Boot Ubuntu to the login screen (or choose 'Recovery kernel' at boot and drop to a shell as root when you get to the options screen). If you are at the login screen, hit Ctl+alt+F1. You should end up at a CLI (a big terminal) whichever way you do it.

Login (if using the ctl+alt+F1 method) and then type these three commands, one after the other, with return between. It will remove X and ICEauthority and reboot the machine (close all open apps before dropping to the CLI is best):

> sudo rm .Xauthority.*
sudo rm .ICEauthority.*
sudo reboot -h now


Can you log in now? If you have problems removing .ICEauthority, try .iceauthority. I'm pretty sure it is with the caps, though. A new Xauthority and ICEauthority will be generated on reboot.

If all this fails, try [this]("http://ubuntuforums.org/showthread.php?t=949750&p=5977334&viewfull=1#post5977334"), replacing 'jake' with your user name.

---

### Post by free10 on 2015-04-29
OK thanks, I will try that, though don't know where that Jake came from LOL I am on my 13.10 drive at the moment doing a download and have a headache right now for some reason. But thanks again

---

### Post by Bucky Ball on 2015-04-29
13.10??? Not supported any longer. Consider upgrading to a supported release, LTS releases for five years support, nine months for anything else. 

We can't give you a lot of help with an EOL release and it also gets no security updates so I'd avoid being online with it. 13.10 is also no longer supported by Canonical, but, of course, it is entirely up to you which release you choose to use. Just remember, support won't be the greatest (although there is still a lot of pages on the web regarding 13.10). You can probably expect more headaches with 13.10 as it gets older and further away from when it went EOL without updates, then again, if it's not online, you could possibly run it forever without much issue! Good luck. ;)

PS: 'jake' came from the example to fix your problem on the page I linked to in my last post.

---

### Post by free10 on 2015-04-29
OK thanks. Normally I was on 14.04, but incase of failure of it and to have additional space for storage I havre the 13.10 drive. While 13.10 is not supported, it also does not eat up my 4gig of memory when I am using it like 14.04 does, so I haven't upgraded the 13.10 drive. I am also not real paranoid on the security side and I don't do windoz LOL

I have to admit though when I could get login and then saw what looked like the strange titled "/.Xauthority.2NJPDX" file what was going on, but that was on the 14.04 drive. Thanks again.
 

.

---

### Post by Bucky Ball on 2015-04-29
Wow, there seems to be a problem big time if 14.04 LTS is eating up 4Gb of RAM! If this is a only just installed, untweaked or customised (or is easy to get back into that state) it might be worth going again if that is the case and seeing if this time it doesn't do that.

On a normal boot is 14.04 showing that it is chewing through all the RAM idle or when using apps? What's /swap doing?

Run 'htop' in a terminal (or 'top') and find out. See the screen shot for mine. ;)

---

### Post by free10 on 2015-04-29
It is when using apps and pretty much since install.  I monitor it all using "system monitor" and once around 80-90% and over it is getting pretty slow and buggy. Swap is being hardly used untill very late. I noticed others had this problem too and have changed swapiness and some other values, and it did help but still it uses it faster than my 13.10 does. And way faster than earlier versions of Ubuntu.

I am usually using Vuze, Firefox, and Thunderbird and have those going, along with Pidgin and system monitor, plus Psensor.  I may be more spoiled/sensitive than most, because when I was running BeOS R5 with only 256mb or 512mb of ram I would stay up and running for months, and never have to reboot with constant use. It was designed for optimum operation when using only 125mb of ram.  Video cards then were only 4-8mb, no cache on hard drives, and little cache on the CPUs. Most reboots were caused by hardware swaps or power failures, and from the time of hitting reboot, to back on the Desktop was under one minute, with an old slow single 10gig hard drive, and single 566mhz CPU, and that was a full reboot.

I was spoiled LOL Thanks again. Later today I will see if I can get rid of that login problem.

---

### Post by free10 on 2015-05-01
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

Boot Ubuntu to the login screen (or choose 'Recovery kernel' at boot and drop to a shell as root when you get to the options screen). If you are at the login screen, hit Ctl+alt+F1. You should end up at a CLI (a big terminal) whichever way you do it.

Login (if using the ctl+alt+F1 method) and then type these three commands, one after the other, with return between. It will remove X and ICEauthority and reboot the machine (close all open apps before dropping to the CLI is best):



Can you log in now? If you have problems removing .ICEauthority, try .iceauthority. I'm pretty sure it is with the caps, though. A new Xauthority and ICEauthority will be generated on reboot.

If all this fails, try [this]("http://ubuntuforums.org/showthread.php?t=949750&p=5977334&viewfull=1#post5977334"), replacing 'jake' with your user name.

Well finally got around to trying your commands and it kept saying files not found. Did not try the page you linked commands yet, but will.  I did try some commands to see if my home folder was found and it was, and then did the command to change passwd. I tried tp just reuse my old passwd but it said it was not allowed as it was the same one, so it knows its my password. Like I said said I will try thecommands used on your link and if that doesn't work keep trying different things. Thanks

---


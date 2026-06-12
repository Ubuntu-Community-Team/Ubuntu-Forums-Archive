---
title: "Hardy Big Big problem"
date: 2008-04-24
forum: General Help
---

### Post by sajuukkhar on 2008-04-24
Hey guys, im a bit nooby so bear with me...

Updated from Dapper to Hardy (RC) through software update.  It then told me to restart and my xorg file then had troubles.  It said it couldnt find drivers for my "mouse" and my "wacom" 

I have tried deleting it, didnt work
I have reconfigured it, didnt work

Then a guy came in and helped me, and said to do apt-get update followed by apt-get dist-install.  Waited 5 hours for 500mb to download.  

It downloads yadayada.  

Sudo apt-get install ubuntu-desktop : dependency errors occur, X informs me to run Sudo apt-get install -f to fix them

I do that and get an error in my /var/cache/apt/archives/xkb-data_1.1~cvs.20080104.1-1ubuntu6_all.deb
error 2: Sub-process /usr/bin/dpkg returned an error code (1)

i also get warnings from perl that setting locale failed and it wants me to check that my Language, LC all and Lang are supported and installed.  It then says to Standard Locale and LC_ALL cannot be set to a default locale because there is no such file/directory.

---

### Post by kgr132 on 2008-04-24
I hate to say it, but when my last upgrade from one major version to another failed miserably, the easiest and least painful out of it was to do a clean install of the latest Ubuntu release. If you back up your home folder, the profiles for most of your apps should restore OK when you copy the stuff from your old home folder to your new one. When saving the stuff from your old home folder, be sure to enable viewing the hidden files in the file browser and take a look at saving the hidden folders for your apps like Firefox, Thunderbird, etc. Overwriting any default folders in the home folder of the new install with the ones you saved will put things back the way you had them for a lot of the apps. Your Firefox plug-ins will even migrate fully functional this way, except for any that are deemed incompatible with the new Firefox 3.0 that comes with Hardy. Best of luck.

---

### Post by grannyw on 2008-04-24
i would say that you rather wait a bit,cause everyone is trying to update now and the server just goes wild

---

### Post by sajuukkhar on 2008-04-25
What I will do is this, im downloading Hardy (6 hours of dling) iso and while i wait i will just move my data over through either my Ipod or something.  Question, how do i disconnect my Ipod from Linux command line?  

Then I will just reformat and install hardy.  Sounds good?  My pivate settings dont really matter. One of the guys from Launchpad though want me to email through the log files from my first attempt at doign the dist upgrade with dapper and i have forgotten it where it is, i think it might be in var/#### 

Other than that i am set :)
I think

---

### Post by estanton on 2008-04-25
would umount /dev/sda1 or whatever your ipod is do the trick? my iPod is in the car and I've never unmounted it from the command line but I would imagine that would do it

---

### Post by sajuukkhar on 2008-04-25
This is funny, I had my ipod connected in and started up the laptop

Somehow the BIOS started to boot from that although i have no settings to allow that and then it shuts down and then my Ipod disconnects anyway :)

---

### Post by sajuukkhar on 2008-04-25
Accuse me of double posting, you are right but something VERY interesting has happened (suspense): GNOME has started working again.  But mouse and synaptic pad does not work and my wacom doesnt work either.  Keyboard is responsive.  This might be a good thing.  Dunno how to fix mouse and synaptic pad (Synpad is my laptop mouse)

---

### Post by natrixgli on 2008-04-25
I have an idea...

Smash the mouse, wacom, and touchpad with a hammer and throw them away. Then, switch to a simpler window manager, such as **awesome** and never touch a mouse again.

Um, or not....

Just a lil' comic relief. My guess is xorg.conf is buggered up, but I agree with the above poster - I would back up important stuff and install fresh from CD.

Cheers,

-n8

---

### Post by estanton on 2008-04-25
also it never hurts to have a CD sitting around. It seems like alot of people have to use one eventually, I know I do when I break the system from messing around without really knowing what I'm doing.

---

### Post by sajuukkhar on 2008-04-25
Whence why I am downloading a Hardy ISO and i will burn that :)  

Awesome soudns cool, i rather stick to my command line, since i been spending the past 2 weekends on seperate problems.  

I think it was my fault for screwing up the xorg file.  Tryign to install the wacom.  Failed.  Epically.  That was last weekend.  Moral of story: Dont install Wacoms on Dapper Drakes?

200 mb to go til i have that cd or 2.5 hours

---

### Post by sajuukkhar on 2008-04-25
Xorg file of my laptop, remember my mouse dont work but my keyboard does.  Wacom also doesnt work.  its in open office format, sorry guys, best i could do with my tab key.

Take a look and puke.

Edit: Extra Puke material, my xorg log

---

### Post by sajuukkhar on 2008-04-25
Problem solved.  Reformat done and I now have hardy heron.  2 days of hard hard hard work done.  I want to thank you guys here and the fellas on IRC #ubuntu on freenode for the help you guys gave.  Couldnt have done it without you.

---

### Post by lonniehenry on 2008-04-25
sajuukkhar please mark solved so others with similar problem will know what worked. Thanks

---


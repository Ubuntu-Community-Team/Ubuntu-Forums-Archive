---
title: "splash screen (how do i install a diff one?)"
date: 2006-10-30
forum: General Help
---

### Post by Lax101 on 2006-10-30
Its me again How do i install a new splash screen on ubuntu edgy.  I knwo how to install new themes but now i wanna install a different splash screen.  How do i go about that?

---

### Post by autocrosser on 2006-10-30
Which one do you want--Grub Splash--Boot-splash--login splash(GDM) or Session splash?  With the right stuff you can change all of these---8)

---

### Post by Lax101 on 2006-10-30
well since u put it that way why not both. i'am pretty new at this so i mind as well learn how to do both. The help would be greatly appreciated.

---

### Post by autocrosser on 2006-10-30
Well--That's four different choices--Let's start with Grub--

Grub--Grand Unified Bootloader
You need to see a image you want to add--I goto [http://www.gnome-look.org/](http://www.gnome-look.org/) and look at what is there--you should also cruise the site  (look at the art forum) and see what Ubuntu people have created--

You found a grub image you want to use--COOL! Next--goto Menu>Accessories>Terminal & open one
Next-type in  sudo gedit /boot/grub/menu.lst  & hit return
you will be asked for your password & Gedit will open.

Then, scroll down to  ## ## End Default Options ##

And add in the next line--   splashimage=(hd0,1)/boot/grub/splash.xpm.gz

And to make sure--pull up your /boot/grub/menu.lst and look at the first kernel line--that will tell you if hd 0,1 is right or if you need to change it--any probs--just copy your menu.lst & post it (you will need to copy it to your desktop & rename it by adding .txt to the end--the forums don't allow uplaoding of some filetypes)


 Save the file and close the app.

If you look in my post--you will see splash.xpm.gz
Download it  (it should goto your desktop) and in the terminal--
sudo cp ~/Desktop/splash.xpm.gz /boot/grub   and hit return
Your will now have a grub Splash of Tux looking at you!!

If you are still with me--goto the GDM splash--This is easier--Goto Menu>System>Administration>Login Window

It will ask for your password & then the first window is "LocaL"

look to the side & see +ADD--click on it after you have got some GDM themes from Gnome-Look.org--add as you want;)

Next--Login Splash--Goto Menu>System>Administration>Synaptic & Search for gnome-splashscreen-manager (if you don't find it, you will need to enable the "extra" repositories--ask if this is a Prob)--download/install it & then use it to get wallpapers/splashscreens/icons--GREAT little app!

Last one--the Boot Splash--you will need to follow a guide to install Usplash-Switcher, but it is well worth it!! If you are game to install the switcher--search for it & ask me--

Welcome to the Ubuntu-World8)

---

### Post by prs444 on 2006-11-06
autocrosser,
I tried to do your little Grub splash Tux but for some reason it won't work.
I get a error that it can't find the image splashimage=(hd0,1)/boot/grub/splash.xpm.gz
I run a dual boot Win XP Ubuntu setup but when I installed Dapper Drake I accidently left the partitions for the last version of Ubuntu in place. so I have both versions installed. I think the =(hd0,1) part may be the problem since I have a goofed up setup. How can I check to see if this is correct and if it isn't how do I find the correct entry?
Any help would be great. 
I would like the Tux splash image as it spices up the boot proccess when people at work are noticing my "LINUX" laptop boot.  ](*,)

---

### Post by autocrosser on 2006-11-06
Sorry--I forgot to: sudo cp <where you put the image>/splash.xpm.gz /boot/grub

Let's say you downloaded it to your desktop--that would be: sudo cp /home/<your account>/Desktop/splash.xpm.gz /boot/grub

cp is the Linux "copy file" command--so you are just using root permissions to copy the file from your desktop to the directory /boot/grub

That will get Tux lookin' at you!!!;)

And to make sure--pull up your /boot/grub/menu.lst and look at the first kernel line--that will tell you if hd 0,1 is right or if you need to change it--any probs--just copy your menu.lst & post it (you will need to copy it to your desktop & rename it by adding .txt to the end--the forums don't allow uplaoding of some filetypes)

---

### Post by prs444 on 2006-11-06
autocrosser,
Thanks for the help! I got it working! Looks cool! Tux looks great on my Grub boot screen!\\:D/ \\:D/
Don't forget to add the help into the instructions at the top post, us noobs
are notorious for not reading all the way down a thread.
Thanks again!

---

### Post by autocrosser on 2006-11-06
Just out of curiosity--was it hd0,2 or hd1,0?  Glad you like it--I got it from another poster--aysiu   I'd also look at gnome-look.org--you can find all kinds for art--from Splash screens to wallpaper there--all for the linux in you;)

I also edited my upper post to make it clear--thanks for the note!!

---

### Post by prs444 on 2006-11-07
autocrosser,
it was hd0,5 I guess due to the old version breezy version still on the hard drive. 
I would love to have a walk through for the Usplash-Switcher. 
I'm starting to have an impressive looking Linux system. I have Tux in my Grub Boot Loader, And I have a killer Login Screen that matches my desktop background. I found a matching splash screen for the loading screen & background but I have no clue how to install or use Usplash.
Thanks again for your help! I can't wait to see what Usplash can do!

---

### Post by autocrosser on 2006-11-07
Do a forum search for usplash-switcher--there was a bit of buzz about it couple of weeks before Edgy's release & I haven't heard much after--I need to see if there is a update---so I'm on the look after I post this;)---I'll keep it posted---

---

### Post by autocrosser on 2006-11-07
OK--I found the post that had a .deb for usplash-swicher---use GDebi to install it:  
[http://www.ubuntuforums.org/showthread.php?t=278301&highlight=usplash-switcher](http://www.ubuntuforums.org/showthread.php?t=278301&highlight=usplash-switcher)

If you don't have GDebi--make sure you have all the repositories enabled  & search for it in Synaptic....

AW-rats--I forgot that this only works with Edgy---needs the updated GTK2.10 libraries---sorry to get your hopes up....In any case--I remember reading that someone ported the Edgy usplash to Dapper--Nice black theme--I'd track it down if you are interested---

---

### Post by autocrosser on 2006-11-07
Take a look at this: [http://www.ubuntuforums.org/showthread.php?t=264883&highlight=usplash](http://www.ubuntuforums.org/showthread.php?t=264883&highlight=usplash)

for Dapper--

---


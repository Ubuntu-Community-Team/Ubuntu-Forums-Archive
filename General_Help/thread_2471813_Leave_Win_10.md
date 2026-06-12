---
title: "Leave Win 10"
date: 2022-02-10
forum: General Help
---

### Post by newboy19 on 2022-02-10
I have 10 year old Lenovo laptop which is not suitable to take Win 11 as i am only a general user on the net for shopping.utube.searching. banking etc i dont play games or need a office programs so i thought i would ditch Windows and try a chromebook or Linux i have Ubuntu 18-04-6 lts on a on  a old Toshiba satellite L300 laptop which i have had a bit of practice on to see how i get on i have Firefox on it and all is well but i wanted to get iplayer and tv channels but this were i have a problem i looked up how to get iplayer but cant see how to open the terminal if i click as recommended Ctrl+Alt+T the mouse and trackpad freezes  and i cant do nothing the issue on tv channels is i have clicked the DRM but nothing will play also on BBC news site the news clips wont play but on utube and facebook it all works fine, The Toshiba  has 1.8 Mem. 245 GB that is the only OS on there my idea is if i can master the use of Linux of it i can get the latest Ubuntu on my Lenovo laptap and forget Windows.

All advise wellcome.

---

### Post by howefield on 2022-02-10
> **newboy19 said:**
> ..but cant see how to open the terminal if i click as recommended Ctrl+Alt+T...

Try the "Windows" key + T

---

### Post by mIk3_08 on 2022-02-10
> **newboy19 said:**
> I have 10 year old Lenovo laptop which is not suitable to take Win 11 as i am only a general user on the net for shopping.utube.searching. banking etc i dont play games or need a office programs so i thought i would ditch Windows and try a chromebook or Linux i have Ubuntu 18-04-6 lts on a on  a old Toshiba satellite L300 laptop which i have had a bit of practice on to see how i get on i have Firefox on it and all is well but i wanted to get iplayer and tv channels but this were i have a problem i looked up how to get iplayer but cant see how to open the terminal if i click as recommended Ctrl+Alt+T the mouse and trackpad freezes  and i cant do nothing the issue on tv channels is i have clicked the DRM but nothing will play also on BBC news site the news clips wont play but on utube and facebook it all works fine, The Toshiba  has 1.8 Mem. 245 GB that is the only OS on there my idea is if i can master the use of Linux of it i can get the latest Ubuntu on my Lenovo laptap and forget Windows.

All advise wellcome.

If you are going to install a new Linux Ubuntu Operating System. I suggest you go with the long term support (LTS) you wont regret it.  For more release information of Linux Ubuntu you can just [click here]("https://wiki.ubuntu.com/Releases").  And [click here]("https://ubuntu.com/download") for the latest Linux Ubuntu Release download page.
Here are some installation instructions, guides for you. Just follow it for more best and accurate results. 
Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") for a Quick Install from USB. This is a quick guide to installing from a USB memory stick.
And Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStick") for Installation from USB - Installing from a USB memory stick (full version).
USB stick + grub - Similar to above but using grub. [Click Here]("https://help.ubuntu.com/community/Installation/FromCForUSBStick")
Installation/iso2usb - Overview: cloning and extraction, tools and a simple 'Do it yourself' extracting method. [Click Here]("https://help.ubuntu.com/community/Installation/iso2usb")
Smart Boot Manager - Installing from a PC which will not boot from a CD. [Click Here]("https://help.ubuntu.com/community/SmartBootManager")
And the BBC iplayer is also a supported application with the Linux Ubuntu  Operating System. They have their instructions on how to install in  their website. Just follow it for more smooth installation of the  application  
Good Luck and Cheers.

---

### Post by yancek on 2022-02-10
A 10 year old computer might not be the best for Ubuntu but you could try Xubuntu or Lubuntu or a non-Ubuntu system such as AntiX.  Maybe do an online search for Linux on older computers to get more uggestions.

---

### Post by mastablasta on 2022-02-10
BBC clips and news should work out of the box. it is possible that older machine has a bit worse GPU or not so well supported. So the CPU get's more load and then if that one is not a good one it can cause everything not to run well or to run at all. i would suggest a live session from boot on a newer machine.  

also 10 year old doesn't mean anything. it can be from this year with bad configuration and it won't play all the stuff properly. i have one small netbook from 2013 or so. it was soooo slow on win7 starter. it did better on Linux but man was it crashing sometimes and lagging. Youtube would play fine but some other video would give me issues - not playing, freezing, crashing, making fans run like crazy... we could play left4 dead on it or older minecraft but still occasionally it would get system crashes. it has 512 MB GPU chip and not a good CPU (one of the budget ones from the time - low power usage, low computing power). total it had 2 GB RAM memory. win7 starter only supports up to 2 GB. 
anyway last year i decided to upgrade ram to 8 GB since kids were using it for school and to open some office stuff and then look at it or take notes from it and it was bad experience. as soon as i upgraded the RAM, everything works so well. no more lags, videos play well, they could move to another room to do school work. so it still has some life in it. i bet it would be even better if i also upgraded the HDD to SSD. but that is not necessary yet an di am not sure if this investment would actually be worth it for such an old machine.


for office work you need something like i3 or Ryzen 3 preferably a newer model with nvme or SSD disk inside. 10 year old i5 or even i3 might also get you through, but it really depends on the GPU, it's driver support, and things you are doing on it.

---

### Post by grahammechanical on 2022-02-10
Even after activating DRM content in Firefox settings you will also need to install Ubuntu Restricted Extras if it is not already installed. Those extras contain some proprietary audio and video codecs that we need to play some content. This is how I solved a problem using ITV hub recently.

Regards

---

### Post by newboy19 on 2022-02-11
Thanks for the info and have now managed to open the terminal to try and install the programs you all suggested after entering the sudo command i am then asked for admin password and when i try nothing happens he cursor is not flashing and i cant type anything else so cant progress on,  my OS is now the latest version after update during the install i had notification that 3 third party apps were turned off but i could turn them back on using package manager so were would i find that ??

---

### Post by tea for one on 2022-02-11
> **newboy19 said:**
> Thanks for the info and have now managed to open the terminal to try and install the programs you all suggested after entering the sudo command i am then asked for admin password and when i try nothing happens he cursor is not flashing and i cant type anything else so cant progress 

When you use the terminal with sudo, there is no [COLOR="#0000FF"]echo[/COLOR] of the keystrokes for your password.
Type your password and press Enter.

---

### Post by TheFu on 2022-02-11
> **yancek said:**
> A 10 year old computer might not be the best for Ubuntu but you could try Xubuntu or Lubuntu or a non-Ubuntu system such as AntiX.  Maybe do an online search for Linux on older computers to get more uggestions.

+1 for Lubuntu. The LXQt DE is lite and easy to use.

Video playback is mainly tied to the GPU and having drivers for the GPU that natively decode h.264 videos.  Around 10 yrs ago is when this really became something included in very low-end systems. It made Chromebook hardware one of the cheapest/best youtube content platforms on Earth.  Alas, some machines of that time didn't have GPUs or iGPUs with any support for hardware decoding of h.264, so they struggle and fail with content over about 600p.  I've tested this at length.  I had an Asus Eee which could do 600p content, but stuttered badly on 720p.  Then I got a cheap Acer C720 Chromebook ($200 back then) and it easily played everything youtube had even with a Celeron CPU and iGPU.  Use C720s can be had for $60 today.  At the time, Intel hadn't figured out how much CPU a chromebook would actually need, so that Celeron 29950U CPU was much more powerful than most later Chromebook CPUs for about the next 5 yrs, unless someone paid 2x more.  

There was a bonus. That Acer C720 could easily run Ubuntu of the day and I wiped ChromeOS for Lubuntu on that machine. Used it for a few years before the keyboard broke. Since 2010, pretty much all laptop keyboards are made to wear out, so look at what it takes to replace them, figure out if you can do that (I bricked my C720 attempting it) and be certain to consider labor costs.  Basically, changing a keyboard on a $200 Chromebook costs $130. $100 labor and $30 for the hardware.

If you want to reuse this old computer, there are ChromiumOS distros that provide the chromebook experience. Definitely worth check out. Most make it easy to install directly on hardware because they wipe everything else there first.

If you want a new chromebook, then I'd look up the planned support period for whatever machine you are considering.  The OS will lose support ... some in 3 yrs, some in 5 and a few have 10 yrs of guaranteed support. By then, you'll know enough.  The support period on Chromebooks is very important.  Google pushes OS updates whenever they like. No way to stop it if the machine is connected to the internet.

Chromebooks can be great for some people.  I always needed a little bit more OS than they provide. Same for Android tablets.  I tried to travel 3 weeks overseas with a 10inch Android tablet and found it limiting.  Oddly, I was able to travel almost 2 months with a 4 inch Debian-based tablet overseas and didn't have the same issues.  There's something about having a full GNU-capable OS with a full network stack that I can control. I did the Debian travel before the Android travel. Eventually, I moved to a 10inch Asus Eee and was content with that for a few years, until the video playback was just too limiting as more and more content was 720 and 1080 resolution.

If you can run **inxi -Gbxx**, we'll have the basic information needed to provide better advice.  Boot from any Ubuntu flash drive in "Try Ubuntu" mode, install inxi, then run it from a terminal with those options and finally, copy/paste the results back here, wrapping the output in 'code tags' ... that's the (# button) in the advanced reply. Use it like you would a quote-tag.

---

### Post by newboy19 on 2022-02-13
I checked and Restricted Extras is installed but still no joy i have tried all info on the net about installing BBC ipayer  but again no joy the commands are not recognized the laptop now has the latest Ubuntu version after upgrade and i am happy with the outcome apart from the TV channels.  i can live with that .

Thanks for your help.

---

### Post by newboy19 on 2022-02-26
I am trying to install ubuntu restricted extras and as you can see from screenshot i am not making much progress i have tried several commands to try and sort this but none are recognized  The second screenshot is iplayer that i seem to have installed but i have no idea how i can use it as i dont know were it is

---

### Post by Impavidus on 2022-02-26
Try running```
sudo dpkg --configure -a
```like suggested, but this time don't forget the spaces.

Furthermore, the package you want to install is called ubuntu-restricted-extras, with two dashes:```
sudo apt install ubuntu-restricted-extras
```It may ask you to accept a user agreement. It uses a classical text-based menu. Use the keyboard: tab to select, enter to hit a button.

---

### Post by newboy19 on 2022-02-26
Thank you so much its amazing what a extra space will do all working fine now .

---


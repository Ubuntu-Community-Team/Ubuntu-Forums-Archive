---
title: "A newbie viewpoint on 'it  should just work'"
date: 2007-08-13
forum: General Help
---

### Post by Guyver1 on 2007-08-13
Hi all

just recently joined the Ubuntu connumity. currently dual booting with XP on my Alienware m9750 laptop.

I'd like to put forward some opinions and idea's which will hopefully generate some discussion and positive/constructive responses and also some intelligent counter arguments.

this thread for me will relate to my frustrations and concerns with the 'it should just work' tag line with regards to hardware and drivers.

let me give you a bit of background:

I've been using PC's since 1999, 99% for gaming. back in the day tweaking your win98 system was key to get the best performance, best framerates etc. Im geek enough to know what all my bios options do, how to tweak and edit the registry, how to tweak my internet connection. What i never had to do was mess about with drivers or hardware. Yes some drivers would cause crashes so you'd roll back to a driver that worked and waited for a fix. But hardware and drivers on windows is the true meaning of 'it should just work'.

You install windows, 95% of your hardware will get installed and working (some with a default driver that you'll need to upgrade to get full functionality) then the remainder of the hardware is simply an exe of the supplied driver disk or a simple download off the net. install said exe and device works, fully, properly.

Now im not completely green to linux, I used to work for Wireplay running Unreal Tournament servers on a remote suse box via putty. I even got myself a spare machine to install suse on to 'learn' the basics of bash so i could run my servers faster and more efficiently. In that respect it didnt matter if all my devices worked or not.

I like Ubuntu so far, I like the GNU principles, i like the idea of not being tied to a monopolistic company.

What i dont like is trawling for hours through forums/google/websites just to get my <insert random piece of hardware here> working properly. 

For me linux should be exactly the same as windows on a hardware level.

For example, my current situation, I have the Realtek HD Audio soundcard in this lappy and 2x 512Mb nvidia GeForce Go 7950 GTX cards and the intel 4965 wifi card.

windows, install driver, reboot, done. Each hardware component has x amount of settings/sliders/radio buttons/options once installed and they all work (give or take the odd minor glitch/bug under certain driver releases)

Linux, not even close to the above, my soundcard has been the 'easiest', downloaded realtek's latest driver, ran the automated install, bombed out first time due to a missing library, ok no prob got that, re-ran install, installed fine. on startup instead of the startup wav. i get white noise. i only get sound if i plug my headphones in, the laptop speakers dont work, i dont even have the option as i do in windows to 'mute speakers when headphones plugged in'.

GFX, I use SLI in windows, had to install a 3rd party app just to get the nvidia drivers installed properly (envy), i had to trawl then to find how to enable SLI, i still dont know if its enabled or not and i have no idea if it is enabled how to change render mode (i'm waiting on a reply in another forum thread)

wi-fi, dont get me started, from what ive read so far, install different kernel, do this, do that, edit this, edit that. :(


Please dont think im some sort of whiner, I'm not, i've spent years being 'geek' on windows and learning how to 'tweak' etc, I'm geek enough that it annoys my wife how much time i spend on the PC. I love learning, but I love playing/competing at UT than having to trawl through websites and know how to low level code just to get a sound card to work :(

I would love to be able to remove windows, but right now I really cant, I dont have the time to be geek anymore, I have a family and limited time, I can accept that software can not do everything all the time, but i really expect to have my hardware work like its supposed to :(

How can this situation be improved? If the linux community REALLY wants to go mainstream and attract more people, it really needs to improve on the hardware/driver area, your average joe punter isnt gonna last 2 minutes on linux. 

Who's at fault? the makers of each distro? the hardware manufactures? both? Why cant a piece of hardware that works prefectly well with all its settings available work just the same on linux with all its settings/radio buttons/drop down settings intact?

Im about to subscribe to cedega to get my games working in ubuntu, im making effort to get up that steep learning curve, but i fear only because i'm geek enough to make the effort to make the climb in the first place. 

Software i cant accept as not 'just working' you can work around that. but when it comes to hardware i really think linux has a really long way to go before it can compete even close to windows.

for now i cant leave XP behind, but i wish i could.


cheers for reading.

Leon.

---

### Post by 5-HT on 2007-08-13
***Disclaimer: I'm not trying to be harsh, just honest.**

> **Guyver1 said:**
> Hi all
For me linux should be exactly the same as windows on a hardware level. 
It's not. It's close, but it's not. This has nothing to do with Linux, and everything to do with the hardware manufacturers who 1) do not release linux drivers, or 2) do not allow anyone outside the company to get the specs for the device so that they may write a Linux driver.


> **Guyver1 said:**
> 
wi-fi, dont get me started, from what ive read so far, install different kernel, do this, do that, edit this, edit that. :(
The new iwlwifi driver from intel supports your card (yay intel! :)). I and many others here could hep you getting it installed and configured.

> **Guyver1 said:**
> 
How can this situation be improved? If the linux community REALLY wants to go mainstream and attract more people, it really needs to improve on the hardware/driver area, your average joe punter isnt gonna last 2 minutes on linux.

1. Linux has  *never* wanted to go 'mainstream', this is not a popularity contest. Why do so many people think that Linux is trying to take over?
2. The hardware/driver area is  *completely* not in the hands of any  *nix developpers, it's in the hands of the  hardware manufactureres who either 1) won't release the drivers, or 2)won't  allow anyone outside the company to do so.
3. Linux honestly doesn't care about 'Joe Punter'...really...use it if you like it, if not then don't. No one's forcing you (escape from Microsoft does not count. There are plenty of other OS's around, and if none suffice--well, Microsoft have done a lot of hard work to make sure of that). Now, there are some companies who will sell you a distro and provide full handholding support. Please use their services if you find yourself out in the cold.  If windows is a better match then please, by all means, use it. Those who use Linux use it because they want to. It has nothing do to with escaping windows.
> **Guyver1 said:**
> 
Who's at fault? the makers of each distro? the hardware manufactures? both? Why cant a piece of hardware that works prefectly well with all its settings available work just the same on linux with all its settings/radio buttons/drop down settings intact?

Hardware manufacturers

> **Guyver1 said:**
> 
for now i cant leave XP behind, but i wish i could. 
It's all about which OS you are more productive with. If it's XP, then please use XP. Now there are some other considerations (FOSS), but if that's not a philosophical concern for you, use what works!:)
cheers,


** *EDIT:** forgot to mention: If you purchase your hardware specifically with Linux support in mind, you will NOT run into any problems. The issues come to bear when trying to install with hardware for which there is no Linux support. You have plenty of choices of which compatible hardware to buy that will work perfectly with Linux, trying to install with incompatible hardware is not an excuse.

---

### Post by ramjet_1953 on 2007-08-13
I think that perhaps you may be looking at things from the wrong angle.

Many hardware manufacturers refuse to release open source drivers. They do this for proprietary reasons.

Without the necessary driver, or any hardware, or firmware information, it is a very difficult task indeed for a Linux programmer to write a driver.

A couple of instances, which are regularly causing grief for Linux users are Lexmark printers and either ATI, or SIS video cards.

A very similar problem is now arising with people who are shifting from XP to Vista. Apparently, there are quite a few pieces of hardware out there, that don't have the necessary driver.

So, the bottom line is that with hardware, the finger needs to be pointed at the the manufacturers of the hardware, not the operating system.

Regards,
Roger

---

### Post by ZipoTe on 2007-08-13
Send this letter to your <insert random piece of hardware here> company. If they don't support linux, tell them!! Go to your hardware company's forum and complain there about their point of view. That's the way it works. Maybe one day they release a functionaly driver for linux so we all will enjoy with our hardware :)

---

### Post by Guyver1 on 2007-08-13
thanks for the replies. I knew the hardware makers were mainly at fault, but not why. It would appear that protecting their 'tech' is more important than getting it working on anything other than windows...

Is linux then destined to forever suffer from hardware/driver problems?

---

### Post by 5-HT on 2007-08-13
> **Guyver1 said:**
> 
Is linux then destined to forever suffer from hardware/driver problems?
Hopefully not :), but it's hard to tell. So far, time has been good and more manufacturers are opening up. Either way, there are *tons* of Linux drivers out there for certain hardware, it's just a matter of using those devices.
If there are any hardware issues you're experiencing, please make a new thread and, if the devices are supported, people here can help you to get them work (wireless is one that comes to mind: the issue with your card is that the intel driver is fairly new--well the card itself is fairly new--and the new wireless subsystem {mac80211} has only been implemented in kernels >=2.6.22. There is a way to patch your kenel for the new subsystem if it doesn't have it. The problem here is not Linux in general, but Ubuntu's release philisophy. All rolling-release distros have implemented the new stack and drivers).

cheers,

---

### Post by Guyver1 on 2007-08-13
oh and what im frustrated at is not a 'lack' of drivers, but the situation that when drivers ARE released they either A. install but dont work properly and dont  give you everything you get in windows, like the same settings/options etc. or B. they need some severe manual configuration of various configs/kernal/libraries etc thats beyond most people in terms of time needed.  or C. they simply wont install.

please understand im not some MS fanboy bashing 'nix, im someone trying to understand and gain knowledge on why things have to be so 'difficult' (for want of a better word) on 'nix..... 

the strange thing is im getting frustrated and challenged and enjoyment all at the same time :)

---

### Post by Steveway on 2007-08-13
> the strange thing is im getting frustrated and challenged and enjoyment all at the same time 
That's the right mood.
This is how I forced my selve to keep using Linux and learnig to love it. You're on the right way.

---

### Post by 5-HT on 2007-08-13
> **Guyver1 said:**
> oh and what im frustrated at is not a 'lack' of drivers, but the situation that when drivers ARE released they either A. install but dont work properly and dont  give you everything you get in windows, like the same settings/options etc. or B. they need some severe manual configuration of various configs/kernal/libraries etc thats beyond most people in terms of time needed.  or C. they simply wont install.

Yup, :( some drivers do not have the equivalent functionality as they do in Windows. Again it's a manufacturer issue, but it's frustrating none-the-less.

In terms B) & C), once you get used to the *nix way of doing things, I can bet that everything will make a lot more sense. Yes, sometimes you will need to dive into config files or recompile a module or kernel, but the great thing about *nix is that all config files are plaintext! This might not sound important, but have you ever tried to change config files in Windows? It's all in hex! Who can read that?
There is a quite a learning curve, but in the end I personally feel much more at home running Linux. Yes, things don't always go as desired, but if something does go wrong you have a much, much easier time fixing it in *nix (what's the equivalent in Windows, Reinstall? What happens if there's a particular issue with the program and your system? In *nix you can fix that right away, in Windows you are not allowed to).
cheers,

---

### Post by bluenova on 2007-08-13
You&#8217;re preaching to the converted. Go preach to the hardware vendors who unfortunately still need converting.

---


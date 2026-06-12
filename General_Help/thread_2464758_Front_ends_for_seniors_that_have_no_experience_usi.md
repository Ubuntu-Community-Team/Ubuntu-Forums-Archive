---
title: "Front ends for seniors that have no experience using a computer"
date: 2021-07-11
forum: General Help
---

### Post by SUPERFITTER on 2021-07-11
I am looking for a Ubuntu front end to make computer use easier to use for seniors with no computer experience.  I have looked at WOW and Telikin computers (that are the same basic computer)  that are just a ripoff for seniors. 
Thanks in advance

Dennis

---

### Post by grahammechanical on 2021-07-11
You cannot teach an old dog new tricks. That might be true for dogs but I do not accept it to be true for humans. That being said, Ubuntu comes with many universal accessibility options. Check out System Settings>Universal Access.

Would an on screen keyboard be useful?

[https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html.en)

A lot will depend on the prospective users needs and the limitations of the hardware. And at some point the new user will have to be trained in how to use the equipment and how to keep the OS up to date and secure. 

Regards

---

### Post by him610 on 2021-07-11
Some thoughts...
Does the Senior positively want to learn how to use a computer?
Patience and frustration avoidance are needed by all.
Each Senior must realize they won't break something if they make a mistake. 
The instructor/tutor will need to walk the Senior through each step. May need to repeat this each day for awhile.
I would expect maintenance and upgrades are responsibility of instructor/tutor.
I think little kids are taught about computers using Raspbian OS. Couldn't the same be used for Seniors?
Maybe a Chromebook?  It is all browser.
If eyesight and hand-eye coordination is good then universal access or on screen keyboard probably not needed.
Mouse probably better than touchpad.
I taught a Senior how to use a computer (Ubuntu) some years ago. It takes some handholding initially, but with each step more confidence is gained. By the way, that Senior uses a web browser 99% of the time. Logs on every day; only asks for help occasionally.

What kind of hardware will the Senior be using?

---

### Post by dragonfly41 on 2021-07-11
I suggest using a launcher such as Albert. Binding say [Num+Enter) (which is nearest the mouse) brings up a simple popup query field.. The tutor will need to enable/write the appropriate python extensions for the user. In fact the conf file can also be controlled by Tutor to reflect different mixes (profiles) of extensions. Triggers can be written on a cheat sheet.

---

### Post by rsteinmetz70112 on 2021-07-13
Since I'm technically now a senior (almost 70) I wonder how many Seniors today really have no experience with computers. My parents (now gone) would have been 99 this year and both used computers after they retired.  Even my very non technical MIL used a computer some before she to left us. I would think a simple interface with a few simple icons and an intelligent voice assistant would be great. It could suffice for most people unless they have some disability. I don't know if there is a good voice assistant. But then I'm just another old guy.

---

### Post by ActionParsnip on 2021-07-13
What are they planning to use the system for? If they just need a web browser and nothing else then setting up a web browser kiosk will do just fine. You can manage the systems yourself using SSH :guitar:

---

### Post by HermanAB on 2021-07-13
Hmm, considering that it was us seniors who invented the computers to begin with…

In my experience, the biggest annoyance is small unreadable fonts on fuzzy low resolution displays.  If you get a big high resolution (retina) screen then any old geezer will be much happier.

---

### Post by TheFu on 2021-07-13
My 82 yr old Mother used Lubuntu for 3 yrs. It was all point-n-click for her. 

I did all the systems management from 3 states away over ssh. I setup local backups for her to a local USB drive, did weekly patching and weekly backups for her most important information (basically just financial data).  I did capture system and personal settings too, but she didn't need to know about that.

She was running WinXP before, but got hacked by an enticing "New Baby Pictures" email from a grand daughter's email account who actually just had a baby.  I'd say no grandmother would NOT click on that sort of email. It is physically impossible to prevent. She never had a chance.

IF they only need a web browser, then rather than a full Ubuntu desktop, a chromebook clone would be better.  Look for a "ChromiumOS" installation.  Those are FAST and run on minimal hardware.  Heck, I saw a new Acer Chromebook for $129 on sale this week.  For someone with minimal computing needs, I'd honestly push them towards a chromebook.
Here's the Walmart page: [https://www.walmart.com/ip/Acer-Chromebook-311-11-6-HD-Intel-Celeron-N4020-4GB-LPDDR4-32GB-eMMC-Pure-Silver-Gigabit-WiFi-Bluetooth-5-0-CB311-9H-C4XC/588464990](https://www.walmart.com/ip/Acer-Chromebook-311-11-6-HD-Intel-Celeron-N4020-4GB-LPDDR4-32GB-eMMC-Pure-Silver-Gigabit-WiFi-Bluetooth-5-0-CB311-9H-C4XC/588464990)  The small screen (11.6 inch) and laptop keyboard/touchpad can be augmented using an external monitor, real keyboard and USB mouse.  There is a Dell 20inch monitor, P2014H, for $90 there to get a larger screen.  I've seen wireless keyboard+mice paks for $20, though personally, I'd never use wireless (any sort) for a keyboard OR a mouse.  

There are cheap 15 inch chromebooks too. Let me see what I can find: 

Just be certain to get at least 4GB of RAM, 32GB of storage, and at least 1500 passmarks. 
[LIST]
[*]Celeron N4000: [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4000+%40+1.10GHz&id=3239](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4000+%40+1.10GHz&id=3239) is close enough to 1500.
[*]Celeron N4020: [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4020+%40+1.10GHz&id=3683](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4020+%40+1.10GHz&id=3683) is a little faster.
[/LIST]

Just throwing out options.  There are used chromebooks for $75 lots of places.  If someone has an old PC or laptop, using the ChromiumOS version really would be a great option.

Chromebooks are probably the single most secure networked computing device available today.  Of course, we can't confuse security with privacy. Those are not the same thing.

If you need a light Linux and don't want just ChromeOS or ChromiumOS, then a 130MB TinyCore will do what most seniors need and run FAST on almost any hardware.  I use TinyCore for my online banking. The entire OS gets loaded into RAM, so nothing will be faster.   Put only the needed programs into the distro - a GUI in 16MB, add a few programs to get 64MB OSes or put lots of popular programs for 130MB.

---

### Post by QIII on 2021-07-13
Nothing wrong with being a senior.  I get by pretty well, except for the fact that Mrs QIII has to write our address on the inside of my underwear in case someone finds me walking down the county road in just my underwear, black socks and garters.  Fortunately most of the folks around here know where our farm is and would just bring me back.

I am going to echo TheFu with a bit of my philosopy:  Don't get hung up about the OS.  Ubuntu or any other Linux distro.  ChromeOS.  Windows if you do *a lot of work to harden it* and train the user.  From the user's perspective what you want is something that will become familiar and do what is needed.  

The hardware need not be expensive or powerful.  

But I would say that if a bit of web browsing and other light work is all that is desired, something presenting the least possible number of services in its exposure to the outside world would be best.

---

### Post by mastablasta on 2021-07-14
> **HermanAB said:**
> 
In my experience, the biggest annoyance is small unreadable fonts on fuzzy low resolution displays.  If you get a big high resolution (retina) screen then any old geezer will be much happier.

+1 

large screen, large(er) icons & text, make it crisp.

if they want to learn, they will learn. might need help with maintenance. i taught my grandfather (he passed away some time ago). his biggest issue was spam email on his local email address, but i've solved that with an email scanner at the time. questions and curiousity here and there. he always wrote it down, so he would remember what to do. he learned a bit of excel for his stock of drinks (he had a small bar), but i improved his table and showed him how to do it if he wanted to do it himself next time. and he was very happy with that.

---

### Post by Autodave on 2021-07-14
No matter what size screen, you can always make the icons bigger and the text on any website bigger by choosing a lower resolution that the screen's max.  My mother only has a 16" screen, but lowering the resolution, she has no trouble seeing and reading it.

---

### Post by rsteinmetz70112 on 2021-07-14
I mentioned this to my non technical computer user wife and she said the most important thing was to have someone available to help. Depending on the setting that may be either easy to do or hard.

---

### Post by grahammechanical on 2021-07-14
This thread has turned into general advice on accessibility options. That is nice. I would like to add to the list Gnome Orca screen reader.

[https://help.gnome.org/users/orca/stable/](https://help.gnome.org/users/orca/stable/)

We do have another post requesting help for finding speech control software. Please check it out.

[https://ubuntuforums.org/showthread.php?t=2464872](https://ubuntuforums.org/showthread.php?t=2464872)

Regards

---


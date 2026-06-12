---
title: "Lexmark All-In One Drivers..."
date: 2006-11-22
forum: General Help
---

### Post by online14230 on 2006-11-22
Hi all, and welcome to another edition of: How to mess things up!
Just to recap, I have a Dell optiplex GX150, Intel i850 integrated graphics, and theres a funny looking card stuck into the AGP slot. No plugs or jumpers, its just there! Dapper Drake plus Mandriva 2006. Trust me, Ive had numerous messups with dapper, but Mandriva KILLS me!!
Anyway, as things were going, I managed to get Dapper behaving JUST like a schoolkid: behaving when Im there, but giving everyone else hell. :) I love it!!!
THEN, as the saying goes, "If it aint broke, fix it", I decided to mess around and try AIGLX and run Beryl. hehe. All hell broke loose, because I downloaded all the goodies the howto says to, and sudo dpkg -i *.deb... thing is, I had all these debs on my flashdisk (no internet conmnection, download from XP machine at work and install at home). So half installed, half didnt. So I dpkg 'ed again, and again, and then all of a sudden, it downgraded apt, removed gnome-desktop, removed all- other-things-gnome including rhythmbox, K3B )yes, I have it running under gnome... what a pleasure), and other media players and the like. Then it uninstalled everything under 'system administration' and proceeded to cause my PC to switch off. Not shutdown, switch off. The thing went dead. I pushed, prodded and played with the power button. Nothing. IEVEN tried to arouse it by stripping in front of the PC. Nothing.So I gave up and went to bed. Suddenly, I was woken by my wife, who showed me the PC was on, and waiting at the login screen. YIPPEE!!!. I logged in, and sat there, looking at nothing. EVERYTHING WAS GONE. No problem. I fired up synaptic and tried to re-install from the repositories I have on disk. NIL. NADA. ZIP. It wont even let me mount the disks because it doesnt recognise the Benq 1650 DVD Writer :) Now THAT was funny... I shutdown, booted up and all was fine. Anyway, I managed to add the disks to the repository list and started re-installing, which was going well last I saw the PC. I left it running this morning, knowing that it will access the ISO's as and when needed, and shutdown when done installing my selection. (I HOPE!)

Now, why did Beryl/AIGLX mess with me like that, and how would I get it to run? The how-to's dont seem to apply here. Im a 1 in a million nutcase PC owner. HELP!

Also, I need drivers for a Lexmark X1180 printer. Any idea where I might find ? Lexmark has a developers kit, which aint any help to me since all I develop are pictures :) (and an odd illness, occassionally )..
Everywhere Ive looked, people are ](*,) and :( and Ive seen a few cry. The ones that DO have a working driver are :-# . HELP ME PLEEZE!!!!????

---

### Post by camilluk on 2006-11-22
Can't really help you, but your story is very funny. I'm pretty sure voodoo has something to do with what happened to your pc... ;-)

---

### Post by online14230 on 2006-11-22
Thanks, CamillUK, youre a whole big ray of F&%^Y^NG SUNSHINE :)

At least you read it and said SOMETHING! Everybody else just reads, laughs at my plight and gooes on their merry way, blissfully Ubuntuing, while Im stuck at an XP machine, running DAMN IEXPLORE, reading mail through this stupid OUTLOOK. Im REALLY not a happy person.

---

### Post by adam.tropics on 2006-11-22
> **online14230 said:**
> Thanks, CamillUK, youre a whole big ray of F&%^Y^NG SUNSHINE :)

At least you read it and said SOMETHING! Everybody else just reads, laughs at my plight and gooes on their merry way, blissfully Ubuntuing, while Im stuck at an XP machine, running DAMN IEXPLORE, reading mail through this stupid OUTLOOK. Im REALLY not a happy person.

OK, so when you try and install stuff, dependencies need to be resolved. When you go outside of the main repos, whilst apparently extremely exciting (!), packages are not always perfectly put together, and this can lead to serious dependency issues, which the package manager, unable to resolve by adding stuff (no net), will fix by removing stuff until the dependency problem is solved. In the worst case scenario, namely yours, this I suppose could lead to pretty much the whole system being removed. Not good! 

If you want to try stuff like that, honestly, I would wait till you can get on-line, particularly for the likes of Beryl. Had you been on-line, the odds are you wouldn't be re-installing it all now!

As for Lexmark printers, sorry to be the ray of sunshine, but I don't have one.

---

### Post by online14230 on 2006-11-24
Unfortunately for me, I live in merry ol South Africa, where the phonelines promise 56k and deliver less than half that (WHEN theyre running!) ADSL costs are just ridiculous. I just read a comparison between a few, and basically, Im screwed. Basically, we pay WAY more than anyone else, almost double...

Check out the MyADSL broadband report for a breakdown or search the forums here for it. Ill post it soon enough.

---

### Post by adam.tropics on 2006-11-24
> **online14230 said:**
> Unfortunately for me, I live in merry ol South Africa, where the phonelines promise 56k and deliver less than half that (WHEN theyre running!) ADSL costs are just ridiculous. I just read a comparison between a few, and basically, Im screwed. Basically, we pay WAY more than anyone else, almost double....

How about [this for a plan though]("http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html"). Either get someone with a VERY decent adsl plan, or see if they can burn and send you a copy for a few bucks....sure would make your life easier.

---

### Post by deadgobby on 2006-11-24
> **online14230 said:**
> Hi all, and welcome to another edition of: How to mess things up!
Just to recap, I have a Dell optiplex GX150, Intel i850 integrated graphics, and theres a funny looking card stuck into the AGP slot. No plugs or jumpers, its just there! Dapper Drake plus Mandriva 2006. Trust me, Ive had numerous messups with dapper, but Mandriva KILLS me!!
Anyway, as things were going, I managed to get Dapper behaving JUST like a schoolkid: behaving when Im there, but giving everyone else hell. :) I love it!!!
THEN, as the saying goes, "If it aint broke, fix it", I decided to mess around and try AIGLX and run Beryl. hehe. All hell broke loose, because I downloaded all the goodies the howto says to, and sudo dpkg -i *.deb... thing is, I had all these debs on my flashdisk (no internet conmnection, download from XP machine at work and install at home). So half installed, half didnt. So I dpkg 'ed again, and again, and then all of a sudden, it downgraded apt, removed gnome-desktop, removed all- other-things-gnome including rhythmbox, K3B )yes, I have it running under gnome... what a pleasure), and other media players and the like. Then it uninstalled everything under 'system administration' and proceeded to cause my PC to switch off. Not shutdown, switch off. The thing went dead. I pushed, prodded and played with the power button. Nothing. IEVEN tried to arouse it by stripping in front of the PC. Nothing.So I gave up and went to bed. Suddenly, I was woken by my wife, who showed me the PC was on, and waiting at the login screen. YIPPEE!!!. I logged in, and sat there, looking at nothing. EVERYTHING WAS GONE. No problem. I fired up synaptic and tried to re-install from the repositories I have on disk. NIL. NADA. ZIP. It wont even let me mount the disks because it doesnt recognise the Benq 1650 DVD Writer :) Now THAT was funny... I shutdown, booted up and all was fine. Anyway, I managed to add the disks to the repository list and started re-installing, which was going well last I saw the PC. I left it running this morning, knowing that it will access the ISO's as and when needed, and shutdown when done installing my selection. (I HOPE!)

Now, why did Beryl/AIGLX mess with me like that, and how would I get it to run? The how-to's dont seem to apply here. Im a 1 in a million nutcase PC owner. HELP!

Also, I need drivers for a Lexmark X1180 printer. Any idea where I might find ? Lexmark has a developers kit, which aint any help to me since all I develop are pictures :) (and an odd illness, occassionally )..
Everywhere Ive looked, people are ](*,) and :( and Ive seen a few cry. The ones that DO have a working driver are :-# . HELP ME PLEEZE!!!!????

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)
[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy?highlight=%28AIGLX%29](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy?highlight=%28AIGLX%29)
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters?highlight=%28lexmark%29](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters?highlight=%28lexmark%29)
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?highlight=%28lexmark%29](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?highlight=%28lexmark%29)

I hope the links help. Enjoy your day now.
Gobby

---

### Post by Sef on 2006-11-24
> Also, I need drivers for a Lexmark X1180 printer. Any idea where I might find ? 

Check [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-X1185").

It's for an X1185, so will likely work for you.

---

### Post by blakeatl on 2007-01-05
Here's another tip for anyone needing to install drivers for an X1100 model.....I have the X1185. When you follow the commands to use in terminal and have to install alien, I found that sudo apt-get install alien does not work when trying to pull from the cd. I had better luck using the sudo aptitude command. Once you get alien installed and you try to install the drivers....make sure you're in the desktop directory as instructed (desktop/lexmark). A change directory (cd) is a must or nothing will get installed. As a mostly new person to Linux......I tried to do it from the default line in terminal. Took me a few hours over time to figure that out as the person giving the instructions assumes we should know that. Once everything goes fine and you're setting up the printer and try to find the driver....it's not there.....you have to go to ./usr/share/cups/model/ and find the driver there. Last thing....if you already have a printer set up with the wrong driver......delete the whole printer and create a new one. This is how I got mine to finally work and hopefully it will help someone else. Thanks to the guys for posting the directions to get this thing running finally.

---

### Post by CiriusX on 2007-02-12
> **blakeatl said:**
> Here's another tip for anyone needing to install drivers for an X1100 model.....I have the X1185. When you follow the commands to use in terminal and have to install alien, I found that sudo apt-get install alien does not work when trying to pull from the cd. I had better luck using the sudo aptitude command. Once you get alien installed and you try to install the drivers....make sure you're in the desktop directory as instructed (desktop/lexmark). A change directory (cd) is a must or nothing will get installed. As a mostly new person to Linux......I tried to do it from the default line in terminal. Took me a few hours over time to figure that out as the person giving the instructions assumes we should know that. Once everything goes fine and you're setting up the printer and try to find the driver....it's not there.....you have to go to ./usr/share/cups/model/ and find the driver there. Last thing....if you already have a printer set up with the wrong driver......delete the whole printer and create a new one. This is how I got mine to finally work and hopefully it will help someone else. Thanks to the guys for posting the directions to get this thing running finally.

 Hi blakeatl
This is the info I've been looking for since I installed Edgy 3 days ago. I didn't need to play "hunt the driver" in Dapper and I couldn't work out why it didn't automatically appear in Edgy after a successful install - talk about thick - especially after doing just that so many times restoring drivers on Evil Empire boxes. You've saved a (possibly) sane man from a complete breakdown!! Many thanks for taking the trouble to post this info, cheers.

---

### Post by Brunellus on 2007-02-12
I'm moving this to the general support forum.  Please be advised that Beryl and Compiz are off-topic in absolute beginners.  

If you live on the cutting edge, you're bound to bleed from time to time.  Remember that when you install beta software.

---


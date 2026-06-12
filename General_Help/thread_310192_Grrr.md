---
title: "Grrr"
date: 2006-11-30
forum: General Help
---

### Post by koulanji on 2006-11-30
yea, I was following the comprehensive sound guide [here]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=configuring+soundcard"), because ubuntu is ******* retarded when it comes to my [sound blaster audigy]("http://www.ubuntuforums.org/showthread.php?t=295272") While i was following the guide to get the ALSA drive from a fresh kernel my screen blacked out, so I logged back in only to find that my ternminal is missing, and when i try to use synaptic to get back the ubuntu gdm i get this lovely error the one that says i need to re-configure dpkg. As you can see, I am more than three ******* shades of pissed, because my soundcard sometimes works and sometimes does not. I have tried two other soundcards from comp USa and I have the same frigging problem, so I know it's not my soundcard.

---

### Post by koulanji on 2006-11-30
Actually the exact error message I recieve is this one: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

And before I get a lecture about me stopping the install my screen went blank for the 20 minutes before I hit the restart button.

---

### Post by taurus on 2006-11-30
```
sudo dpkg --configure -a
```

---

### Post by po0f on 2006-11-30
koulanji,

Your sound problems arose from some programs using ESD for the sound server, and some programs using the hardware directly via ALSA.  Try switching all references of one to the other in programs that you use.

[EDIT]

Would a moderator please edit the tags for this thread?  Thank you.  :)

---

### Post by koulanji on 2006-11-30
> **taurus said:**
> ```
sudo dpkg --configure -a
```

oot@axisaudio-desktop:/home/axisaudio# sudo dpkg --configure -a
root@axisaudio-desktop:/home/axisaudio#

That's what i get in my root terminal or linux console, since this install removed my terminal alltogether :) amazing :-D

---

### Post by taurus on 2006-11-30
If you are logged in as root, then don't include the sudo!!!

```
dpkg --configure -a
```

---

### Post by koulanji on 2006-11-30
> **taurus said:**
> If you are logged in as root, then don't include the sudo!!!

```
dpkg --configure -a
```

nope still does not work. I'm using the linux console, since it is the only thing i have access to.

---

### Post by bettlebrox on 2006-11-30
What happens when you do "dpkg --configure -a" ?

---

### Post by koulanji on 2006-11-30
> **bettlebrox said:**
> What happens when you do "dpkg --configure -a" ?
That's what I want to know. After following the aforementioned sound guide, I have no terminal no gdm, and no access to my desktop, and I get this dumb message about dpkg. How do i access it without the terminal, because I have no OS. Not to mention I can't even access my places.

---

### Post by koulanji on 2006-11-30
After doing dpkg config and trying to reinstall my gdm, which ubuntu chooses to take away, whenever I'm reinstalling alsa for my soundcard, thanks, I cannot log in to any session. It says that my last session lasted less than 10 seconds and I am to try logging in again, because of a failed install. What exactly do i do now? This is exactly why I switched from windows, in order to have some sort of functionality, but apparently I'm mistaken, because now I have lost my papers, my music, my anime and everything else, and why? Because apparently Mr. Mark Shuttlecock does not think that sound is included in computer functionality. My audigy has worked on and off in ubuntu, and so has two of the other older soundcards I've bought and returned to comp USA. I am not using bleeding edge **** people. My audigy is a year old; it should work, and it has worked, just not consistently. And I'm not sorry for being rude, why you ask, because I've lost the majority of my songs, my movies, and some of the work that I have due. This is absolutely ridiculous, especially from linux. If anyone knows how I can log into my session or rescue my gdm from live cd please let me know.

---

### Post by Adramelech on 2006-11-30
Your first place to look for problems should be the boot logs at /var/log, review the X and the boot logs for errors.

EDIT: From the guide you posted:

VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop

---

### Post by taurus on 2006-11-30
> **koulanji said:**
> After doing dpkg config and trying to reinstall my gdm, which ubuntu chooses to take away, whenever I'm reinstalling alsa for my soundcard, thanks, I cannot log in to any session. It says that my last session lasted less than 10 seconds and I am to try logging in again, because of a failed install. What exactly do i do now? This is exactly why I switched from windows, in order to have some sort of functionality, but apparently I'm mistaken, because now I have lost my papers, my music, my anime and everything else, and why? Because apparently Mr. Mark Shuttlecock does not think that sound is included in computer functionality. My audigy has worked on and off in ubuntu, and so has two of the other older soundcards I've bought and returned to comp USA. I am not using bleeding edge **** people. My audigy is a year old; it should work, and it has worked, just not consistently. And I'm not sorry for being rude, why you ask, because I've lost the majority of my songs, my movies, and some of the work that I have due. This is absolutely ridiculous, especially from linux. If anyone knows how I can log into my session or rescue my gdm from live cd please let me know.

You just need to calm down if you really want others to help you!!!  I have Soundblaster Audigy2 ZS in my two computers and they work just fine with Dapper & Edgy...

---

### Post by koulanji on 2006-12-01
After a good night's sleep let me properly articulate my errors. 

1. Ever since I installed dapper, my soundcard has been half working. Sometimes I would boot up and get sound, but heavens help me if I dared to restart, and when I did I had no sound. This included my players, the greeting sound at the GDM and splash screen and AIM. The only way to solve this was to restart my computer numerous times until I got sound. Since edgey eft was on its way, I decided to use the odd restart solution to get my sound. However, when I updated edgey I had the same problem, the soundcard chose to work whenever it felt like it. 

2. I tried 2 other soundcards and the same problem embraced me, so I returned them to comp USA, under the inclination that my audigy was fine.

3. I reffered to the [sound guide]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=configuring+soundcard"). Now this is the interesting part. When typing in all the commands to check for errors, there were none. I got a list of devices when i typed in aplay -i. I did not get the "no soundcard found" error. After checking the alsa mixer, I discovered that no sound was muted, so I plodded on through the guide until I came to reinstalling the Alsa drivers from a fresh kernel. 

"The warning brings up an interesting point that the gdm will be removed once I remove the drivers." Now, I thought the gdm maybe removed after the reboot, but little did I know that the gdm would be removed right then and there, and that I would be greeted with a blank screen. Emphasis on BLANK, because I got no indication that I was in the terminal "[axisaudio@mahfoodnet ~]$ ". After 30 minutes, I figured the removal was done and I restarted.

When I returned, I returned to a desktop with no terminal, no desktop, and no access to my places. I ran the dpkg config in the linux shell, and tried to reinstall the GDM with "sudo apt-get install gdm ubuntu-desktop", and I got a flash of error messages and my computer restarted on its own.

When I rebooted, I was taken all the way to the graphical GDM screen, and not a text based terminal. However, when I tried to log in, I was told that my last session lasted less than 10 seconds, and I was to try again in failsafe mode. I hit ok, and my screen froze for another half and hour. I restarted and tried logging in the failsafe mode as instructed, and I was met with the same problem in EVERY session. And since I cannot log in, I have no access to the terminal or nano or vi, to check any bootlog errors. Ubuntu boots fine until when I log in at the GDM, so again if anyone can tell me, how to access my terminal and the exact codes to fix this horrendous error, I would be glad.

Let me take a moment to point out that the root of my frustration is not your help that for one reason or another does not solve my problems, it is with ubuntu itself. 

Ubuntu prides itself on being one of the most user-friendly distros in town. The reason why I run it on my main machine, as opposed to SUSE or Fedora, is because of the large community.
Although the install is a piece of cake, unlike other distributions it does not allow you to configure anything, like the DEFAULT soundcard, your display, or your network connection. Although removal of these options make installation less tedious or cumbersome,not having them creates more work for the user later on. I've read numerous complaints that users have to edit xorg, setup their network connection, and their sound. If ubuntu had asked me for my default soundcard during installation and made it sure it worked by asking me to play a test sound, see fedora and SUSE, this problem would be non-existent. It's also strange that you have those options, but yet you give the option of manually editing parition tables. WTF? It's much more likely that someone would know the name of their device, than knowing how to edit partition tables. 

Whereas with other distros like Fedora and Suse, you're asked these questions, and it more than likely eliminates problems like this in the long run. 

I can see how removing these options make for a faster less tedious install, but at this point you're replacing efficiency with ease of use, since users will later have to run around configuring devices that are not setup properly. The only reason why I am continuing patiently with this is because I need to pull my papers and my media.

---

### Post by po0f on 2006-12-01
koulanji,

In your other thread, you mentioned that this was on a Dell.  Can you post the output of:
```
[FONT="Courier New"]$ lsmod | grep emu[/FONT]
```
IIRC Dell use an OEM version of the Audigy 2ZS, emuk10k1x should be the module returned.  If it's emu10k1, try this:
```
[FONT="Courier New"]$ sudo modprobe -r emu10k1
$ sudo modprobe emu10k1x[/FONT]
```

HTH.

---

### Post by koulanji on 2006-12-02
I appreciate the help, but is anyone realizing I have no access to my terminal because I cannot log into any session, failsafe, gnome or xgl. My primary concern is logging in and regaining my gdm, which I'm unable to do.

---

### Post by LLRNR on 2006-12-02
> **koulanji said:**
> I appreciate the help, but is anyone realizing I have no access to my terminal because I cannot log into any session, failsafe, gnome or xgl. My primary concern is logging in and regaining my gdm, which I'm unable to do.

Can't you just choose the "recovery mode" boot option from GRUB ? You'll be able to login in text mode...

---

### Post by koulanji on 2006-12-02
And I do that by pressing what button at startup?

---

### Post by LLRNR on 2006-12-02
> **koulanji said:**
> And I do that by pressing what button at startup?

If your GRUB menu doesn't show up, then try right after you boot (i.e. turn on your PC) to press the ESC key - this should bring up the GRUB menu.

Otherwise, you'd have to edit the /boot/grub/menu.lst file, but it would involve booting from the LiveCD, mounting your partition... sheesh!

---

### Post by koulanji on 2006-12-02
So I'm in text mode and guess what I try to reinstall my gdm, and I get this error: 

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or reoved out of incoming. The following information may help resolve the situation:

The following packages have unmet dependencies:
ubuntu-desktop: Depends on xorg but it is not going to be installed
E:Broken packages

Tell me I don't have to reconfigure xorg.

---

### Post by LLRNR on 2006-12-02
What's wrong in reconfiguring your xserver-xorg? You can't get any worse than you are... I think ! Aysiu has an article on what to do if you don't have any means of graphical login... [See here](http://www.psychocats.net/ubuntu/nox).

LLRNR

---

### Post by koulanji on 2006-12-02
re congfigured xorg same problem i can't log into any session and i cant reinstall the ubuntu gdm when I type in sudo apt-get install gdm ubuntu-desktop. 

I get the message that the ubuntu desktop is dependent on xorg, but xorg is not going to be installed

E:Broken packages.

Any suggestions from here. Reformatting is not an option.

---

### Post by LLRNR on 2006-12-02
Nothing positive happens when you```
sudo /etc/init.d/gdm start
```or when you```
startx
```?

---


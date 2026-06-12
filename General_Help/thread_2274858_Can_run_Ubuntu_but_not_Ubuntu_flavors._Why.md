---
title: "Can run Ubuntu but not Ubuntu flavors. Why?"
date: 2015-04-22
forum: General Help
---

### Post by eipapp on 2015-04-22
I have no problems running Ubuntu (14.04) on my machine but when I try to load either Ubuntu Mate 14.04 or Mint Cinnamon 17.1, while they load fine, neither of them will boot up.
I've tried installing Ubuntu Mate as a stand alone OS, but for some reason it won't boot after install. It attempts to run but after a short while just goes to black screen. The same exact 
thing happens when I install Mint Cinnamon 17.1. Yet when I go back to installing Ubuntu 14.04 on the same machine, it works great. 
Anybody have any idea why this would be? I can't rationalize why Ubuntu works and yet two other Ubuntu based products won't. 

Thanks,
Bruce

---

### Post by Impavidus on 2015-04-23
A black screen usually means that it does boot, but because of a broken graphics driver doesn't show anything on screen. Maybe one automatically installed proprietary graphics drivers and the other not? Or automatically added some boot option (like nomodeset)? Some information on your graphics hardware may help.

---

### Post by Bucky Ball on 2015-04-23
You could try with nomodeset first. When you boot from the install media and get to the screen with 'Try Ubuntu' 'Install Ubuntu', etc., hit F6 and choose 'nomodeset'. Proceed. Any different?

PS: As for Mate, we can give you some help with it and it is supported here. As for Mint 'anything', that is not supported on the main forum sections here, although there is a sub-forum for it in 'Other Distro Support'. Mint has a very active community, though, and you should post there to improve your chances of getting support for Mint issues. Good luck. ;)

---

### Post by eipapp on 2015-04-23
This is output from when I checked for additional drivers 
[ATTACH=CONFIG]261489[/ATTACH]

---

### Post by eipapp on 2015-04-23
AMD Radeon HD 7340
When I checked for drivers it said I am using the recommended driver.

---

### Post by eipapp on 2015-04-23
Have to leave the house shortly so won't have time to try your suggestion till later this afternoon. USA-EST (current 7:00 A.M.)
Will let you know how I make out.

thanks,
Bruce

---

### Post by jeremy31 on 2015-04-23
Have you made attempts with Secure Boot disabled?

---

### Post by eipapp on 2015-04-23
Not even sure I know how to do that

---

### Post by pqwoerituytrueiwoq on 2015-04-23
it is a bios setting

---

### Post by eipapp on 2015-04-26
Sorry I've been away so long, has been a very hectic last few days. Anyway, to catch up..........
1.) I tried the suggestion from **Bucky Ball** but was not successful in that I was not able to get any response from pressing the F6 key as he suggested. In fact I couldn't get any F key to respond. 
2.) Disabled Secure Boot as suggested by** jeremy31** and that did not work either. (see below) * 
3.) I reinstalled Ubuntu 14.04LTS which worked, as always, then upgraded to Ubuntu 14.10 and was back to the no boot situation again. What was interesting was that the login screen came up with the obligatory Ubuntu drum roll (there was nothing on the screen I just knew where I was by the drum sound)
indicating, apparently, that the graphics card was not functioning as it should. I gather there is something in the newer releases (Ubuntu 14.10, Ubuntu Mate 14.10) that is messing with my graphics card making the OS essentially inoperable. Does anyone have an idea 
what I can do about that short of replacing my graphics card ? Went back into bios and re-enabled secure boot so that my Ubuntu 14.04 would work properly. 
* when trying to install the OS after disabling secure boot I got the message "The ext file system in partition #1 of SCS/1 (0,0,0) (sda) failed. Failed to create file system" during installation which stopped me cold as I was unable to go any further in the install process. I don't know
if this is of any value but thought I would include it anyway.

---

### Post by Bucky Ball on 2015-04-26
Boot the machine, get to the boot options, choose your kernel but don't hit return, hit 'e' to edit.

Find the line that ends in 'quiest splash' or any combination of one or both those words. At the end of that line, type a space and then 'nomodeset'. It should now look, at then end of the line, like:

quiet splash nomodeset

Follow the instructions at the bottom of the screen to save and reboot. Any different?

---

### Post by eipapp on 2015-04-27
Forgive my ignorance but was not able to find kernel under boot options or to make the change  re:nomodeset.
Is there another way to go about this ? Sorry.............

---

### Post by Bucky Ball on 2015-04-28
When you boot, do you get a screen to select what to boot? A Ubuntu kernel or Windows, if you have it installed? If not, hit shift (or might now be escape) just after boot and that should bring it up. THEN you choose the kernel you want to boot, hit 'e', etc. etc. (see my last post). 

You could boot to the desktop from Live media and change the correct file manually, but let's see how you go with the above first to see if it is going to work to get you in before changing any files permanently ...

---

### Post by eipapp on 2015-04-28
When I boot up I select the esc key which give me the start up menu:

> Continue start up
> system information
> change language

> diagnostics
> boot menu
> computer set up
> system recovery
> network boot
> utilities
> run uefi applications

At this point, I chose "boot menu" which gives me the following:

> uefi boot sources
   Ubuntu
   Windows boot manager
> legacy boot sources
   atapi cd/dvd drive
     sata1
   hard drive
      sata0
network controller

Here I chose Ubuntu but it would not let me do anything other then 
to select it, hit enter and at that point it booted into Ubuntu. 
Could not find a option to edit anything. 
If I hit the esc key while highlighting ubuntu it would again boot into ubuntu.

---

### Post by Bucky Ball on 2015-04-28
Nope, still not getting there. You need the grub menu which will have a list of Linux kernels and the Windows entry, if you have one, to choose from. Doesn't sound like you're getting that list.

So when you finally boot into Ubuntu, same issue? Screen black?

---

### Post by eipapp on 2015-04-28
Could I maybe get there by using "Boot Repair" utility ?

---

### Post by eipapp on 2015-05-05
Hi Bucky,

Got into grub and made the change you suggested re: adding **nomodeset after "quiet splash**", however I could not find a way to [COLOR=#ff0000]**save**[/COLOR] my changes.

These are the only options they gave me at the bottom of the screen:
get help
exit
write out
justify
read file
where is
prev page
next page
cut text
uncut text
cur pos
to spell

How do I save changes to grub in order to see if there are any changes to my system after inserting nomodeset ?

Thanks, Bruce

---

### Post by Bucky Ball on 2015-05-06
This is at the grub menu at boot and NOT the /etc/default/grub file you're changing? For the former, from memory, it should be control+x to save then 'b' to boot, but if you don't have those options showing beneath the boot lines I'm stumped. Try it anyway.

You could try exit and see if it gives you the option to save your changes. Maybe this routine has changed since last time I was there (haven't needed to do this for a few years). ;)

---

### Post by eipapp on 2015-05-06
No, unfortunately it's the etc/defaul/grub file I was referencing was never able to pull up the grub menu from boot. 
With the etc/default........ it says to run sudo update-grub for changes to take affect but when I go back to view it nothings changed. Perhaps I need to re-boot for changes to take ?

---

### Post by Bucky Ball on 2015-05-06
Ok. Got ya. Pull up that file again (make sure you are not pulling up the one from the Live media, if that's what you're booting from) and then:

```
sudo nano /etc/default/grub
```

... and make this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=**"splash quiet"**
GRUB_CMDLINE_LINUX=""
```

... look like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=**"splash quiet nomodeset"**
GRUB_CMDLINE_LINUX=""
```

Hit control+x, then 'y', then, when at a cursor:

```
sudo update-grub
```

Reboot.

PS: If you are tweaking the file from the install media and not from the hard drive, see [here]("http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd").

PPS: I can't remember where you're getting to when you try and boot, but wherever it is, can you hold control+alt and hit F1 and get to a CLI? If so, do the above changes that way.

---

### Post by eipapp on 2015-05-07
Hey Bucky,

I was working on this issue yesterday while talking with my wife and stumbled across the grub menu we've been trying to find in order to add nomodeset to. I made the changes you asked me to but not sure I saved them correctly. I pulled grub again using sudo nano etc and it does not show that my changes took. The problem is a don't remember how I was able to find the grub menu as i was distracted at the time and all my efforts to replicate it have failed, however I'll keep trying and let you know. As they say, even a blind squirrel finds a nut once in a while.

Thanks,
Bruce

---

### Post by Bucky Ball on 2015-05-07
> **eipapp said:**
> As they say, even a blind squirrel finds a nut once in a while.


Ha. I like that. I'm using it. ;)

Well, if you do get there again (maybe check my last post, particularly the link at the end if you're booting from live media to do this), just remember, once you changed the file, and incidentally, only change the bit I show there, nothing else, hold control and hit x, hit 'y' key, then enter. Should be saved.

If you made the changes and they didn't stick I can think of two reasons why: you didn't save the changes with the three steps above, or, you were working from live boot media and you changed /etc/default/grub on that (which would not be saved on reboot of the live media and not saved to disk), or, forgot 'sudo update-grub' after saving the changes and closing the file.

We're getting there hopefully. When we do, I have my fingers crossed it will actually do something that at least gives us a clue if it doesn't give us a fix.

---

### Post by eipapp on 2015-05-07
Bucky,

Ok, was able to get grub menu back but it's very, very tricky. Timing is everything.........anyway, here's my problem:

At the bottom of the screen it lists the following...........

Min EMACS-like screen editing is supported.
Tab list completions.
Press ctrl-x or F10 to boot, ctrl-c or F2 for a command line or esc to discard edits and return to the grub menu

SO, as you can see, pressing ctrl-x boots the machine and does not allow me to save the changes I made. What should I be doing differently to save the changes to the grub menu ?

---

### Post by Bucky Ball on 2015-05-07
Control+x should save and exit so I think you're already there ...

---

### Post by eipapp on 2015-05-07
Then run update grub and reboot ?

---

### Post by Bucky Ball on 2015-05-07
No. Perhaps we should clarify ...

You are booting the machine and getting to the grub options then hitting 'b' to edit one of them? Or are you editing the /etc/default/grub file? If the former, hitting control+x should save the changes (but I remember you needed to hit 'b' to reboot, but maybe not).

If the latter, once you've made the changes, control+x, 'y', return, sudo update-grub, reboot.

---

### Post by eipapp on 2015-05-07
Have now set up a dual boot system with Ubuntu Mate 15.04 alongside Ubuntu 14.04 LTS. On boot it defaults to the Mate, of course, as this was the last OS installed. Unfortunately it will not boot up and I'm back to the black screen again.
If, however, I select the Ubuntu 14.04 it boots nicely and works normally. 
Where do I go from here ?
Sorry to be such a pain.............

Bruce

BTW - I made my changes to the grub menu without resorting to the /etc/default   etc. 
With dual boot set up it should be must easier to get to and edit the grub menu at this point.

Thanks again.

---

### Post by Bucky Ball on 2015-05-07
Ok. Getting somewhere. Just remember, if the nomodeset worked, the changes won't be there on the next boot. You need to change the grub menu then update-grub to make the change permanent. You need to do that in Mate as that is the active grub.

---

### Post by eipapp on 2015-05-08
Ok, did as you said and changed the grub menu in Mate. Also ran sudo update-grub then rebooted. However, I'm still getting the black screen. When I reboot again and check the grub menu (Mate) it has reverted back to the original configuration. The change to nomodeset is not holding after ctrl-x and sudo update. Any other ideas as to what I can do to save changes I make to Mate grub menu ?

Thank you,
Bruce

---

### Post by eipapp on 2015-05-08
As a follow up to my last post, after I make the change in grub to nomodest, Mate does boot which allows me to run terminal and the sudo update-grub command. It's only after I then reboot that I get the black screen.

---

### Post by eipapp on 2015-05-09
Hi Bucky,

I checked the grub menu for my Ubuntu 14.04 and found that it has reverted back as well. Apparently the changes I'm making to the grub menu in both Mate and Ubuntu are not holding. In the case of the Unity desktop it doesn't seem to matter but with the Mate it does.

Bruce

---

### Post by eipapp on 2015-05-12
Hi Bucky,

You had mentioned in one of your earlier posts that "You could boot to the desktop from live media and change the correct file manually". 
Is that still an option or did you already give me directions for doing that and I just missed it ?
The "nomodeset" added to the grub menu seems to work as far as allowing me to boot into Mate but as stated before I can't seem to make the changes permanent
to the grub menu.
Your thoughts please............

Thanks,
Bruce

---

### Post by Bucky Ball on 2015-05-13
To make that change permanent, boot to the desktop, open a terminal and:

```
sudo nano /etc/default/grub
```

Look for this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```

Yours might read 'quiet splash'. That's the line. Make it look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"
```

Hit ctl+x, 'y', enter. Then:

```
sudo update-grub
```

That should be it. ;)

---

### Post by eipapp on 2015-05-13
Well, Bucky, by all accounts everything seems to be working just fine, thank you very much. Getting some funky stuff here and there but nothing I can't live with. Am able to boot into either Ubuntu 14.04 LTS or Ubuntu 15.04 Mate.
So, from my standpoint, problem solved !!
I want to thank you for your help and especially your patience. I can't help thinking that we could have gotten to this point a lot sooner had I not made so many misinterpretations and screw ups along the way. 
You've been a saint. 

Thanks again,
Bruce

---

### Post by Bucky Ball on 2015-05-14
A pleasure. All part of the learning curve. Enjoy. :)

---


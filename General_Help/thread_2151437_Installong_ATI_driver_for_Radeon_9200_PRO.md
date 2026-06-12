---
title: "Installong ATI driver for Radeon 9200 PRO"
date: 2013-06-04
forum: General Help
---

### Post by xp15 on 2013-06-04
Hello everyone. I have a problem learning how to install this driver.
I thought to download from the said but running it faild, and I did as said here: [http://ubuntuforums.org/showthread.php?t=1541719](http://ubuntuforums.org/showthread.php?t=1541719)

My problem is screen tearing, in many flash videos. HTML5 works good, but also have a little bit this screen tearing, and got stuck sometimes (maybe only loading).
I run this video in full screen 720p in HTML5 for example: [http://www.youtube.com/watch?v=BmHZtCMlTTY](http://www.youtube.com/watch?v=BmHZtCMlTTY)

I run this flash video: [http://www.youtube.com/watch?v=BmHZtCMlTTY](http://www.youtube.com/watch?v=BmHZtCMlTTY) 
and It worked pretty fine, the screen tearing is not so noticeable, but I just looks for it so I see it ^^ .
well, tried this video: [http://www.youtube.com/watch?v=rYEDA3JcQqw](http://www.youtube.com/watch?v=rYEDA3JcQqw)
the 720p didn't run so good (pretty heavy ^^) and also the 1080p ofcorse. I tried the 480p full screen and so my screen tearing on the door and on her face many.

I run also this, from vimeo: [http://vimeo.com/44420219](http://vimeo.com/44420219)
and while the video quality is not HD, I can pay attention more to the screen tearing (on both youtube and vimeo).
also watch this movie again: [http://www.sockshare.com/file/P3I0E9M80DCK8K#](http://www.sockshare.com/file/P3I0E9M80DCK8K#)
and there are screen tearing.

How can I improve the performance of my graphic card and the graphic in general? is there any driver? maybe changing the refresh rate as mentioned here?: [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing)

In short, I need a driver or any way to improve the performance of my graphic card and the pc.
Is there a good guide with up-to-date commands? a guide for ATI Radeon 9200 PRO?

Thanks!

EDIT: I also have a feeling that the open-source driver isnt working well, how can I install/reinstall it?
And I got some dependencies errors:
 xserver-xorg-video-ati : Depends: xorg-video-abi-11
                          Depends: xserver-xorg-core (>= 2:1.10.99.901)

and some more I saw. any suggest? should I post more info? if do, how? which?

---

### Post by ajgreeny on 2013-06-04
The only driver for that card is the one you already have, ie, the open-source ati/radeon driver.

The proprietary driver for that card was discontinued a long time ago, 2006 or 2007, I think, and there is no point in trying to get anything better than the one you have.  If you try to install fglrx from the repos it will not work, and may make things worse than they are now.

My old machine had the ATI 9200SE card which worked reasonably well, but could not run unity properly, so I wonder what DE you are using and which version of Ubuntu.

---

### Post by xp15 on 2013-06-04
> **ajgreeny said:**
> The only driver for that card is the one you already have, ie, the open-source ati/radeon driver.

The proprietary driver for that card was discontinued a long time ago, 2006 or 2007, I think, and there is no point in trying to get anything better than the one you have.  If you try to install fglrx from the repos it will not work, and may make things worse than they are now.

My old machine had the ATI 9200SE card which worked reasonably well, but could not run unity properly, so I wonder what DE you are using and which version of Ubuntu.

Thanks. can you tell me however how to reinstall the open-source? couldn't find a lot of information. I think I broke the driver, and wanna be sure I can safely reboot and get a desktio again.

Also, saw this: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options)
I understand there are another open drivers, and though some are not more active, thay may be just good for my card. what can you tell me about those options?

Thanks!

---

### Post by ajgreeny on 2013-06-04
You can try reinstalling the **xserver-xorg-video-ati** and **xserver-xorg-video-radeon** but I don't think it will make any difference, I'm afraid.

The catalyst driver is not a possibility for that card.

---

### Post by xp15 on 2013-06-05
> **ajgreeny said:**
> You can try reinstalling the **xserver-xorg-video-ati** and **xserver-xorg-video-radeon** but I don't think it will make any difference, I'm afraid.

The catalyst driver is not a possibility for that card.

OK, thanks.

what about this one: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
is that the one who doesnt working?

what about the other drivers I gave in this line?: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options)

Maybe I can fix the screen tearing in other ways? Hsync, Ysync, refresh-rate?

---

### Post by Mark Phelps on 2013-06-05
What version of Ubuntu are you running? Apologize if you already mentioned that, but I didn't see it in your posts.

As to your latest set of questions:
1) NO -- you can't just go installing the fglrx driver.  Any recent version will NOT work with your card.
2) Maybe -- depends on what version of Ubuntu you are using.  Those instructions only work for specific Ubuntu versions.

---

### Post by xp15 on 2013-06-05
> **Mark Phelps said:**
> What version of Ubuntu are you running? Apologize if you already mentioned that, but I didn't see it in your posts.

As to your latest set of questions:
1) NO -- you can't just go installing the fglrx driver.  Any recent version will NOT work with your card.
2) Maybe -- depends on what version of Ubuntu you are using.  Those instructions only work for specific Ubuntu versions.

Ubuntu 12.04 LTS (also installed now lubuntu 13.04 for trying performence, but It seems that a new ubuntu 12.04 LTS will be better, or maybe it is just psychologic).
Can you direct me to a good way? a good chance? which open driver in the link I gaved mat work good?

---

### Post by Mark Phelps on 2013-06-06
> **xp15 said:**
> Ubuntu 12.04 LTS (also installed now lubuntu 13.04 for trying performence, but It seems that a new ubuntu 12.04 LTS will be better, or maybe it is just psychologic).
Then, as indicated in the instructions, since those are for Oneric, they will NOT work for you.

Unfortunately, you have a very OLD video chipset -- and video driver writers simply stop writing new drivers after a while.

When you install Ubuntu, it will install the default Radeon driver.  IF that doesn't work, you are out of luck. Sorry.

---

### Post by xp15 on 2013-06-07
But oneiric is the first version before 12.04 LTS. I know that commands are the same. So what won't fit to my system?
Thanks.

I still think to try some of the open-driver, to check what I can do with them. To at least try them.

---

### Post by mastablasta on 2013-06-07
removing AMD fgrlx driver:
> 
[LIST=1]
[*]
Remove/purge current fglrx and fglrx-amdcccle (If you have used a method outside of aptitude, apt, Software Center or Synaptic, follow the other party's instructions for removal): 
sudo apt-get remove --purge fglrx fglrx-amdcccle
For some users, the fglrx-updates and fglrx-amdcccle-updates packages do not work. If you attempted to install them, also do: 
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
[*]Reboot.
[/LIST]




or here: [http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand](http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand)


> **xp15 said:**
> But oneiric is the first version before 12.04 LTS. I know that commands are the same. So what won't fit to my system?
Thanks.

because you have a very old GPU. the only way to make it work better is to get a newer GPU with propper support or to replace the CPU with something really strong (eventhough this might not solve it)

to have the drivers working you would have to install a very old version of Ubutnu from 2007 that is not supported anymore (i.e. not patched so you would be vulnerable online). that version will also have difficulty installing modern up to date programmes.

> 
I still think to try some of the open-driver, to check what I can do with them. To at least try them.

as mentioned opensource driver is the driver that is installed by default. so when you install the OS you see a desktop. that desktop and all you see is provided by the opensource driver.

you could tray adding xorg edgers PPA though i doubt it will help. unless they fixed some bugs but i am not sure how much effort are they putting into these old chips.

---

### Post by xp15 on 2013-06-09
OK, thanks. I found this thread earlier: [http://ubuntuforums.org/showthread.php?t=1701563](http://ubuntuforums.org/showthread.php?t=1701563)
And DRICONF program (with S3TC something enabled) Plus adding the PPA of [COLOR=#000000]xorg-edgers (as you too says) and running "sudo apt-get update" sp the "Update-Manager" jumped and showed me like 40 updates ^^.

I knew this xorg-crack something before, but never new how to install it. Now I know that this PPA can be just added and the [/COLOR][COLOR=#000000]"Update-Manager" will give me everything. Am I right? or there is maybe a command to install it? Have I done it right?

Thanks! and I shared my solution so if someone see it he will know a good way to solve it. Basicly, I would like to have still a better performance if I can, I still have flash and videos "screen-tearing" but very few, and little.


[/COLOR]

---


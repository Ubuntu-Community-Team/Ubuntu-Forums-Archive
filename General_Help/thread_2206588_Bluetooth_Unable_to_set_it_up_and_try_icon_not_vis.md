---
title: "Bluetooth: Unable to set it up and try icon not visible"
date: 2014-02-19
forum: General Help
---

### Post by viriatovigo on 2014-02-19
Sorry but after some updates my Ubuntu 12.04 went on holidays for long time. Just yesterday, in the end, morgaes, Bucky Ball and mastablast did manage tomeke me install Ubuntu 13.10 overriding 12.04 for good.

The 13.10 is brilliant and looks ad works nearly 90% as Apple Maverick, with menus easy to use. 

But still I can’t set up the Bluetooth to pair my mobiles phones and  my wireless keyboard.

In the past were truing to help me Linuxisfast, ClientAlive and dragonfly41, but I am too thick and I didn’t manage to solve the problem. Sorry all of you for wasting your time.

The situation is the same than before:

I am trying to set a wireless keyboard through a bluetooth USB adapter. The wireless mouse that comes with the keyboard did start working straight away but the keyboard needs to be paired and input a code. 

The bluetooth tray icon is not visible and going into Systems Settings > Bluetooth the window is greyed so cannot be used. Also in the greyed window can be seen that the “Bluetooth” and “Visibility” are “OFF”.

For the same reason I can't pair my mobile phones Samsung GT-S3650 and the HTC Nexus One.

I the Bluetooth window there is nothing in the bottom, just before someone says "go to the instructions in the bottom of the window".

Please, help. Thank you.

---

### Post by deadflowr on 2014-02-19
Post the output for 
```
lsusb
```
We'll start simple.

Perhaps, more robust variants of this command will be needed later on...

---

### Post by viriatovigo on 2014-02-20
Good morning and thank you deadflowr,

Here are the outcome:

vigo@vigo-X50V3:~$ lsusb
Bus 001 Device 004: ID 04f2:b351 Chicony Electronics Co., Ltd 
Bus 001 Device 008: ID 0e8d:1806 MediaTek Inc. Samsung SE-208AB Slim Portable DVD Writer
Bus 001 Device 007: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 276d:1105  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
vigo@vigo-X50V3:~$

---

### Post by viriatovigo on 2014-02-27
2 weeks ago  olipoh1 did start a thread "13.10 bluetooth problems (no try icon)" with siilar problem and he/she didn't get any answer. It seems that, so far, the problem has not solution. I suppose that is matter of time... I will seat with a case of Guinness watching video films on the net...
And I can see that the problem comes since the 20th of June 2008...

---

### Post by viriatovigo on 2014-03-14
New misterious mistery of Ubuntu...

I've got fed up of Ubuntu 13.10 and I did install 12.04 in other PC (because is impossible to uninstall any Ubuntu once installed, as I can see in other posts, so not only is happening to me) and the Bluetooth icon did show up automatically in the menu tray in the top right side and it is working without problems as used to be, and the Bluetooth window is not greyed and is "ON" as well as Visibility. Why on Earth is greyed and cannot be used in Ubuntuy 13.10 and there is not way to do anything with it?

Also in Ubuntu 12.04 do shows up the very useful "Workspace Switcher" that has disappeared in Ubuntu 13.10. Why?

---

### Post by Doug S on 2014-03-14
> **viriatovigo said:**
> Also in Ubuntu 12.04 do shows up the very useful "Workspace Switcher" that has disappeared in Ubuntu 13.10. Why?Workspaces are disabled by default on 13.10. I don't know why. They can be enabled by going to "System Settings" - "Appearance" - the "Behavior" tab - click "Enable workspaces".

---

### Post by viriatovigo on 2014-03-14
Ta Doug S.

It did work. Thank you.

It is funny... It seems that Linux is doing the same than Microsoft: Every new version has less goodies than the one before... For instance now in 12.04 I can't connect the wireless router as before, I can't install the webCam as before, etc.,etc, etc., always "Ubuntu has encountered a problem...".

Have a nice day.

Tino

---

### Post by viriatovigo on 2014-12-21
Hallo there.

[FONT=arial]Sorry, I have been out of the net for awhile due to health problems.

Still I can't switch on bluetooth becuse, as I said in the beginning and I did post the screenshot, the window is greyed and does nothing. I can see that deadflowr did not answer to my outome to my lsusb input. I have now Ubuntu 14.4 and the problem remains. Following the advise to someone elso I did [/FONT][FONT=arial]sudo rfkill unblock bluetooth and before the **Exist 0 **I did write what they said with not avail at all.[/FONT] 

Please,help

---

### Post by viriatovigo on 2014-12-22
I can see that tis is a recurrent issue since long time ago that seems that has not solution:

 			 				 				 					 						 	[**[COLOR=#000000]chunky bacon![/COLOR]**]("http://ubuntuforums.org/member.php?u=1221527") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						5 Cups of Ubuntu 					 					 						[IMG]http://ubuntuforums.org/images/rank_2.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateJan 2011Beans39DistroUbuntu Development Release 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: Can't turn on bluetooth module on my latptop[/h] 		 				 				 					 				 		 			 				[INDENT] 					I made the apparent mistake of turning off bluetooth once, and now I can't turn it back on, either.  

Dell Vostro V130 laptop that came preinstalled with 10.04. There is no  Windows install for me to fall back on, unfortunately.  Everything was  fine out of the box until I made the silly mistake of not knowing I was  going to break everything simply by trying to save power.  Up until  then, I had been bragging to so many friends on how nice it was for new  linux distros to have everything working like it should, right out of  the box.

I've installed blueman.

I've done the edit of /etc/bluetooth/main.conf RememberedPower = false

uninstalled everything bluetooth related and reinstalled.
sudo /etc/init.d/bluetooth restart
sudo /etc/init.d/bluetooth start
sudo /etc/init.d/bluetooth stop


nothing, zilch, nada.  i get the indicator, but it will forever say  "bluetooth needs to be enabled." you click "enable," and get "the  connection timed out."

and every bug I see that deals with it says "yes, its broken."

I guess bluetooth is just a no-go for most folks in linux.

That being said, since Ubuntu is so user friendly, there should be a  huge gigantic warning the first time you try to turn bluetooth off.   Something like "YOU WILL NEVER GET IT BACK NO MATTER WHAT YOU DO.  ARE  YOU SURE YOU WANT TO DO THIS?" 				

So, Bluetooth doesn't work with Linux. Thank you anyway. I know it now and, since have 2 more PCs with different OS I will work Bluetooth in them.

All the best.
[/INDENT]

---

### Post by viriatovigo on 2014-12-27
Well... That's it. I understand now why Linux is only used by a 6% of the market: It is useless for business.
 

 Nothing works and nothing has a solution. After scrolling this forum I can see that practically all the issues that I am having are running since 2009/2010 without solution at all.
 

 The Bluetooth can't be set on because the screen is in grey and nothing respond so it is not possible to download anything from my mobiles, for the same reason I can't par the keyboard, The screen saver has a mind of its own and can not be done anything because whatever I do returns to the same position again and again and keeps opening the screen saver on spite of choosing “never” and requesting my password on spite of not being tick “password required”, and the same a lot of things.
 

 Everyone that asks for a solution gets a response like “open that and click on that, if this is not working open the terminal and write 'whatever' and if this doesn't work either then write 'another whatever' and if this doesn't work again then write once more 'another different whatever'”  and like that for hours “ab eternam” because nothing works at all... just the ideal to resolve something on the spot when in the other side there is a customer waiting.
 

 Ending this post I going to put this PC for sale in eBay because is useless since once any Linux OS is on it there is no way to uninstall it unless you take the HDDo ut (because Linux doesn't allow to format it) and put it through a degauss unit as can be read I other posts on the forum.

 

 Linux go to hell.

---


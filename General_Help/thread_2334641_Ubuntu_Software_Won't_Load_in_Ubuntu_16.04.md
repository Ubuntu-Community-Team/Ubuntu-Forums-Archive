---
title: "Ubuntu Software Won't Load in Ubuntu 16.04"
date: 2016-08-21
forum: General Help
---

### Post by Mike_Andrews on 2016-08-21
Can't get Ubuntu Software to load available new packages. Have consistently updated Package Manager via Synaptic but still, no dice.
I get this message in Terminal:

(ubuntu-software:5696): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:5696): GsPlugin-WARNING **: could not lookup cached macaroon: Error calling StartServiceByName for org.freedesktop.secrets: Timeout was reached

. . . All software up to date :?

---

### Post by chileno35 on 2016-09-08
Hello,
i have the exact same problem. When i click the Ubuntu Software icon it opens and shows that there is 1 Update available but the cursor is only spinning around and nothing happens.
When i start the Ubuntu Software from the Terminal i got this message:
(ubuntu-software:22031): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

Any hints what to do?

---

### Post by chileno35 on 2016-09-08
I have a solution that worked for me:

Kill the process "gnome-software" and then Ubuntu Software is working properly again. :popcorn:

---

### Post by Mike_Andrews on 2016-09-08
[**[COLOR=#000000]chileno35[/COLOR]**]("https://ubuntuforums.org/member.php?u=1914390") 	 
 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]  					 					 						First Cup of Ubuntu 					 					 						[IMG]https://ubuntuforums.org/images/rank_1.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateApr 2014Beans5 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: Ubuntu Software Won't Load in Ubuntu 16.04[/h] 		 				 				 					 				 		 			 				[INDENT] 					I have a solution that worked for me:

Kill the process "gnome-software" and then Ubuntu Software is working properly again. :popcorn:
-------------------------------------------------------------
Chileno35,
Thanks for the leg up. 
Can I use Synaptic for this chore or is it a task strictly for Terminal?
. . . Took me a while to reply; just did a complete reinstall of Ubuntu with no backup.
Deja-dup doesn't work for me.
Come back?
[/INDENT]

---

### Post by howefield on 2016-09-09
> **Mike_Andrews said:**
> Can I use Synaptic for this chore or is it a task strictly for Terminal?

Load up System Monitor and look in the *Processes* tab.. highlight the one you want and click the *end process* button.

If you want to use the terminal, try

```
ps aux | grep "whatever_you_want_to_search_for"
```

and using the PID number, kill it with..

```
kill PID_number
```

---

### Post by chileno35 on 2016-09-09
I killed the process from the taskmanager. In German it is the "Systemüberwachung" where you can see cores of your computer, RAM and the Tasks that are already running.

Killing processes from the terminal is new for me, so i prefer the way from the GUI :-)

---

### Post by Mike_Andrews on 2016-09-09
Thanks to Chileno35 and Forum Admin Howefield for the good vibes. . .

As it turned out I did use Synaptic to simple-remove gnome-software, and in its place by typing in the search term, 'ubuntu-software' I hit the lucky bingo.

Now my system has a Unity toolbar icon named 'Software' in the same place as the old icon named Ubuntu Software, but it is different. It now allows me to search for software dedicated to Ubuntu. Is there an oxymoron contained in this somewhere?[B][COLOR=#000000] 

[/COLOR][/B][COLOR=#000000]I have no idea why ubuntu-software konked out on us like it did, Chileno35; the software I deleted was the program originally installed from disk.
[/COLOR]
But as the old saying goes, 'all's well that ends well.'

Thanks again to all

---

### Post by crankyoldbugger on 2016-09-17
this worked for me as well.  +1 for chileno35

---

### Post by Mike_Andrews on 2016-09-17
Since the jury still seems 2 B out regarding a permanent fix for this annoying little glitch please let me make a few conjectures pertaining to solutions I've come up with and the reasoning behind them.

For one, I use BleachBit, running it from Terminal with Deep Scan enabled. Although I have been at a loss to locate any mention in BleachBit's log of AppStream and/or ubuntu-software/gnome-software, I nonetheless must recognize that in other cleaning prerogatives one must exercise caution in BleachBit's presets to avoid deletion of needed things. I confess to destroying my system once because I added the WRONG FILES to BleachBit's Additional section. BleachBit is extremely efficient at what it does.

. . . I have no evidence to substantiate my gut hunch that unless setup dead-letter perfect, BleachBit CAN CAUSE the ubuntu-software issue. I hope I'm wrong, but a more definitive analysis could be obtained by polling the number of individuals having this problem who are also running Bleachbit. I don't believe in dejavu again but I do believe in Einstein's Theory of Relativity.

I like Synaptic PM and find myself using it frequently, because it functions flawlessly and never hangs the way (ahem) other software installation/removal methods in Ubuntu sometimes do. *Often *do. Fixing the ubuntu-software glitch via Synaptic, then, has come to be a fairly standard chore involving my time several days a week, so that I've gotten some seat-of-the-pants remedies down pat while still lacking more than a vague clue as to what could be the underlying cause. And I should say that if Bleachbit IS the cause it's likely because other parts of the system are not playing by the rules.

As already revealed via other links the issue was disseminated in March, 2016 by experts whose investigation revealed that a certain amount of bad code is getting injected SUPERFLUOUSLY into the ubuntu-software data stream and I say this could be poignant in lieu of the known (but as yet not fully patched) TCP exploit to which Linux is susceptible. 

At any rate and with all bets still off, when the anomaly occurs these are the things I have found effective in restoring ubuntu-software connectivity:

1) Using Terminal, code: sudo apt update && sudo apt upgrade && sudo apt install
I haven't been removing ubuntu-software/gnome-software initially as otherwise recommended, but if it makes you feel good, go 4 it!

Reboot

2) Code: sudo apt install ubuntu-software

3) Reboot again and check to see if ubuntu-software appears in a Unity search.

. . . If not, sign in to Synaptic and type ubuntu-software into a search. If it doesn't list any results ubuntu-software has somehow been removed from your system. Hit Reload so that Synaptic can retrieve the latest package, then run the Synaptic installer.

Reboot.

Open a Unity search and type ubuntu-software into the search bar. You should now see the latest ubuntu-software icon appear as an orange shopping bag. If you want it in your Unity Dashboard simply drag 'n drop, and you're back in business.

4) For many years it has been my policy to disconnect the WAN cable from a machine while I'm away. Doing so is not problematic and removes your bacon from the reach of any wolf with an exploit. You never know; why not play it safe?

Having so said I am forced to admit that sometimes, when I return and hurriedly renew my work effort I forget to RECONNECT the DSL. It's a small OOPSIE but distracting. (It is said that if one can remember the word Alzheimer's he doesn't have it). Pink thositive.

But if this has happened 2 U, consider as I have that attempting to access a WAN destination while OFFLINE may -- I'm not saying it definitely does, but it may -- cause a problem with desktop-manager and Unity (I'm guessing) so that the latter have sections of code somehow getting overwritten, thus preventing system recognition of ubuntu-software/gnome-software functionality via app-stream, causing poor, confused Ubuntu to go off on a wild tangent thinking it 'lacks permission.'

And. . . this is where 1, 2 and 3 above come into play. N'est pas?

Just between you and watashi I've UN-ticked the box in BleachBit/System for Broken Desktop Files, although Autoclean and Autoremove are still functional in BleachBit for now. Fingers. Crossed.

As to my personal litany of cosmic potentials lying within the mundane reach, my ballpark guess would be that the Ubuntu Development Community will eventually issue a permanent cure for the ubuntu-software bug. But until that halcyon moment arrives we can continue getting by via seat-of-the-pants wit and no small degree of dedication. 

Thanks, crankyoldbugger for your input.

M.

---


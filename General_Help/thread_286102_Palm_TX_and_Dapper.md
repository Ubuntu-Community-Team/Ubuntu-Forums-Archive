---
title: "Palm TX and Dapper"
date: 2006-10-27
forum: General Help
---

### Post by anti-net on 2006-10-27
Hello, I was wondering if anyone has had any issues or sucess with syncing a Palm TX with Dapper, if they've had sucess and are able to point me in the the directon of syncing it problem free, rather paranoid about my palm buggering up as it has a lot of information I need. 

Thanks, Greg

---

### Post by distortedstar on 2006-10-27
I also own a Palm TX, and I've been successful syncing with the Jpilot program. Make sure you enable all repositories so you can download it.

The only quirk I've found is that I have to press the sync button on the palm/cable first, then sync in jpilot. 

I've been nothing but unsuccessful with gnome-pilot and kde-pilot, so I don't know how to get to sync with evolution and/or kontact/korganizer.

---

### Post by megamania on 2006-10-29
> **distortedstar said:**
> I also own a Palm TX, and I've been successful syncing with the Jpilot program. Make sure you enable all repositories so you can download it.
I had given up using Jpilot with Dapper, because:
- I kept getting a segmentation fault error
- I could only connect via wireless

For these reasons, I had to stick to the pilot-xfer suite. I needed to setup an "exclude" file in order to skip the bigger files which caused a segmentation fault, but besides that everything worked fine.

Now that I made a clean install of edgy, I decided to give jpilot a new try.

It connects wirelessly (I haven't tried with the usb cable) and starts syncing. After a while, however, it stops syncing and the palm apparently freezes (i.e. after a few minutes I have to warm-reset it)
This usually happens when syncing one of these files, which are subsequent: BGCache-PDat, Disko.mp3, Lamasbonita.mp3 or BGCache-lnch. So the weird thing is that it doesn't always stop on the same file.

Has anybody experienced the same problem? Does anybody have a suggestion? The dream of syncing my Palm with jpilot is becoming a nightmare...

---

### Post by Daliz on 2006-10-29
I couldn't get my Zire 72 to sync with Dapper at all. It worked well in Hoary, using JPilot, but in Dapper I never got it working. I just upgraded to Edgy, and guess what? It works again, very easily, with gnome-pilot and JPilot. Not a really helpful reply but just to let you know :D

---

### Post by wastrel on 2006-10-29
USB sync is broken in Dapper (apparently due to USB issues with the kernel). 

This is all fixed in Edgy with kernel 2.6.17 (yay!!!)  Now I can sync reliably again.  Try USB sync again if you're in Edgy & wifi sync isn't working.

---

### Post by megamania on 2006-10-30
> **wastrel said:**
> Try USB sync again if you're in Edgy & wifi sync isn't working.

Can you tell me what device name you used for usb sync?

---

### Post by wastrel on 2006-10-30
> **megamania said:**
> Can you tell me what device name you used for usb sync?

I use /dev/pilot  -  but this requires a little explanation.

This /dev/pilot link is created by the kernel's usb device subsystem (udev) when you plug in your palm and press the hotsync button on the palm side.

If /dev/pilot doesn't work for you it may be because the link is created pointing to the wrong USB device.  In my case I had to change the udev rule for creating /dev/pilot because the default /dev/pilot always pointed to the 2nd USB device, and my clie seemed to want to sync with the first USB device.

For the record, I changed the udev rule in  /etc/udev/rules.d/60-symlinks.rules  , on line 22 to read:

KERNEL=="ttyUSB[02468]", SYSFS{product}=="Palm Handheld*|Handspring *", \

The original read  "ttyUSB[*]" instead of "ttyUSB[02468]"  

I've been meaning to file a bug about this but haven't gotten around to it.  

Anyway, this change makes /dev/pilot point to the first of the 2 USB ports that are created when the palm sync button is pressed, instead of the second.

This fixed /dev/pilot for my case.  (If you do change system files, please make a back up copy of the original in case you mess things up :).

Remember this is on Edgy - I don't know & can't comment on how udev is set up for /dev/pilot on Dapper.  

Good luck!  Let us know if you get it working.

---

### Post by megamania on 2006-11-01
> **wastrel said:**
> I use /dev/pilot  -  but this requires a little explanation.
[...]
Good luck!  Let us know if you get it working.
Thank you VERY much for your suggestions. Although I didn't change the file as you suggested, your thoughts helped me find a way to sync my TX with jpilot again.

So, to sum things up for people who are having the same problem, here is my experience:

[LIST]
[*]I'm using Edgy and a Palm TX
[*]Wireless sync (through a router) starts but freezes when it is close to the end (see my previous posts)
[*]Cable sync works by setting **/dev/ttyUSB1** as *serial port* in the *File->preferences->settings* dialog
[/LIST]
I needed a few tries before getting it to sync. Looks like I have to press the sync button **on the palm** first, and then press the **jpilot** sync button.

I'm still curious as to why wireless sync hangs with jpilot while it works perfectly with pilot-link though.

---

### Post by fragos on 2006-11-02
The Palm button is first and then I wait for the Palm to say connecting before clicking the jpilot sync button.  That always worked.

---

### Post by helmut_hed on 2006-11-20
Palm sync via USB now works consistently for me... but only after kernel hacking.  I reported a bug on Dapper;  hopefully they'll accept the fix (which is present in later kernels such as in Edgy).  More info here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39518](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39518)

What's happening is the kernel bug triggers a segmentation fault in the syncing application (whichever one you have) and leaves the USB data in an inconsistent state (which is why sometimes you see the USB2/3, USB4/5, etc. in addition).

Cheers,
Jeff Trull

---

### Post by gyffes on 2006-11-30
For those struggling (STILL) with syncing their palm with their ubuntubox, I offer this bit of hope:

> **megamania said:**
> 
to sum things up for people who are having the same problem, here is my experience:

[LIST]
(stuff cut)
[*]Cable sync works by setting **/dev/ttyUSB1** as *serial port* in the *File->preferences->settings* dialog
[/LIST]


This WORKED for me on Dapper with my Clie' (NX80) via USB.

The key, it seems, was changing the /dev/ttyUSB1 setting in jpilot's preferences. It HAD read USB0 -- the moment I changed it, I was syncing.

In fact, I only needed to press HOTSYNC on the palm for it to sync, not the dual-part pressing others have described.

I'm astonished that I finally managed to install new files onto my palm after weeks of frustration, but it's working.

Good luck!

---

### Post by twrock on 2006-12-02
I have something resembling success syncing a Palm TX with Dapper. I simply opened Evolution, clicked Edit>Synchronisation Options... and followed the directions. I also added the Pilot Applet to my Panel.

My current settings in gnome pilot are: Cradle /dev/pilot 57600 USB.
I have only the Address, Calendar, Memo, and Todo conduits enabled. (I use Backupman on the Palm to keep my TX backed up to my SD card, so backup to the desktop is not critical for me.) 

I have to say that periodically things go wrong. Either there is not recognition that the hotsync has attempted to start (no musical beep) or things hang when trying to identify the user. This seems most often to happen when I have run Evolution, and either hotsync while it is open or after I have closed it. But I've gotten things to work much better than the "single time hotsync and then never again" problem the last time I tried to get things going.

Incidentally, the solution that I have found when things hang is to start the System Monitor (System>Administration>System Monitor) and kill gpilotd and gpilot-applet and then re-add the Pilot Applet to the Panel. That seems to get things going again. So that is probably also what you would want to do to restart the setup process. (Kill both, start Evolution, run the Synchronisation Options, and then add the Pilot Applet to the Panel.)

Now, I can almost guarantee that YMMV, but that is working relatively well for me at the moment. Good luck.

---

### Post by twrock on 2006-12-03
Ok, I'm back. I decided to take the advice of some others and move up to Edgy. The short story is that I have a very consistently working hotsync between Evolution and my Palm TX via gnome-pilot in Edgy. Edgy has a few other problems that I will work on solving, but it is nice to get this big one out of the way (knock on wood). So if you are interested, below is the long, drawn-out version of what I did, step by step.

___________________________________________________

Report on my process of getting a Palm TX to hotsync with Evolution via gnome-pilot in Ubuntu Edgy Eft (6.10):

After installing Edgy and completing the first update, I decided to try to get my Palm TX hotsync working. These are the steps I took.

(Background note: My install of Edgy was "clean"; I formatted all partitions so no configuration information was carried over. During my install of Edgy, I had my Palm TX plugged into the original Palm hotsync cable. I doubt that mattered at all, but I'm trying to make this as accurate a description of what I did as possible.)

After installing Edgy, I ran Evolution for the first time. I set up a default email account, but I did not check email or do anything else. I closed Evolution.

I then started the Palm OS Devices configuration by clicking System> Preferences> PalmOS Devices. I then just went through the menu prompts as follows:
   Device Settings:
      Name: Cradle
      Type: Changed to USB
      Timeout: 2
      Device: /dev/pilot
      Speed: 57600
   PDA Identification: "Yes, I've used sync software with this PDA before."
   Initial Sync: Put the PDA in the cradle (actually, just connected the cable) and pushed hotsync button. 
      Results: Successfully retrieved Owner Name and ID from PDA.
               Owner Name: *** ******** (my PDA username)
               PDA ID: 3837
   PDA Attributes:
      Name of PDA: Palm TX
      Local folder: /home/ron/Palm (I had already created this folder manually, so I don't know what would happen if I hadn't.)
   Success (I clicked "Apply")

gnome-pilot Settings popped up. Under the Conduits tab, I enabled the following:
   Backup (the directory was already set; I clicked "Remove local base if deleted on PDA")
   eAddress
   eCalendar
   eMemos
   eToDo
   Expense (I set the directory to /home/ron/Palm/Expense which was a folder I had already created.)

   NOTE: I also set all "One time action:" to "Copy from PDA" and checked "Sync Private Records" in each item I had enabled (that had that as an option).

I closed gnome-pilot.

I hit the hotsync button on my Palm cable. I heard the musical beep, and the hotsync began. Nothing popped up on my computer screen at all; the only indication that anything was happening was that I could see on the PDA screen that things were synchronizing. It took some serious time to back up all my Palm apps (I have a lot of apps and data!).

SUCCESS!!!

However, interestingly, my "Expense" folder was somehow moved into a newly created folder named "del". I don't know where it came from nor why "Expense" was moved there.

I opened Evolution. I clicked on the "Contacts" tab and I got an error message saying that Evolution was not able to access its data file. Calendar, Memos, and Tasks were all there just fine. I closed Evolution and reopened it. Still no Contacts, but everything else was still fine. I closed Evolution.

I reopened PalmOS Devices (gnome-pilot Settings). I clicked on the Conduits tab and set the "One time action" in eAddress to "Copy from PDA". I closed gnome-pilot Settings. I hit the hotsync button on my cable. My Palm TX tried to start a hotsync and quickly did a reset. Bummer! I waited for it to reset. I again hit the hotsync button. It started to hotysync. This time the hotsync went much quicker.

I opened Evolution. Success! My Contacts were all there. I closed Evolution. I wanted to test to see if opening and closing Evolution would affect gnome-pilot negatively in Edgy as it had in Dapper.

I hit hotsync again. Again the sync was successful and as quick as the last time (maybe slightly quicker because it didn't have to sync all those addresses).

I opened the file browser to have a look at my Palm folder again. What's this? The Expense folder has returned and has files in it. The same files are still in the /Palm/del/Expense folder. Hmmm, I don't know what's up with that, but I don't think it is a problem. At least it is there, not gone.

I made a minor change to a record in each of my main PIM apps and tried to sync again. It sync'ed.

I opened Evolution and verified that all the changes had synchronized. They had, and there the Expense entry showed up in the Expense folder as well.

I made a change in a Contact in Evolution and started another hotsync with Evolution open. It sync'ed again, but the changed Contact did not seem to change (I had changed the "File under" only, so maybe that doesn't really sync across). I made a more significant change (Country) and synced again. This time the change did get sync'ed over. Looks good!

I closed Evolution and hit hotsync again. Success.

I restarted the gnome desktop (Ctrl-Alt-Backspace). Hit the hotsync button. Nothing. Started Evolution. Hit the hotsync button. Nothing.

Right clicked on the bottom panel and added Pilot Applet to the panel. Hit hotsync. The "gnome-pilot progress" dialog popped up, and for the first time ever (including when I was using Dapper) information about the progress was displayed in the window. Great!

Opened Evolution. Hotscyn'ed. Success.

Closed Evolution. Hotsync'ed. Success.

Restarted gnome desktop. Pilot Applet was still in the panel. Hotsync'ed. Success.

At this point, I have done multiple hotsync operations with Evolution both open and closed. I have made data changes and verified that they sync'ed. I think I have a consistently working Palm TX synchronization.

So, if synchronization is a critical function for you and you are having problems in Dapper (or earlier versions), you might seriously consider an upgrade to Edgy. However, I should emphasize that I did a complete install of Edgy from scratch (reformatted all partitions).

YMMV. Good luck.

Edit: I later increased the speed from 57600 to 115200 and saw no apparent problems.

---

### Post by fragos on 2006-12-03
Thanks for the detailed discription of the steps you took.  All your hard effort has apparently turned into a working pairing of Ubuntu and your TX.  The result unpredictability of some of your steps is still a little scary.  In my personal attempt to get my E2 to sync the user ID on my Palm was destroyed and changed to gibberish.  All of my purchased Palm aps started nagging about registering which was now impossible because my original ID was gone.  I ultimately found a bit of Palm software that allowed me to set the name and all has returned to normal.  Although I wish to sync with Evolution I'm still hesitent.  Your results make me hopeful but still not confident enough to try again.

---

### Post by djcrash1981 on 2006-12-10
Hi to all, i been looking this post a lot of times trying to find out what happen with my palm and see if something helps me througt.
Here is the deal:
I'm trying to sync my palm (A T|X) with the computer (HP Compaq dc5100SFF).
What i have seen so far is for making a succesfull sync the palm must be discovered in the ttyUSB1 ttyUSB0 and the /dev/pilot link must be pointing to ttyUSB1.
The weird thing is, if i unplug the palm and plug it again now is discovered in ttyUSB2 and ttyUSB3 and the link points to the ttyUSB3 and nothing happens ](*,) :confused: you cant syncronize.
What i have to do is kill the gpilotd process and start it up again, and the palm is now right discovered and i can syncronize it.

Someone knows what is happening????

---

### Post by fragos on 2006-12-10
The appearance of ttyUSB2 and 3 is because Linux hasn't gotten around to unmounting 0 and 1 yet and 2 and 3 are the next in sequence.  You can use "ls /dev/ttyUSB*" to see when the origninal connection is unmounted.  It won't take long for it to happen.

---

### Post by rioghal on 2006-12-10
I have a Palm T|X and I lost the sync cable so I found another method of installing Palm apps on the device:

1) For any Palm app, find the *.prc file (Palm resource file) and email it to yourself, as an attachment, via your desktop/laptop PC.

2) Then, in your Palm T|X, connect via wifi and check your email (I used Versamail with my gmail account).. you'll need to download the entire email along with the attachment.

3) In Versamail, after downloading the email and attachment, the attachments will show up at the bottom of the email. Tap the attachment (.prc file) and the Palm T|X will install the Palm app automatically.

4) You're done :)

This has worked for me for all 15 Palm apps that I use on my Palm T|X. I've only synced my T|X once and I didn't install anyting when I did it. I don't own any other Palm devices so I can't say whether or not it will work, but, I would assume all Palm devices using PalmOS 5.x will work with this method. A friend of mine copies the .prc file to an SD card (/Palm/Launcher), inserts the card into her Palm, taps the .prc file and it installs itslef.

There's more than one way to skin a cat ;)

---

### Post by djcrash1981 on 2006-12-10
Thanks for the advice, by the way anyone can tell me how i can install the programs for the palm through the cradle??? Or any another way???? :confused:  :D 

And another question have anyone tried to sync the T|X by bluetooth. I tried this how to [https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto) but it didn't work. ](*,) ](*,) :evil: 

Any idea???? :confused: :rolleyes:  :p

---

### Post by fragos on 2006-12-11
Use an SD card in a PC card reader.  One returned to the Palm the PRC can be copied to RAM.  All PRCs are self installing on the Palm.  You can also get Card Reader 1.04 from [www.mobile-stream.com](www.mobile-stream.com).  Set the Palm in the cradle and run this program.  The SD card in the Palm mounts on your PC like any other flash memory device.

---

### Post by megamania on 2006-12-11
> **rioghal said:**
> I have a Palm T|X and I lost the sync cable so I found another method of installing Palm apps on the device:

1) For any Palm app, find the *.prc file (Palm resource file) and email it to yourself, as an attachment, via your desktop/laptop PC.
Why don't you just change your device from USB to "net:" on pilot-link, jpilot or gPilot?

Then you just have to select "net sync" on your palm, enter the ip address of your computer and you're done.

---

### Post by rioghal on 2006-12-11
> **fragos said:**
> Use an SD card in a PC card reader.  One returned to the Palm the PRC can be copied to RAM.  All PRCs are self installing on the Palm.  You can also get Card Reader 1.04 from [www.mobile-stream.com]("http://www.mobile-stream.com").  Set the Palm in the cradle and run this program.  The SD card in the Palm mounts on your PC like any other flash memory device.

OMG! That is awesome.. alleviates a few steps. Thanks for posting this idea :)

---

### Post by rioghal on 2006-12-11
> **megamania said:**
> Why don't you just change your device from USB to "net:" on pilot-link, jpilot or gPilot?

Then you just have to select "net sync" on your palm, enter the ip address of your computer and you're done.

Well, I didn't know this was possible. Thanks for posting the idea :)

---

### Post by twrock on 2006-12-12
> **djcrash1981 said:**
> Thanks for the advice, by the way anyone can tell me how i can install the programs for the palm through the cradle???

You know, that is an interesting question. I haven't even tried to install a Palm app in Ubuntu. Since my primary computer for sync'ing my TX runs Windows, I haven't even tried to do it yet. Seems gpilotd has that functionality labeled "File" in the conduits, but I don't know how to make it work either. Is it something as simple as creating an "install" folder like on the Windows version (i.e. C:\Program files\Palm\Username\Install) and dropping files in there? Anyone know?

---

### Post by twrock on 2006-12-12
> **fragos said:**
> ... All PRCs are self installing on the Palm.

I wish I could remember a specific example, but it's been a long time and I can't. In the six years that I have been using Palms, there have been a few apps that had to be hotsync'ed to work correctly. Conversely, there were also a few that could not be hotsync'ed and needed to be copied from the external card. It has been rare though, so for the most part, copying from the SD card is a simple way to get a new app onto your Palm.

In addition to the card reader, there is a nice Palm app called CardExportII by Softick. It allows you to connect your Palm to your computer via the hotsync cable, and you computer sees the Palm's SD card as an external storage device. Then you can copy, move, delete files from inside your computer's file manager. (Of course if you don't have a hotsync cable, that's kind of not an option.)

---

### Post by wastrel on 2006-12-12
> **twrock said:**
> I haven't even tried to do it yet. Seems gpilotd has that functionality labeled "File" in the conduits, but I don't know how to make it work either. Is it something as simple as creating an "install" folder like on the Windows version (i.e. C:\Program files\Palm\Username\Install) and dropping files in there? Anyone know?

There's no way to install programs with Evolution.

You can install programs from the command line with either gnome-pilot

```
gpilot-install-file <filename>
```

or the pilot-link tools

```
pilot-xfer -i <filename>
```  

Jpilot offers a GUI for this.  (Kpilot must as well, but I don't know anything about it.)

The File conduit is not for installing programs - I believe it's for doing backups.

---

### Post by twrock on 2006-12-12
> **wastrel said:**
> The File conduit is not for installing programs - I believe it's for doing backups.

There is a "Backup" conduit as well as a "File" conduit, so it seems they must serve different functions. In the description of the "File" conduit it says "Installs files on the PDA".

BTW, here's link for anyone who wants a little more info on the gpilot-install-file command: [http://www.die.net/doc/linux/man/man1/gpilot-install-file.1.html](http://www.die.net/doc/linux/man/man1/gpilot-install-file.1.html)

---

### Post by fragos on 2006-12-13
The TX has bluetooth and if you have a USB bluetooth dongle you can use SendTo and OBEX to transfer files.  There's lots of help setting up bluetooth in Ubuntu so I won't get into it.  I use bluetooth with my Palm E2 to install.  I would think that the TX's WiFi would offer yet another way to install.  Remeber installing is just a matter of transfering the PRC.

---

### Post by rioghal on 2006-12-13
> **fragos said:**
> The TX has bluetooth and if you have a USB bluetooth dongle you can use SendTo and OBEX to transfer files.  There's lots of help setting up bluetooth in Ubuntu so I won't get into it.  I use bluetooth with my Palm E2 to install.  I would think that the TX's WiFi would offer yet another way to install.  Remeber installing is just a matter of transfering the PRC.

> Originally Posted by **megamania** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=1871298#post1871298") 				
 				[I]Why don't you just change your device from USB to "net:" on pilot-link, jpilot or gPilot?

Then you just have to select "net sync" on your palm, enter the ip address of your computer and you're done.[/I]

That sounds pretty easy using wifi, though I haven't tried it.

---

### Post by twrock on 2006-12-13
I've spent quite a bit of time digging into the File conduit and have only found that a lot of people  have had the same question, but so far not the answer. However, I did find a neat little idea in one of the old threads here in the Ubuntu forums.

If you don't want to type commands in the terminal, there is a way to install Palm apps/databases via the "Restore" function of the Pilot Applet in the Panel. Simply create a new directory /home/loginname/MyPilot/Install (your directory setup may be different). Then drag and drop all the files you want to install to your Palm into the "Install" directory. Then right click on the Pilot Applet and choose "Restore...". Change the directory name to .../Install/ and click OK. Push your hotsync button and the files will be installed. It will only install the files, not do a full hotsync (similar to PilotInstall for Windows). Remember to clean out your Install folder after you have completed the transfer or you will be installing them all over again next time.

It isn't all that much of a time saver, but it may be preferable to some. YMMV.

Edit: I also discovered during all of this testing that apps deleted on my PDA do not automatically get removed from my backup directory on my PC. This would mean that if I ever did have to do a restore of my PDA, I would get everything back, including apps I didn't want.

---

### Post by megamania on 2006-12-14
> **twrock said:**
> I've spent quite a bit of time digging into the File conduit and have only found that a lot of people  have had the same question, but so far not the answer. 
In my opinion, jPilot is the best solution available for Gnome. Installing files is easy, backup is easy, and you can access/update your PIM data on the computer (a lifesaver if you lose/damage your palm).

---

### Post by jeremy on 2006-12-14
will jpilot sync with Kontact?

---

### Post by megamania on 2006-12-14
> **jeremy said:**
> will jpilot sync with Kontact?
I don't think so. It's a stand-alone application which resembles Palm Desktop.

---

### Post by twrock on 2006-12-14
> **megamania said:**
> I don't think so. It's a stand-alone application which resembles Palm Desktop.

That's part of what keeps me working on gpilot and Evolution sychronization. I sync with Outlook on my office machine, so using Evolution just feels more familiar. 

Are there email apps that can access the address/contacts data if someone is using jpilot? Sounds like Kontact can't, but are there others? That was one of the biggest reasons that I didn't use the Palm Desktop software in Windows.

---

### Post by djcrash1981 on 2006-12-14
Ok, now i can install and synchronize my palm with my UBUNTU Desktop :D \\:D/

Thanks a lot for the help, by the way what i found on my system is when it doesn't sync my palm with the pc is because it's discovered on the ttyUSB2 and ttyUSB3, so what i did is a small script that kills the gpilotd daemon and start it again, and with that everything goes perfect. :lol:

I'm still searching for a way to synchronize it trough bluethoot, so if anyone have an idea let me know it :D ](*,)

---

### Post by dfourth on 2006-12-30
Synchronization with J-Pilot and my Palm T|X is relatively painless, but J-Pilot is simply not adequate as a replacement for the Palm Desktop. The T|X (as well as my previous Palm) supports three addresses per record, but J-Pilot only supports one, as with the original Palm products. The other problem I have with J-Pilot is with the KeyRing plug-in. It's a terrific idea, but does not permit additions or modifications to categories, so you are stuck with what's built into the plugin if you want to use it. Issues with PIMs and synchronization, as well as a few critical technical programs, are the main reason I keep a dual-boot machine.

---

### Post by elektronaut on 2007-01-05
> **twrock said:**
> 
Are there email apps that can access the address/contacts data if someone is using jpilot? Sounds like Kontact can't, but are there others? That was one of the biggest reasons that I didn't use the Palm Desktop software in Windows.
Sylpheed allows to use jpilot's address database. It's a great email app!

---

### Post by elektronaut on 2007-01-05
> **djcrash1981 said:**
> 
I'm still searching for a way to synchronize it trough bluethoot, so if anyone have an idea let me know it :D ](*,)
I sync J-Pilot using bluetooth. Just put "net:any" in the connection preferences. A bluetooth connection to the palm has to be already configured, try google or the wiki for this, there are a lot of tutorials.

---


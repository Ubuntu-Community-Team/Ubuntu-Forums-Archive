---
title: "Bluetooth remote control with cellphone"
date: 2004-11-18
forum: General Help
---

### Post by SVen2000 on 2004-11-18
I want to use my cellphone (Sony Ericsson T610) as remote control for several programs (e.g. totem or showimg) using ubuntu - is that possible?

---

### Post by jdong on 2004-11-18
Unanswered/abandoned... Moving to Stumper Questions section.

---

### Post by scoon on 2004-11-22
[QUOTE=jdong]Unanswered/abandoned... Moving to Stumper Questions section.[/QUOTE]

Hey there, 

That should be possible.  I use bluetooth keyboards and mouse with ubuntu.  What you must do in order for bluetooth to work properly is to install the bluez-utils and bluez-pin , which are both in ubuntu apt repos.  Then you need to head over to [www.bluez.org](www.bluez.org) and get the kernel patch that matches the kernel you are running.  Patch your kernel, build your kernel and make certain that you have the bluez-utils service starting up durning boot.  Once that is all done, you should be able to do a hidd --show to see if your phone is connected.  Once connected, then you can figure out how to use is for a remote.  I think there is a xmms plugin for such a thing. 

scoon

---

### Post by mterring on 2004-12-21
> Then you need to head over to [www.bluez.org](www.bluez.org) and get the kernel patch that matches the kernel you are running.

What kernel are you running?  [www.bluez.org](www.bluez.org) indicates that normal 2.6 kernels should already have the bluetooth patches.  I have 2.6.8.1-4 and bluetooth works for HCI but not HID (ie. data communications with a phone, but not for a mouse).

---

### Post by scoon on 2004-12-21
Hey there, 

I do not use the ubuntu kernels.  I get vanilla kernels from kernel.org and patch them myself.  

scoon

---

### Post by frisket on 2006-11-13
> **SVen2000 said:**
> I want to use my cellphone (Sony Ericsson T610) as remote control for several programs (e.g. totem or showimg) using ubuntu - is that possible?

Is there really nothing more recent than a recommendation to patch your own kernel? I just installed Edgy Eft, and file transfer with bluetooth works perfectly to my SE Z5201, but there doesn't appear to be (a) any app for Ubuntu to allow a passphrase response when I request pairing from the SE (or vice versa: ie nothing pops up to let you type in the passphrase); and (b) any app to allow remote cursor control for running a program (eg xpdf, ooimpress, etc).

---

### Post by Aetherius on 2006-11-16
about 8-10 months ago i was messing about with a friends Sony Ericsson and i got it controlling my desktop in a matter of minutes.

You had to install a few wee apps, and it couldn't run all the time cos it hogs ur bluetooth even when not connected but it def. worked.

That was Breezy tho... dunno about ol' Edgy.

I bought a k800i yesterday so I'll be investigating it again tonight/this weekend so i'll keep ya posted.

---

### Post by mirshafie on 2006-11-17
I am also very interested in this. I'd like to control apps like MPlayer and KMix with my cellphone (Nokia 7610). If anyone finds out more information about this it would be great if you would post it. :)

---

### Post by Aetherius on 2006-11-18
7610 is quite difficult to use in this respect, i had one until VERY recently, nokia+bluetooth+linux isn't a good combination in my experience, thats part of the reason i got a sony ericsson this time around

however, for windows and mac there is a program called "Salling Clicker" quite impressive my brother used to control his itunes on his mac brilliantly, it even downloaded the album covers and displayed them on his phone. You can get this app in symbian .sis quite easily however you will have to find or develop a server end for it on linux.

[http://www.salling.com/](http://www.salling.com/)

Aeth

---

### Post by Aetherius on 2006-11-18
Part 1 ---

[SIZE="5"][COLOR="Orange"]Simple Desktop Control with Sony Ericsson[/COLOR][/SIZE]

Right, this is deadly simple. It allows your mobile to take control of the mouse and provide some keyboard functionality as well.

first install bluez-utils, there may be some dependancies

```
sudo apt-get install bluez-utils
```

next lets find your phone via ol' bluetooth

```
hcitool scan
```

and you'll get a MAC address and identifier

```
00:11:22:AA:BB:CC  MyPhonesName
```

copy the MAC address and do the following

```
sudo hidd --connect 00:11:22:AA:BB:CC
```

but with your own MAC address, this should bring a mesage up on you phone "allow *** to access remote control?", click yes and select 'Desktop'. woohoo you can control the mouse (as well as tab and windows key and a few other things depending on you model of sony ericsson)

it sucks a bit if you have to do this everytime you want to use ur mobile, and so....back to the terminal

```
sudo hidd --server
```

and now you can connect your phone from your phones remote control menu option ( usually entertainment>>remote control )

Part 2 ---

[SIZE="5"][COLOR="Orange"]Media Player control with Sony Ericsson[/COLOR][/SIZE]

This bit is a right <<explicative deleted>>. 

The Sony Ericsson media player remote is based upon Wind*ws Media Player keyboard shortcuts, so if you want... follow the same steps as above and select media player on your sony ericsson. Then when you click Play/Pause you will just end up printing what ever you're currently looking at (ctrl+P is pause in WMP) and if you hit stop you just get a save dialog (ctrl+S), so if you want to you can change the amaroK global shortcuts to that of WMP and it should work fine, but you'll never print, save or search from keyboard shortcuts ever again.

for the record >>

Play/Pause >> ctrl+P (also print....)
Stop       >> ctrl+S (also save.....)
Next       >> ctrl+F (also search...)
Previous   >> ctrl+B (also embolden.)

as for fast-forward and rewind... i have no clue, rewind seems to be ctrl+B as well (maybe hold it in), but fast-forward seems to be nothing!

volume control is F10 and F9 i think.

thanks for ruining everything again micros*ft.

Anyways best of luck with this


Aeth

---

### Post by frisket on 2006-11-18
Thanks for posting this, it's just what I was looking for. Amazing that this information is (a) so hard to find and (b) not available as a standard facility within the GUI interface to bluez.

The only problem is the granularity: one click on my SE Z750i is *two* menu items in the Applications menu on-screen (laptop is 1440x1050). Whereabouts in the HIDD stuff is the granularity configured?

///Peter

---

### Post by Aetherius on 2006-11-18
no problem, it seems a bit too easy for there to be so many unanswered requests for it!

No idea about the granularity tho, sorry.

---

### Post by Marsolin on 2006-11-19
I am aware of two Bluetooth remote control apps, but neither seems to be in real active development from what I can tell, and neither is in the Ubuntu repos. The two programs are [BlueMote]("http://linuxappfinder.com/package/bluemote") and [ToothMote]("http://linuxappfinder.com/package/toothmote").

---

### Post by Aetherius on 2006-11-21
hey all, may have sorted out this sony ericsson remote issue out once and for all, stumbled across some official sony ericsson documentation on the development of new HID profiles, allowing you assign any keyboard/mouse action to any key on your phone.

Once I have a good look i might create some profiles specific to native apps, totem, amarok, vlc etc etc

if if i get it right i'll upload some profiles and write a HOWTO!

---

### Post by rockprincess on 2007-01-04
hmm I'm not sure what I'm doing wrong here.....

```
sudo hidd --connect 00:xx:xx:xx:xx:xx
Can't create HID control channel: Connection refused

```

any ideas? ;)

---

### Post by littleiffel on 2007-01-11
I am having the same issue as rockprincess. "Can't create HID control channel"

---

### Post by rockprincess on 2007-01-24
ohhh i think i've fixed it last night...at least i got my phone and my headset working..

[SIZE="4"]**this is for all Kubuntu Users who are experiencing problems with pairing their bluetooth device:**[/SIZE]

[LIST]
[*]switch on your bluetooth device (mobile phone, headset, etc..)
[*]go into the konsole and type: passkey-agent --default /usr/bin/bluez-pin
[*]and then enter your PIN
[/LIST]

that's about it really...but it must go easier....this is a dirty solution because i can't be bothered starting this pairing assistant everytime i wanna connect to my headset or mobile phone.
does anyone know how to automatize this process?

i've tried following these solutions :
[http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html](http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html)
[http://docs.kde.org/development/en/extragear-pim/kdebluetooth/installation.setup.html](http://docs.kde.org/development/en/extragear-pim/kdebluetooth/installation.setup.html)

but in my opinion these aren't much of help! kdebluetooth (or kdebluetoothd) needs a massive revamp, hopefully for the next kde version, or for kde4, because they suck!

and for normal users (like me) it's too complicated to get into that stuff, no I'm not being lazy nor I'm making it too easy for myself.
but the simple fact is that I'd have given up already if I hadn't bought my bluetooth devices.

this should go a lot easier!

you can mark this topic as solved!:KS

---

### Post by bornakke on 2007-02-23
People having problems not being able to send the pin to the desktop should also make sure that gnome-bluetooth is installed

---

### Post by Sirhanz on 2007-05-10
Thank you very much this worked like a charm, ive used my w300i ericsson as a remote for a while now but always had to initiate from my computer. Do I have to do the server command each time i reboot , or is that permenant for now? Oh and also you can modify the global media shortcuts in linux. I use Amarok and I just modified those controls. I simply went to edit them and used the corresponding button on the phone to assign the controls. So for instance when i chose to assign next traack command in amarok i pressed 6 on my cell phone, which translates to CTRL+U on my cell phone. It was actually easier assigning the keys like this then it is in windows. Lol. Well good luck to you all. May the force be with you.

---

### Post by goeland86 on 2007-06-12
Ok, so how did the owner of a W300i manage to get bluetooth working right?
I'm on Xubuntu, and I tried the kbluetoothd solution to no avail. I can't transfer files back and forth (konqueror would not display any services) and hidd gives me that control channel error posted above.
Pairing is a problem, no matter what I did that was above in the forum I can't get the passkeys to load (edited /etc/bluetooth/hcid.conf), and still no go.
Any ideas on how to go about this? (Not particularly fond of Xfce, just got it because it's part of Xubuntos, for TinyOS programming, but it's just a few scripts and extra packages on top of Xubuntu).

---

### Post by FuturePilot on 2007-06-13
I have a W300i also. Everything is working except for the remote. When I try to connect it as a remote it connects for a second then drops the connection. Then if I try to control the mouse the phone says connecting to computer or something. And I can't get it to work. Need some help here.

---

### Post by Sirhanz on 2007-06-13
Um I have the W300i. As I recall I had to find the address for the phone then enable it to connect via Hidd server. I cant remember all the details unfortunately but now everytime i boot i have to enable the sever by executing the following as super user.```
hidd --server
``` you can also sudo HIDD --server but this has to be redone everytime the phone reconnects. By executing as SU the PC will listen for the phone and will connect via the phone control. Sorry I dont presently remember all the details.

---

### Post by Sirhanz on 2007-06-13
OK apparently i got this working way back when i joined this thread. It is in the beginning in one of Aetherius's posts.
Aetherius's Avatar 	
Aetherius Aetherius is offline
A Carafe of Ubuntu
	  	
Join Date: May 2006
Beans: 131
Ubuntu 7.04 Feisty Fawn User
Send a message via Skype™ to Aetherius
Re: Bluetooth remote control with cellphone
Part 1 ---

Simple Desktop Control with Sony Ericsson

Right, this is deadly simple. It allows your mobile to take control of the mouse and provide some keyboard functionality as well.

first install bluez-utils, there may be some dependancies

Code:

sudo apt-get install bluez-utils

next lets find your phone via ol' bluetooth

Code:

hcitool scan

and you'll get a MAC address and identifier

Code:

00:11:22:AA:BB:CC  MyPhonesName

copy the MAC address and do the following

Code:

sudo hidd --connect 00:11:22:AA:BB:CC

but with your own MAC address, this should bring a mesage up on you phone "allow *** to access remote control?", click yes and select 'Desktop'. woohoo you can control the mouse (as well as tab and windows key and a few other things depending on you model of sony ericsson)

it sucks a bit if you have to do this everytime you want to use ur mobile, and so....back to the terminal

Code:

sudo hidd --server

and now you can connect your phone from your phones remote control menu option ( usually entertainment>>remote control )

Part 2 ---

Media Player control with Sony Ericsson

This bit is a right <<explicative deleted>>.

The Sony Ericsson media player remote is based upon Wind*ws Media Player keyboard shortcuts, so if you want... follow the same steps as above and select media player on your sony ericsson. Then when you click Play/Pause you will just end up printing what ever you're currently looking at (ctrl+P is pause in WMP) and if you hit stop you just get a save dialog (ctrl+S), so if you want to you can change the amaroK global shortcuts to that of WMP and it should work fine, but you'll never print, save or search from keyboard shortcuts ever again.

for the record >>

Play/Pause >> ctrl+P (also print....)
Stop >> ctrl+S (also save.....)
Next >> ctrl+F (also search...)
Previous >> ctrl+B (also embolden.)

as for fast-forward and rewind... i have no clue, rewind seems to be ctrl+B as well (maybe hold it in), but fast-forward seems to be nothing!

volume control is F10 and F9 i think.

thanks for ruining everything again micros*ft.

Anyways best of luck with this


Aeth
__________________
Desktop/Server - AMD Sempron 3000+ / 768MB / nVidia 6200GT
Laptop - Thinkpad r60e / Core Duo 1.6GHz / 1024MB / Intel 945GM  Again executing hidd --server as super user will keep your connection live as mentioned before. Also I use Amarok with the W300i and I found if I navigate to Amaroks settings menu, then to configure shortcuts, you can simply hit the button you want to assign then press the corresponding phone key you would like to assign and it should write the phones key configuration for the corresponding key to the shortcut. Best Wishes.

---

### Post by freakavoid on 2007-06-21
Here is a python script I wrote using bluemote and pidgin's dbus interface. 

It sends pidgin notifications (IMs and buddy signed on messages) to the phone. I thought I'd post it and maybe somebody else can make use of it. 

To use it: extract the tar-ball anywhere and run the bluepidgin.py file. It even has a tray icon :)

ps: an instance of bluemote must already be runnig and pidgin must have been compiled with dbus enabled. The deb from getdeb.com works fine.

---

### Post by goeland86 on 2007-06-23
Thanks!
For some reason it didn't work on my laptop running Xubuntu, but using the same method on my gentoo desktop let it run just dandy. Sweet!
Now for those wondering about the media player remote, I also have XP on my laptop, and the utility to CREATE those profiles.
I'll post one for amarok as soon as I'm done testing it!
Cheers!

EDIT:
got the amarok .hid file up, with a tricked out image, too. The volume buttons aren't pictured, but they also control the amarok volume =) Each key does what it's marked to do. The 9 key is an alt-tab key combo. The play actually acts as play/pause (win+C by default), forward and backward are Win + B and Win + Z respectively. the direction pad is still the mouse control.
File is here: [http://webdisk.lclark.edu/jcharnas/blog/amarok_2.hid]("http://webdisk.lclark.edu/jcharnas/blog/amarok_2.hid")
Enjoy!

---

### Post by goeland86 on 2007-06-24
By the way, for those wondering, the BT remote control profile editor from SE actually works under wine, sorta. I couldn't get any Win key shortcuts to be detected properly... The rest seemed okay.
Images should be 128x160 for the display of the remote.
Feel free to modify the profile using the editor under wine, if you don't touch the shortcuts for 1, 2 and 3 you'll be fine :)

---

### Post by durfff on 2007-06-24
Sorted!!!

Right, here it is: I've followed this thread for a little bit and tried to get my sony ericsson k800i to be used as a remote control for my computer, to no avail. 

I tried resintalling all the bluetooth apps and dependencies but it just wouldn't connect ("Can't connect"-type message in terminal).

Then for a laugh (well kinda ;) ) I tried file transfer after restarting the X-server (is that right? lol), since after restarting ubuntu I had the bluetooth icon in my taskbar. That worked fine, so I thought I'd give the remote control another go: not working. 

Then I remembered one thing from when I was using mentioned Salling Clicker on wind*ws: the remote control wouldn't work UNLESS I had a file tranfer session open (no need to actually be tranfering files, but the session should be open). 

Tada!!!! It connects and works. 

So, to anyone having a problem getting the remote to work: 

- follow the howto on first page of this thread;
- make sure you have the normal bluetooth utilities (bluetooth, gnome-bluetooth, etc... Just synaptic manager bluetooth and check anything that says bluetooth or bluez)
- once this is done, restart the X-server (ctrl-alt-backspace)
- start the bluetooth file sharing app, connect to your phone and all
- then execute the command sudo hidd --connect [mac address of your phone]

and you should have it!!!

Hope this helps some of you, I have absolutely no idea why salling clicker needed a file transfer session to be open to work, but it seems weird it sorts it out in Ubuntu as well... And by the way, Salling Clicker is a GREAT app, I'm no developer but if I had any time I'd definitely put some effort into porting it to Ubuntu or Linux in general, it's really mint... Really really mint!!! God I'm excited, I can now watch my films in bed ;)


Cheers everyone, good luck!

---

### Post by knorrhane on 2007-08-21
Excellent! Got it working just fine on my W810i. I also made a Remote GUI for the phone to use with Amarok. I use the Windows-button (Super) in my global hotkeys as it doesn't interfer with any other program. 

I made the image using new Amarok-icons I found and the background image is a contest winner-image for the new Amarok logo. I don't have anywhere to put the image on the web so I can't show you but if you P.M. me I'll gladly send you the HID file to use with your phone or just the image.

Thanks again for a nice walkthrough!

---

### Post by Dougle on 2007-08-21
Thanks very much for the post Aeth, got my V600i and Rhythmbox working together sweetly.

Some other links for people to read:
[https://help.ubuntu.com/community/BluetoothRemoteControl](https://help.ubuntu.com/community/BluetoothRemoteControl)
[http://www.usb.org/developers/devclass_docs/Hut1_12.pdf](http://www.usb.org/developers/devclass_docs/Hut1_12.pdf)

(might be usefull might not)

My next task is to map the USB USAGEID codes to keyboard keycodes, i have a set of media keys on the front of my Dell XPS that i want to trigger with my phone (for interoperability reasons, plus they work globally so the lid could be closed or rhythmbox in the panel etc etc) the key codes are:

keycode 160 = Mute
keycode 174 = LowerVolume
keycode 176 = RaiseVolume
keycode 162 = Play
keycode 164 = Stop
keycode 144 = Prev
keycode 153 = Next

... but i've no idea what the number 160 relates too, any ideas?

i've done some trial and error .hids but to no avail.

Dougle

---

### Post by Shootmeagain57 on 2007-09-01
Thanks this post worked with my Sony W880i

---

### Post by FuturePilot on 2007-09-01
Yep, got it working.:)

---

### Post by purfier on 2007-09-02
Did read this thread and no one has said anything about (k/g)anyremote. Its a simple program that lets you control "every" program on your pc, 

[http://sourceforge.net/projects/anyremote](http://sourceforge.net/projects/anyremote)

hope this help guys.

---

### Post by FuturePilot on 2007-09-23
If you use [Exaile]("http://www.exaile.org/") to manage and listen to your music collection, there is a way to get the default Media Player profile to control Exaile without modifying any of the Gnome global keyboard shortcuts.\\:D/

If you have a version of Exaile earlier than 0.2.10, I would recommend updating to the latest version. The version in Feisty's repos (0.2.8 ) is out of date and there have been many bugs fixed in the recent version. There are repos listed here [http://www.exaile.org/downloads]("http://www.exaile.org/downloads")

So now, start up Exaile, and go Edit>Plugins. Go to the Available Plugins tab and check off Global Hotkeys. (If you've already installed this plugin, you can skip this part) Click the Install/Upgrade button. 

Now go back to the Installed Plugins tab and enable the Global Hotkeys plugin, and then click the configure button.

Now we need to edit some shortcuts here. Below I've listed what the values should be for some of the shortcuts. 
Toggle Play/Pause:..........<Ctrl>p
Stop:...............................<Ctrl>s
Previous Song:................<Ctrl>b
Next Song:......................<Ctrl>f
Increase Volume:.............F10
Decrease Volume:............F9

Be sure to include the <>

Click OK and close the Plugin Manager. 

Now on the phone the following keys should perform these functions
Key1 should do nothing (It should be RW but I haven't found a way to get that to work)
Key2 should be the Play/Pause button
Key3 should also do nothing (Should be FF)
Key4 should take you back to the previous song
Key5 should be the stop button
Key6 should take you to the next song
Key7 should do nothing (Supposed to be mute, can't get it to work)
Volume rocker should control the volume.

If all is working you can now enjoy your music!\\:D/
:guitar:

---

### Post by pyriX on 2007-11-15
Im running Ubuntu Gutsy, and have a Sony Ericsson K610i, with an external HP bluetooth dongle for my desktop. That how to at the begining of the forum was a big help, thanks. But I cant get the sudo hidd --server working. Tried editing the bluetooth config file with gedit, but it did not work. In the end, I just created a launcher on the desktop that runs *"--sudo hidd --connect <mac address of phonicle>* in order to initiate the remote control.

Why don't we have better bluetooth support in ubuntu? It's a relatively open sort of standard is it not? It took me ages just to get OBEX file transfer going, and my phone still refuses to pair properly, which means I can't sync it with anything.

Thanks.

---

### Post by rockprincess on 2007-11-16
bluetooth finally works fine for me, after struggeling with it since dapper ;)

---

### Post by jck2 on 2008-01-01
im able to use the remote by hidd connect but when i do hidd server it says Can't listen on HID control channel: Address already in use

---

### Post by FuturePilot on 2008-01-02
> **jck2 said:**
> im able to use the remote by hidd connect but when i do hidd server it says Can't listen on HID control channel: Address already in use

For me that part wasn't necessary. I only had to do the hidd --connect once. After that I could just connect from the phone even after a reboot.

---

### Post by Bou on 2008-04-01
If you read [this thread]("http://ubuntuforums.org/showthread.php?t=741808"), you'll see that I downloaded some .hid files for controlling Totem and Rhythmbox but didn't like a lot the interface so I ended up making a new one.

Old interface:

[IMG]http://img207.imageshack.us/img207/2572/controlesqj8.jpg[/IMG]

Vs. new one:

[IMG]http://img403.imageshack.us/img403/2253/totemic9.png[/IMG]

I'm uploading the .hid files plus some templates in .svg so you guys can change them to your tastes or make entirely new ones if you want.

Cheers.

---

### Post by Bou on 2008-04-01
I just made one .hid file to control the Desktop. I have two problems that I hope you can help me with:

-It seems impossible to map the "volume up" and "volume down" buttons to Fn+F4 and Fn+F3. Any idea?
-I mapped the hash key to Ctrl+Alt+Del but it doesn't bring the shutdown menu, even though manually pressing those keys does bring it up. What can be wrong?

That aside, it's working just fine.

[IMG]http://img265.imageshack.us/img265/8498/ubuntuvj2.png[/IMG]

---

### Post by jasmuz on 2008-04-03
Wohooo!!
This thread rocks!!! There is nothing cooler than controlling Amarok from your bed while your cozy with your GF :) 

I downoloaded the amarok.hid and it works wonders.. i hope to learn how to make my own for VLC, it would be amazing controling the PC while watching a movie with a projector on top..  

haha.. i havent mentioned, im about to use my SE K700 phone for a presentation, look ma' no hands!!

---

### Post by aaaaalex on 2008-04-06
> **jasmuz said:**
> 
.. i hope to learn how to make my own for VLC, it would be amazing controling the PC while watching a movie with a projector on top..  


There already is one for VLC (and others):

[http://www.kde-apps.org/content/show.php/Sony+Ericsson+HID+profiles+package?content=60288](http://www.kde-apps.org/content/show.php/Sony+Ericsson+HID+profiles+package?content=60288)

---

### Post by jasmuz on 2008-04-06
Many thanks !!

---

### Post by Sub101 on 2008-04-16
The best remote program i have found is Amora. Works well, even shows your display on the phone scren, only problem is cant type.

[http://code.google.com/p/amora/](http://code.google.com/p/amora/)

---

### Post by leifileif on 2008-07-18
Hi, I'm using a software called "X-stream remote" to control Rhythmbox from my se w810i. perfect for browsing the playlist and queue songs.....

---


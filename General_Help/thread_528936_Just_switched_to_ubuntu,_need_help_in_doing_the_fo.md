---
title: "Just switched to ubuntu, need help in doing the following things. Thanks"
date: 2007-08-18
forum: General Help
---

### Post by majorkonig1337 on 2007-08-18
I just switched to Ubuntu and want to know how do I perform the following tasks.

1) Change screen Resolution to 1680x1050 (for 22" LCD), I have a 7600GT for which certain restricted drivers were downloaded when I ran Desktop Effects.

2) Use WINE for emulating windows applications.

3) Install my Sound Blaster 24 Live sound drivers, if they're needed.

4) Install Codecs for watching AVI, Real, QuickTime etc etc movies. I normally use the K-Lite codec pack that comes with Media Player Classic, AND can I use that in Ubuntu.

5) Use good Virus Scan, is the VirusScan program that comes on the Ubuntu install CD any good, forgot what it was called, it was listed on the autorun menu.

6) Can I use 3D Max and Adobe Photoshop in Ubuntu.

7) Can I use Visual Basic and Oracle in Ubuntu, I make databases in VB with the backend datasource in oracle.

Thats it for now. Ill ask later if I have anything else.

Thank You

---

### Post by majorkonig1337 on 2007-08-18
Ooh... One more thing.

I used to use BitTorrent for downloading torrents.

Can I use any good Torrent managers in Ubuntu, and how.

---

### Post by strabes on 2007-08-18
1) Check the link in my signature. There are several methods, depending on your setup. I don't have an nvidia card so I can't help you directly.

2) sudo apt-get install wine

Then wine /path/to/*.exe

3) Don't know. Do you have sound at all? If so, through all of the speakers or just the normal stereo 2?

4) sudo apt-get install ubuntu-restricted-extras

5) You don't need antivirus or defragging programs in linux. The best security tool is the noscript extension for firefox because it can prevent malicious websites from stealing user data. All operating systems are equal in this way.

6) 3D Studio Max at winehq: [http://appdb.winehq.org/appview.php?iAppId=343](http://appdb.winehq.org/appview.php?iAppId=343)
You might want to try blender. It's a native alternative.

Photoshop at winehq: [http://appdb.winehq.org/appview.php?iAppId=17](http://appdb.winehq.org/appview.php?iAppId=17)
The Gimp is sufficient for the vast majority of users who aren't doing really advanced image manipulation. I have a file which you can place in ~/.gimp-2.2 which will make your gimp keyboard shortcuts the same as Photoshop's. Message me if you want it since it won't let me attach it. It's just a text file =\

7) Don't know.

8) There are many bit torrent clients for linux. I use ktorrent because I use KDE (kubuntu)

---

### Post by majorkonig1337 on 2007-08-18
Alright, thanks.

Iam actually going out now, so Ill do them later and post back in like 8hrs.

Thanks.

---

### Post by linque on 2007-08-18
1) Modify your xorg.conf (/etc/X11/xorg.conf) to use that resolution. [LINK]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support")

7) Not sure about VB, but you can install Oracle XE (similar to SQL Server Express). It's free. [LINK]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Oracle_Database_XE")

If you can't tell, I'm fond of that site. I spent several hours searching for a way to use the back button on my mouse, until I ran across it. Follow the directions exactly as listed for Oracle XE -- I've had issues using other guides.

I use the Bittornado client for torrents. Go to Add/Remove Applications, make sure you're looking in "All available applications", and search for "torrent".

Good luck!

---

### Post by GuitarRocker2562 on 2007-08-18
bittorrent is already built in (and very basic, too basic if you ask me), but if you want a nice manager deluge is very nice!

---

### Post by Kitsun on 2007-08-18
I use Azureus as my BitTorrent client, I think its very nice, but it takes up more system resources than you would expect (but I mostly use it for downloading overnight), it also had problems installing from synaptic/apt-get, but it worked when installing from Automatix (some Ubuntu people claim that it breaks updates or something, I've never had problems with it, only had problems by not using it).

---

### Post by majorkonig1337 on 2007-08-19
Thank you all for the Info.

I just got back, *Ill check them all one after the other, and post back.

Just a few more things:

* I have a list of updates available, like 115 of them that are about 170MB+ in size. Should I download them.

* I have a few incomplete torrents (with BitTorrent) that I backed up before switching, can I continue those torrents with BitTorrent or any other client.

* Thunderbird OR Evolution Main ?

That's it for Now.

---

### Post by IanW on 2007-08-19
Re: _updates_. Most will be security updates or bug fixes

Short answer - Yes, you'll want them.

Long answer below:-

If you look at the bottom of the Update Manager window, you should see a little triangle and the sentence "Description of Update".
Click on the triangle and it will open a window that tells you what the currently highlighted update changes.
Click on each update to find out what has been changed/fixed.

Re: _Torrents_ Yes. Most BitTorrent clients have an "import torrent" option, usually on the "File" menu (KTorrent definitely does)

Re: _Mail_ Entirely up to you. I use Thunderbird myself as I got used to it on Windows.

---

### Post by majorkonig1337 on 2007-08-19
The ubuntuguide.org link doesn't work, it says the server is taking too long to respond.

Iam looking at this link
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

it says to run the following commands for one of the methods.
[I]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg[/I]

umm... where do I run them from? Where's the command prompt thingy.

Also for adding software through command prompt, you use the same command prompt thingy right.

Thanks

---

### Post by bwtranch on 2007-08-19
Hi :)

I agree with the above posts. I personally like Thunderbird myself. But, both are good. 

To run commands from the terminal go to Applications --> Options --> Terminal in Gnome (I'm pretty sure that's where it is, I have been using KDE and haven't been there in a while, but just look for Terminal)
This will open up a "shell". There are many programs that will give you shell access, but they all do about the same thing. Also called "bash" born again shell, after the programmer who's name was Bourne. Well, Linux can be kind of dorky sometimes. Usually whemn you see "bash", that means you did something wrong and when I see it anymore, it meanns I want to "bash" someone's head in, like the nearest programmer I can find. :) That is usually me, so I don't have to look very far. There is also a terminal app called 'fish' and it is a little easier to use.

Edit: It is apps-->Accessories--Teminal , sorry, I was in K too long. I booted back into Gnome to check that and I feel like I'm back home. Sorry, I keep jumping around so much, it keeps me confused. I think you should just stay with the regular Ubuntu with Gnome. It really is the best OS for Linux.

---

### Post by majorkonig1337 on 2007-08-19
Alright, Cool!

Thanks.

Soo much to doo and soo little time, Ill post back when Ive checked everything out.

Ooh.. One more thing

How do I get my Logitech (MX518 Mouse software) Setpoint and the G15(keyboard software) LCD to work?

Thanks

---

### Post by majorkonig1337 on 2007-08-19
I tried this command in the terminal
*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom*

and then it asked for my password, but I cant type in anything, when i type in my password, the cursor goes blank and nothing happens. I can press enter, which gives me the wrong password error. Whats Wrong ???

---

### Post by linque on 2007-08-19
I can't believe the ubuntuguide.org site is still down. I noticed it yesterday a few hours after I posted, but I just assumed it would be right back up. Keep checking it, as it's an excellent source for Ubuntu info.

When you issue a "sudo" command, you're telling Ubuntu that you want to do something as root (or administrator). After you issue the command, it prompts you for your password. You won't see anything when you type your password, but it is being entered when you type. It will be the same password you log into Ubuntu with assuming that's the only user you have.

I'm not familiar with the keyboard you have, but I ran accross this post in the forums.
[http://ubuntuforums.org/showpost.php?p=2461304&postcount=285]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285")

As far as email goes, I only use web based accounts now (gmail mostly), but I have used both Thunderbird and Evolution in the past. Mozilla announced recently that they were focusing their efforts on Firefox, and the fate of Thunderbird is unknown, so you might want to stick with Evolution.
[http://www.mozillazine.org/talkback.html?article=22235]("http://www.mozillazine.org/talkback.html?article=22235")

Get used to using a terminal. I would add a shortcut to your panel for easier access.

---

### Post by RonP on 2007-08-19
howtoforge.org has an awsome tut on getting all the nescassaries set up called ubuntu ultimat desktop

---

### Post by majorkonig1337 on 2007-08-20
I messed up my ubuntu, lol

I used this method for the screen resolution:
[I]Section "Monitor"
	Identifier	"hp L2335"
	Option		"DPMS"
	Modeline	"1680x1050" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection[/I]
I saved the file and restarted, but nothing.

So i change the *Modeline* to just *Mode* and that messes it up and now i cant start it.

I made a backup with this:
*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup*

How do i restore the backup to get ubuntu working again??

and what do i do after adding *Modeline	"1680x1050" 154 1920 1968 2000 2080 1200 1203 1209 1235* to get it to work.

I have another 2 line below *Modeline* called Hsync and Vsyns or something like that.

Thanks.

---

### Post by majorkonig1337 on 2007-08-20
Bump

---

### Post by bwtranch on 2007-08-20
Close thread.

---

### Post by majorkonig1337 on 2007-08-20
> **bwtranch said:**
> Close thread.

Wmmm...


WHY???

You guys have been of soo much help.

I got most of the other problems solver, just need a few more.

---

### Post by mali2297 on 2007-08-20
> **majorkonig1337 said:**
> I messed up my ubuntu, lol

I used this method for the screen resolution:
[I]Section "Monitor"
	Identifier	"hp L2335"
	Option		"DPMS"
	Modeline	"1680x1050" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection[/I]
I saved the file and restarted, but nothing.

So i change the *Modeline* to just *Mode* and that messes it up and now i cant start it.

I made a backup with this:
*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup*

How do i restore the backup to get ubuntu working again??


I don't know what you mean by that you can't start it, but you should be able to get to a console and 
restore the backup with this:
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
Usually, you will be thrown to a root terminal in which case you can skip the *sudo* part.

---

### Post by Mach1US on 2007-08-20
Go to _Aplication_s ---> _Accesorie_s  ----> _Termimna_l
To run any command as root (Administrator mode) Put _sud_o  in front of the command.
To install any aplication via command line type _Sudo apt-get instal_l and then name of a aplication you want to install.
hope this helps.

---

### Post by majorkonig1337 on 2007-08-20
Alright thanks, ill try that and post back.

yeah it takes me to somekind of consile, ill restore backup and post back.

---

### Post by majorkonig1337 on 2007-08-20
YAY

Thanks, Ubuntu is up and running again.

Can someone please tell me why i couldn't get my resolution  to 1680 after this:

Section "Monitor"
Identifier "hp L2335"
Option "DPMS"
Modeline "1680x1050" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Thanks

---

### Post by linque on 2007-08-21
Have a look at my monitor section of the xorg.conf file. I have a 24" Gateway, and had to manually add my default resolution.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    [COLOR="Blue"]SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1024x768" "800x600" "640x480"[/COLOR]
    EndSubSection
EndSection
```

Try adding your resolution to the 16 and 24-bit depth lines in your original xorg.conf file -- not the one you modified. Again, I had to type "1920x1200" in front of "1024x768". Reboot, or restart X (ctrl + alt+ backspace) and you should be good. Don't change anything else, as it's specific to my setup.

---

### Post by Spr0k3t on 2007-08-21
Recommendation.  If you are going to be using WINE, you will want some form of anti-virus software just in case.

---

### Post by majorkonig1337 on 2007-08-21
I messed up ubuntu again,  I was playing around and messed it up.

First time I messed it up, I used some command in my history (up button) and got the "xorg.conf" file open in front of me in the console, I made the necessary changes (removed what had caused the problem) and replaced file. Well now either I cant find the command or its not working, I tried this *sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*, i enter my password and and nothing, i get the console input line again. 

And, originally i manually made a backup of the file in the "etc" folder, named it "xorg.conf_BACKUP", now using the console i can replace it and rename it in place of the messed up file and everything will be ok.

now can I do this to replace it:

"sudo mv /etc/xorg.conf_backup /etc/X11/xorg.congf"

but this will just replace it, now how do i rename the file to gets its name to "xorg.conf"

Thanks a lot for all the help. Iam finally getting to know the magic of command line.

---

### Post by mali2297 on 2007-08-21
The command
```

sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```
will rename /etc/X11/xorg.conf_backup to /etc/X11/xorg.conf and remove the old xorg.conf in the process. Thus, moving and renaming are done with the same command.

---

### Post by majorkonig1337 on 2007-08-21
I did that ^^ and i know it worked, because when i re did the command, it said file not found, but when i start ubuntu, i get the same error.

Maybe i may have backed it up wrongly etc. Anyway, is there any way i can run the Ubuntu setup and repair the installation, to get it back to normal.

Iam pretty sure the method *linque * gave will work, because the first poster -*strabes's*'s link said that many different methods worked for different people, and i tired all other methods.

Thanks.

---

### Post by BlueNoteExpress on 2007-08-21
Are you sure you're typing the file names correctly?  On the previous page of this thread, it looks like you named the backup copy xorg.conf.backup instead of xorg.conf_backup

---

### Post by majorkonig1337 on 2007-08-21
the xorg.backup was made by command line, using the cp command, but before i knew how to do that, i manually made a copy using saveas in the text editor. which was named xorg.conf_BACKUP

iam going off now, will check back in 8 hrs or so,

thanks

---

### Post by BlueNoteExpress on 2007-08-21
> **majorkonig1337 said:**
> the xorg.backup was made by command line, using the cp command, but before i knew how to do that, i manually made a copy using saveas in the text editor. which was named xorg.conf_BACKUP

iam going off now, will check back in 8 hrs or so,

thanks

I don't know if you put _BACKUP in all caps for emphasis or not, but keep in mind that Linux is case sensitive.  Therefore, xorg.conf_backup is not the same as xorg.conf_BACKUP.

---

### Post by linque on 2007-08-21
Please post the results of this command:

```
ls /etc/X11/*xorg* -l
```

This will show all files that contain "xorg" in the X11 directory.

If you find yourself using the terminal a lot, here's a helpful hint. Type the first few words of a directory, then hit the tab key. If it's a unique value, it will auto-complete the name. For example, type /etc/X then hit the tab key. It will finish out the rest of X11. Not a big deal for such a small name, but it will come in handy if you have a long file name to type out.

Also, if you find yourself without a GUI, and need to edit a file, type "sudo vi". It's an old-school text editor that works in a terminal. You might need to print out a list of vi commands, as it's not that intuitive.

---

### Post by majorkonig1337 on 2007-08-22
Ubuntu is working again, i used the mv command and it worked, the first time i did it, i used lower case letters and i saved it in upper case, that was the problem. 
The ls command for the etc/X11 folder gave me

xorg.conf
xorg.conf~
xorg.conf.backup

and the same command for the etc folder (where i saved _backup file) gave me
xorg.cong_backup~

and i used the same name in mv command and it worked.
Thanks for that, hmm.. now back to the resolution problem,

i tired what * linque * said, i did exactly the same thing, nothing :-((

do i need to like update my drivers or anything, iam using the drivers that were downloaded thru desktop effects.

Thanks for all the help.

---

### Post by majorkonig1337 on 2007-08-22
I got the resolution. I used this method:

[I][B]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

A configuration page will appear, asking if you want to autodetect video hardware. Select yes, and you should be able to just hit enter a bunch of times to accept the autodetected configurations. After completion, close any open windows or programs you have running on your desktop and press CTRL-ALT-Backspace to restart X. You will be asked to log into your GNOME session again and hopefully everything will be fixed. If not, try the next solution. [/B][/I]

I actually left this one out and tired the others on that page *[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)*
lol.

Anyway, thank you alllll for helping me out.

Ill post back if I need anything else.

Thanks Again.


PS_ one more thing,

out of the 2 torrent clients, which one should i use, keep in mind that i have incomplete torrents that i need to import:
* K TORRENT
* BIT TORNADO 

thanks.

---

### Post by mali2297 on 2007-08-22
> **majorkonig1337 said:**
> 
PS_ one more thing,

out of the 2 torrent clients, which one should i use, keep in mind that i have incomplete torrents that i need to import:
* K TORRENT
* BIT TORNADO 

thanks.

Now that you are familiar with the terminal, why not try out rTorrent? :)

---

### Post by majorkonig1337 on 2007-08-22
Hmm...

I could try it out. I didnt find it under "torrent" in Add/Remove Apps. Ill take a look at it. 

is it completely command based? 

and if I dont like, they which one from the above you you recommend ?;)

---

### Post by mali2297 on 2007-08-22
I was only semi-serious, but if you're interested, this article gives a nice presentation:
[http://polishlinux.org/apps/p2p/rtorrent-console-p2p/]("http://polishlinux.org/apps/p2p/rtorrent-console-p2p/")

You can find rTorrent in Synaptic.

As for KTorrent and BitTornado, I haven't tried them out.

---

### Post by mali2297 on 2007-08-22
Also, if you want to edit files in the terminal, I would recommend *nano* rather than *vi*. 
It is a very basic editor.

---

### Post by majorkonig1337 on 2007-08-25
Hey All,

Everything is fine.

I had a few more questions.

1) In Firefox, how do I goto "Settings" where I can change my homepage etc.

2) When Iam saving pictures/documents etc, to my NTFS partitions, it doesn't let me save it. I can save in my Windows FAT partition and my Filesystem ext-3 partition. 
When I try saving something, it says the drive is write protected and try later after enabling it, the Folder Access under Drive Properties > Permissions is disabled.
How do I fix this?

3) One of the previous replies to my "Importing Incomplete Torrents" question was this: *Re: Torrents Yes. Most BitTorrent clients have an "import torrent" option, usually on the "File" menu (KTorrent definitely does) * by *IanW*.
I installed KTorrent, I pasted the incomplete torrent files in the */home/feltadox1337/.kde/share/apps/ktorrent/* folder as shown in pic:
[http://i199.photobucket.com/albums/aa203/majorkonig1337/ktorrent.png](http://i199.photobucket.com/albums/aa203/majorkonig1337/ktorrent.png)
(selected files are torrents)

How do I go about importing my incomplete torrents??? 
Do the incomplete files have to be in those folders as shown in the pic or without the folders.

Thanks A Lot.

Yours Sincerely,
Me

---

### Post by majorkonig1337 on 2007-08-25
Bump

---

### Post by flemnos on 2007-08-25
1)  In Firefox, your "Settings" are under **Edit** > **Preferences** and from there the preferences window should look almost exactly like the one you're used to.

2) For your NTFS partitions, look at [this section of the ubuntuguide.org/wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions")

3)  not sure about kTorrent, but what works on some other clients is to load the .torrent file (in kTorrent) and when it asks where to download to, point it at the folders containing your partial downloads--it should then check what's in those folders and start wherever you left off.  See if kTorrent does something like this... check [this page]("https://help.ubuntu.com/community/KTorrent") for kTorrent information.

---

### Post by mali2297 on 2007-08-25
1) It isn't that hard to find, Edit-->Preferences/Settings or something like that (mine is translated into Swedish).

2) This might help you:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

3) Can't help you there.  (If you had chosen rTorrent then...)

EDIT: flemnos gave better answers.

---

### Post by majorkonig1337 on 2007-08-25
Thanks, I got it.

The firefox thing was right under my nose, lol.

And that ktorrent page was very helpful, i had to enable a plugin. I imported all my torrents and its all good.

I still couldn't  figure out the partitions part, i did both the methods and i still cant save, its actually on my other hdd, i have 1 80Gb with 3 partitions (1FAT widows, 1 ext3 Linux and 1NTFS) all these partitions works, and another 500GB hdd with 2 NTFS partition called (TOP SECRET and MINE), you can see it in the ktorrent pic above, its these 2 partitions that dont work. I tired both ways and nothing. I can copy/view and all that, just not save. 

Any more ideas??

Thanks

---

### Post by majorkonig1337 on 2007-09-02
Hey Everyone!

I had another question:

I use Ubuntu 7.04 Fiesty, which version of Linux is this: **Linux X-86** or **Linux X-64**.
I was looking at drivers download at the Nvidia website, and under Linux drivers, they had these 2 versions listed. So I wanted to know which to download.

And is it a good idea to use those drivers, or its something different than what I want. because when I ran "Freelancer" through WINE, it told me that my Audio Drivers were not there/supported and my Video Drivers were not there/supported, and I couldn't continue. So I thought I should get new/working drivers.

Thanks

---

### Post by Amazona aestiva on 2007-09-02
Sound Blaster doesn't need drivers. ALSA&OSS is perfect for mine.

---

### Post by majorkonig1337 on 2007-09-02
Ok, thanks!

Any ideas about the other Q?

---

### Post by Amazona aestiva on 2007-09-02
See the first link in my signature. It might help.

---

### Post by majorkonig1337 on 2007-09-03
Could someone please tell me what do I have Linux X86 or Linux X64.

And would installing those drivers on the Nvidia website be a good Idea.


PS-(cockatoo dude) I checked out your topic, it was nice, I installed amarock,  but when I play mp3 files I get a message saying "no mp3 support" and it crashed, I need to force quit it ??? Any ideas?

Do you know any good video playing programs in which I can do the following:

*Increase/Decrease volume with the mouse scroll wheel.
*Pop up the navigation pane(status bar etc) when in full screen mode.

Iam used to Media Player Classic, and those features are really handy, right now iam using VLC, which is allright.

Thanks.

---

### Post by mali2297 on 2007-09-04
> **majorkonig1337 said:**
> Could someone please tell me what do I have Linux X86 or Linux X64.

Try this
```

uname -m

```

---

### Post by majorkonig1337 on 2007-09-04
Got it, thanks.

its X86,

and is installing those drivers on the nvidia website a good idea??

---


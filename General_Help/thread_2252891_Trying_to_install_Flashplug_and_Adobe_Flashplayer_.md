---
title: "Trying to install Flashplug and Adobe Flashplayer in 14.04"
date: 2014-11-15
forum: General Help
---

### Post by Richard_Precht on 2014-11-15
FIRST... Let me apologize for my NEWBIE status and general lack of knowledge. I am willing to learn if that is any consolation.  I certainly do not have the attitude that I cannot learn, even though I am a very OLD dog!

OK... I admit I have toyed with Linux in the past, but never got a swing at the ball - so I definetly never got to 1st base!

But with the help of my daughter and son-in-law, I am now running Ubuntu 14.04 on a desktop PC here in Virginia, USA.  

STATUS>>> I want to install Adobe Flash Player  and then also want to later install Google Chrome and have Adobe Flashplayer work within Google Chrome.  That is what I would like to accomplish in the end!

OK here is what I have tried so far...

Opened terminal, did the three command lines shown here: sudo apt-get install flashplugin-installer sudo apt-get update sudo apt-get install adobe-flashplugin

 Then I ended up with this message: richard@Alex:~$ sudo apt-get install flashplug in-installer [sudo] password for richard: Reading package lists... Done Building dependency tree 
Reading state information... Done E: Unable to locate package flashplug E: Unable to locate package in-installer 
richard@Alex:~$  
 
did NEXT command line: sudo apt-get update (which loaded the "trusty-backports" etc) i.g. = Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") trusty-backports/universe Translation-en Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") trusty/main Translation-en_US Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") trusty/multiverse Translation-en_US Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") trusty/restricted Translation-en_US Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") trusty/universe Translation-en_US Reading package lists... Done 
richard@Alex:~$  
 
did NEXT command line: sudo apt-get install adobe-flashplugin (gave me this info): Reading package lists... Done Building dependency tree 
Reading state information... Done Package adobe-flashplugin is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
 E: Package 'adobe-flashplugin' has no installation candidate 
richard@Alex:~$
 
SO... what needs to happen here?? 
Thanks!
Richard (newbie) in Virginia

---

### Post by grahammechanical on 2014-11-15
I use the Ubuntu Software Centre. It has Adobe Flash Plugin Installer. Just search for Adobe. Chrome has its own version of flash player (Pepper Flash, I believe) you should not have problems with Chrome. Perhaps you should install Chrome first and see how it goes.

By the way, Adobe flash plugin is proprietary software. So, it is not in the Ubuntu repositories. We install an installer and that does the dirty work for us. So, a better command would be

```
apt-get install flashplugin-installer
```

That is the package in the Ubuntu repositories. With the command you used you were actually trying to install something that was not there in the repositories and that why apt-get returned "has no installation candidate."

With Chromium we install a pepper flash plugin installer and that extracts pepper flash from Chrome for us. 

Regards.

---

### Post by Impavidus on 2014-11-15
> **Richard_Precht said:**
> 
 Then I ended up with this message: richard@Alex:~$ sudo apt-get install flashplug in-installer [sudo] password for richard: Reading package lists... Done Building dependency tree 
Reading state information... Done E: Unable to locate package flashplug E: Unable to locate package in-installer 
richard@Alex:~$ 
It seems an additional space sneaked into that command, between flashplug and in-installer.

The correct way to install the flash player from the command line is by```
sudo apt-get update

sudo apt-get install flashplugin-installer
```But you can also use the software centre or one of the other tools. Software centre has been designed for newbies.

To get chrome you have to go to google chrome's website and download the .deb file. Pay attention to the architecture, 32 or 64 bits. For legal reasons chrome cannot be included in the Ubuntu repositories. Double click the .deb file and it should install and update automatically.

Chrome comes with its own flash player, which is more recent than the one coming from flashplugin-installer. This has to do with Adobe's policy regarding software for Linux, and Google's way of dealing with that.

---

### Post by Mike_Walsh on 2014-11-15
> **Richard_Precht said:**
> FIRST... Let me apologize for my NEWBIE status and general lack of knowledge. I am willing to learn if that is any consolation.  I certainly do not have the attitude that I cannot learn, even though I am a very OLD dog!

OK... I admit I have toyed with Linux in the past, but never got a swing at the ball - so I definetly never got to 1st base!

Hello, Richard.

DON'T apologise for being a newbie; we ALL had to start somewhere!

My Mum has just got the hang of 'surfing'.....at the age of 81. Now she can keep in touch with her brother, and various other relatives; she wishes she'd learnt years ago.

I think 'silver surfers' are to be commended for learning what often appears to be highly technical stuff. And the question you've asked is, I think, one of the most frequently asked ones in the forums.....so you're in good company.

Adobe's policy towards Linux leaves a lot to be desired; they haven't gone out of their way to make it easy for us. To that end, we sometimes have to resort to some rather 'dirty' tricks by way of workarounds...as Graham has mentioned!


Regards,

Mike. ;)

---

### Post by Richard_Precht on 2014-11-15
@ Impavidus.... Thank you for the good help.  I have downloade Chrome.  However I seems I have to "run" or open Chrome by using Terminal?  Is it possible to get a shortcut or icon for Chrome onto the toolbar of Ubuntu 14.04?  If possible to do this, can you give me the steps to do that? Google Chrome is currently located in " files" under this directory: /home/richard/Downloads/google-chrome-stable_current_amd64.deb   When I double click on this the Shopping Bag giggles (Ubuntu Software Center) and when I go to the shopping bag, I find this message there: " Please install "google-chrome-stable" via your normal software channels. Only instal this file if you trust the origin".   If I click on the install button (on the right),  The installation begins, and I authenticate by entering my password, when the installation appears to begin and the progress bar starts... But THEN it stops and the page is "greyed out" and nothing else happened.  Not sure what that is all about?  Perhaps I need to delete the download (if I knew how - which I do not) then go to Google and re-download the app. ??  Any help would be much appreciated.  Thanks!

---

### Post by monkeybrain20122 on 2014-11-15
Well to install .deb packages with one click my preferred approach is to use gdebi instead of the Ubuntu software centre. Much faster and lighter, you would finish installing before USC even opens.:) First install that either with the USC or from the terminal
```
sudo apt-get install gedbi
```

Then right click the .deb file you downloaded, choose properties and choose gdebi as the the default for .deb. Now click on it and gebi would open and prompt you to install. Wait til it finishes (there will be two options on the window when it finishes: reinstall package and remove package) Then close gdebi. You can now delete the .deb file you downloaded.

Now go to the dash and search for Chrome, click the icon and it will start. You can drag the icon and pin it on the Unity launcher for easy access.

---

### Post by Richard_Precht on 2014-11-15
LOL thanks Mike I am not as old as your mum  but at 66 I need a lot of help from the younger crowd who grew up sitting in front of a monitor - while I grew up playing outdoors!

---

### Post by Mike_Walsh on 2014-11-16
> **Richard_Precht said:**
> LOL thanks Mike I am not as old as your mum  but at 66 I need a lot of help from the younger crowd who grew up sitting in front of a monitor - while I grew up playing outdoors!

Well, at 56 I'm not so far behind YOU; but I belonged to the generation that were just beginning to hear rumours about this 'bright new future' in our latter days at college.....and in MY case, it piqued my interest, to the point where I enrolled in night-school classes simply to find out more about it! That was roundabout '77-'78; and really, I haven't looked back....been playing about with the things, in one form or another, ever since.

You're never too old to learn new things; but before you say it, I will agree.....it DOES get harder as you get older; the concentration's not what it once was!

You're definitely in the right place to ask questions, though... ;) No matter WHAT your problem, SOMEBODY on here will have a suggestion sooner or later.

Regards,

Mike.

---


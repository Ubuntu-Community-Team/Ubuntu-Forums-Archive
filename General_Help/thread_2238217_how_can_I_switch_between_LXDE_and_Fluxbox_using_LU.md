---
title: "how can I switch between LXDE and Fluxbox using LUBUNTU"
date: 2014-08-06
forum: General Help
---

### Post by nigelhinton on 2014-08-06
I had a very usable build using Lubuntu with a login switch to use mostly Fluxbox with occasion use of LXDE.  This was because my principal app is a series of spreadsheets used with Libreoffice Calc and at the time Lubuntu would freeze and lose data when running Libreoffice unless you installed Tint. 
 
My computer is a Optiplex P4 with 1 GB memory.  It ran like mustard with the old Lubuntu/Fluxbox build with video concurrently with spreadsheets, Firefox open etc etc. This was very impressive really.
 
I 'upgraded' to Lubuntu 14 because I could not install some software and I became concerned for support issues. 
 
Real sense of negative deja vu as I installed as the Grub load did not work when I attempted an install hoping to retain existing packages.  I reformatted disk using gparted and then did a clean install from a usb stick

I then experienced a series of some minor but irritating difficulties as well as the principal problem. 
 
My main app requires programming using a suite of programs developed using QB64 that I developed myself for stat analysis.  After many hours of trial and error I managed at least to get my executables working but the IDE will not compile so I cannot maintain my software.  Probably some library files missing.  I had installed G++ plus many libSDC files which got my executables going. 
 
I then found that Libreoffice was incredibly slow to the point of being unusable - if you move the cursor down the screen it moved quickly until it gets to the bottom then scrolls so slowly that you have to wait for it to catch up. 
 
I re-installed Gnumeric which I had de-installed (a little tricky as it is, for some reason, a 'metapackage' with that wp package.) 
 
Gnumeric was equally slow. 
 
My spreadsheets are not especially large (120k) and ran well using the old calc version under the old Lubuntu OS. 
 
I've searched the Lubuntu forums and the Libreoffice forums and have come across similar problems but no solutions. 
 
I did change calc memory limits in the options part but no change.  I noticed in System Monitor that the application only took 30mb of memory which seems a bit low to me and wondered whether it is not grabbing sufficient memory to give quick screen refresh.  If i use page down or up then it is very quick, possibly because it is going out to disk.  I saved in ODS format and also tried a save and retrieve in Excel format to see if that made a difference. 
 
I then decided to try it using Fluxbox as with Gnumeric AND libreoffice calc being slow, it may be a LXDE issue rather than an application issue. 
 
I then recalled that I had a problem when I built the old system in that the LXDE login screen does show desktop options.  

I experimented and had a disaster when I tried to invoke an alternative desktop using 'startx' because I could not log on at all - it prompted for my user name but would not accept my password.

I searched the forums and managed to get into recovery mode (my machine - keep the right shift key down when the Dell logo appears), then into root and used "mount -o remount,rw /" to get read/write access then "ls -l /home" to check to see if my user name was there.  Used "usermod -aG sudo <my user name>" to redo my password.  Logged on and got my desktop back.  I then had to delete the .Xauthority file as it appeared to lock access to X.windows.

So, that calamity over, but still need either a solution to Libreoffice problem - slow scrolling.  I looked for older versions of Libreoffice calc to test whether these would solve the problem but could not locate any apart from MS Windows versions on the Libreoffice site.

Also need to know who to get a login prompt that allows me to select between Fluxbox and Lubuntu/LXDE and any other desktop manager is wish to use.

(apart from the spreadsheet everything else runs really quickly including video playback and my statistical programs)

I also need to solve QB64 compilation problem as otherwise I cannot maintain my software. I did install a DOS version under WINE and it works perfectly but as many of my programmes use shell commands, despite spending time trying to replicate Linux shell commands in DOS, looks like a non-runner.

Other minor problems experienced:  new version of Firefox a step backwards for me and I will be looking to install a back version.  
The well-documented missing GB keyboard managed to solve by searching the forums but I'm surprised that a minor but irritating bug should get through testing.


Any assistance would be gratefully received.

---

### Post by vasa1 on 2014-08-06
Hi, I too am interested in your Calc problem. I think it would be nicer if you could make specific threads for specific issues with relevant thread titles so that your threads will be clearer to those who want to help.

Re. LibreOffice, have you turned off *anti-aliasing* under Tools > Options > View? That may help a bit.

---

### Post by nigelhinton on 2014-08-07
Thanks vasa1

I tried turning off anti-aliasing but it generated more erratic cursor movements (cursor moving upwards and sideways when you were pressing the down key) and also was still slow scrolling.

As far as separating out individual issues - the main issue is in my title which is switching to other desktop managers as I believe the Calc issue is related to LXDE and I really don't have time to experiment sorting out LXDE-related issues - I've been there before with my early Lubuntu experience and found that I spent ages trying to fix something that was unfixable.

If I don't get anywhere with this I'm going to have to spend a day loading a new OS as I'm really at the end of my tether on this.  Just today, the system continued to use the US keyboard despite going through a procedure that worked before through log-out/log-in.

Having searched the Libreoffce forum and other forums there does not appear to be any solution to the Calc problems which are severe.  Given that Gnumeric also displays the same slowness this indicates LXDE issues.  

In my previous installation, LXDE could not even allow mutliple instances of Calc without freezing, in the processing losing work.

Quite frankly, this is a fantastically quick system (apart from Calc) but it is too prone with bugs to be useful to me to do real work.  

So I'm really only interested in how to switch to Fluxbox or XFCE or any thing else than LXDE.

I take your point that perhaps that is all I should have included in my thread.

Thanks for responding.

---

### Post by vasa1 on 2014-08-07
Hi, if you've done a full Lubuntu install and are not happy with LXDE you can log into Openbox. 

If you've done a full install of Fluxbox, you should see that as an option as well. 

I'm currently using just Openbox (via the Openbox session option at login time).

---

### Post by nigelhinton on 2014-08-07
Vasa1

Just to let you know after I removed aliasing as you suggested and then changed it back I saved the sheet - when I retrieved it the keyboard did not work at all.  Cursor movements in Geany were now slow in scrolling whereas before they were fine.

Perhaps this indicates where the problem lies.  It looks like something to do with keyboard in LXDE.

Regars,

---

### Post by nigelhinton on 2014-08-07
hello Vasa1

Please tell me how to get into Openbox - the only thing I see is the LXDE login-on with my user name and box for password.

thanks

---

### Post by nigelhinton on 2014-08-07
Vasa1,

Hello again.

Rebooted and now I get just the slow scrolling in Calc as before without the erratic cursor movements.

Cursor movement in Geany is smooth and fast.

---

### Post by vasa1 on 2014-08-07
> **nigelhinton said:**
> hello Vasa1

Please tell me how to get into Openbox - the only thing I see is the LXDE login-on with my user name and box for password.

thanks
You can select the option by clicking on the cog-wheel/gear icon near the top right-hand corner of the screen at login time:

---

### Post by nigelhinton on 2014-08-07
vasa1,

Thanks - loaded Fluxbox, tried my sheet, same problem if not worse.

This must be problem with spreadsheets within this build as Gnumeric also was very slow.

I'm going to try to find an old copy of Libreoffice calc,otherwise I've tested my sheets with another Linux OS and they are super fast so my fall back is a full install of another OS which means I lose all the work I've done configuring this build and most likely all the apps I've downloaded.

I'll let you know if using the original LO calc version peforms OK.

Thanks

---


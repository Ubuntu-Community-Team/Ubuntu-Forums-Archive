---
title: "List of smaller (?) problems like Trash seems missing etc."
date: 2008-07-01
forum: General Help
---

### Post by indiworks on 2008-07-01
Hello,

I just switched to an Ubuntu PC (after 15+ years on the Mac) and have a couple of (smaller?) problems or things I don't quite understand. I hope this list of questions is not too long, some short answers or general directions where to find out more about these topics would be quite helpful. Thanks!

- After one recent update I could not change my monitor resolution any more, a couple of days later there was another update and the issue seemed fixed. Today there was yet another recommended update and again I can't change the monitor resolution any more. What to do...?

- Since one of the recent updates my Trash seems missing - all my files go to the "Deleted Items Folder". How can I get my Trash back and what is the "Deleted Items Folder" meant for?

- When installing software via the Synaptic Packet Manager (only sometimes?) I am being asked to insert the Ubuntu Studio 64-Bit CD that I don't have. I then insert the "normal" Ubuntu one (8.04 Desktop AMD64) and have to keep clicking O.K. a couple of times, otherwise I can't install anything.

But this is confusing me: until two week ago I had no internet connection on the PC and could not install anything via the Synaptic Packet Manager, so I was assuming those packages all have to be downloaded and are not on the CD. (Although when I attempted to install packages without having an internet connection the system was able to tell me that these packages were not available for my platform...) But now that I have internet on the PC why do I still have to insert the CD when using the Synaptic Packet Manager...? (Also before I had internet on the PC I installed a couple of programmes from the Ubuntustudio i386 DVD that I have - I thought that's O.K. since I was asked if I wanted to upgrade/install software when inserting the DVD. But maybe this is what confused my system...?)

- Is it O.K. to install software without the Synaptic Packet Manager and move programmes to a folder inside the Home folder? I now have a "Programmes" folder there and use apps that I downloaded using my iMac before I had internet on the PC - also simply because I can't find the "Applications" folder that is listed in the main Ubuntu menu...

- After installing a series of (proprietary?) apps using a recommended, longer Terminal command from the Multimedia forum I still don't have DVD playback. Only one self made DVD from a colleague showed video, sound was not working. The two commercial DVDs that I tested simply did not work at all. I tried the Totem Video Player (which just crashes with DVDs) and the VLC. But both DVDs work on my iMac. Is there a simple way to get this to work or is DVD playback currently a general problem under Ubuntu?

- How safe or recommended are hacks for making a 32-Bit version of a programme work on a 64-bit system? I would need Skype (or something similar) but currently there is only a 32-Bit version available. I found a hack in one of the Ubuntu forums but since a back-up is recommended before doing this I am not sure if this is such a good idea. Any recommendations...?

- I installed the proprietary driver for my GeForce 8600 graphics card and while this seems to work well in blender, I can't get smooth playback when watching Flash Video full-screen, maybe just a couple of frames/sec or so. Also sometimes Flash does not work at all, I only get a grey window where there should be Flash. Reloading or restarting Firefox solves the problem, but sometimes I need to do this a couple of times. Is this a know current limitation for Flash under Ubuntu?

And three more Ubuntu preinsalled apps related questions:

- Is there a way to turn of spell checking for the Tomboy Notes app? I'd like to use it but find that red underlining quite irritating. Or is there maybe another similar app that lets you turn off spell checking?

- When you save/print e.g. a website as a .pdf is there a way to name it before it gets saved/have the option to choose the folder where it should be saved to? (Currently they all just go to the PDF folder inside the Home folder and are automatically named.)

- In OpenOffice I tried to change the spellchecker from American English to British English but it always reverts to American English. Also after changing the system wide language options to British English this still does not work. I also would sometimes need German or French as the default language for the OpenOffice spellchecker. Is this a know problem with OpenOffice or is there something else I need to do?

Sorry if this list is a bit long, if those questions can't all be answered then take it as a list of things that a new user keeps wondering about for a while when he switches to Ubuntu... So far most things worked quite well, but important things connected to audio/video and graphics seem to be a bit of a problem if you don't have internet access on your new Ubuntu PC, that surprised me a bit...

Thanks!

---

### Post by NT4usB on 2008-07-01
(You'll probably get better results asking one question per post...)
> ...- When installing software via the Synaptic Packet Manager (only sometimes?) I am being asked to insert the Ubuntu Studio 64-Bit CD that I don't have. I then insert the "normal" Ubuntu one (8.04 Desktop AMD64) and have to keep clicking O.K. a couple of times, otherwise I can't install anything...
In synaptic, select repositories. Find the third party or extra repositories or..? (not at my Linux machine atm)
You'll see checkbox next to a CD related entry. Uncheck it.
(vague enough for you?) *g*

---

### Post by indiworks on 2008-07-02
> **NT4usB said:**
> (You'll probably get better results asking one question per post...)

In synaptic, select repositories. Find the third party or extra repositories or..? (not at my Linux machine atm)
You'll see checkbox next to a CD related entry. Uncheck it.
(vague enough for you?) *g*

I see, many thanks for your answer!

I did not want to post a whole bunch of questions in this forum one after the other, I thought this might not look too good either, but I guess I have to do split it up somehow... - since I keep having issues with my 64-Bit installation I think I will start from scratch first and install the 32-Bit version, maybe better suited for me, there seem to be more users/better support for it as far as I can see now. (I only went for the 64-Bit version since I thought I have to when looking at the technical details of my chip, an Intel CoreDuo). Also a fresh (32-Bit) installation should automatically solve a couple of problems that I have, like being able to install Skype...

---

### Post by Elfy on 2008-07-02
> spellchecker Open oo and check that format character has UK set, alos check in tools - options > language settings

> Tomboy Notes Edit - preferences - spell check when typing

> DVD Meake sure you have the restricted extras installed check here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> updates - What to do...?Are these proposed, security or main updates. If they are coming from proposed - turn it off (see in a minute). Further - you don't HAVE to accept updates, security updates are a good idea though.

> insert the Ubuntu StudioTurn it off - open software sources - system admin menu - disable the cdrom's, check that you have main, universe, multiverse, restricted enabled. Go to 3rd party tab check the partner repo if you want. In updates - you can turn off everything other than security if you so wish.

> Is it O.K. toI don't think it's a problem as you would likely have to manually remove them anyway.

> TrashI added it to the desktop and then moved the icon onto the panel, you can alos get to it through nautilus - trash:/// in the location bar will find it. To get it onto desktop and then move - open gconf-editor by typing it into run box of Alt+F2 - 

navigate to apps- nautilus - desktop - you will see trash on the right pane - enable it.

That is a few answered, you will need to have a thread or a good search for the flash thing - there are plenty about.


Big long threads like that are not at all easy to decipher - too many questions on one page, there are many here who's first language is not English.

---

### Post by indiworks on 2008-07-03
> **forestpixie said:**
> Open oo and check that format character has UK set, alos check in tools - options > language settings

It's the last one! Tools - Options - Language Settings. This is a bit hard to figure out on your own! I think most users would expect to only have to choose the right Dictionary language under Tools - Spelling check... If this is not a bug and won't be fixed in future updates I think I'll suggest to the developers to make this easier for the user...

> **forestpixie said:**
>  Edit - preferences - spell check when typing

Found it! Again I was looking for this on the individual notes where you have the Tools options...

Now when clicking Close after (un)ticking the check box under Preferences Tomboy Notes sometimes closes/crashes, but sometimes not.

This is similar to the Screen Resolution problem that I have: sometimes I just can't change it, then after an update or a restart it works again (and then not...). Is this kind of instability something I should be concerned about (go for a reinstall and maybe really switch to the 32-Bit version) or is this due to 8.04 being quite new and stability only comes after a while...?

> **forestpixie said:**
> Meake sure you have the restricted extras installed check here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It seems that this is already installed, the check box next to ubuntu-restricted-extras is ticket and I can't Apply Changes, only Cancel. The other package that is linked under Playing DVDs libdvdcss2 is only available for 7.04, 7.10, or 8.04 (i386), I now still have the 8.04/64-bit version running. I guess I'll have to put some more time into this and ask in the Multimedia forum or the 64-Bit forum. Thanks...

(Having to go through this makes you dislike proprietary software concepts just a bit more - how hard should it be to be able to watch a DVD that you legally obtained...? I would not be having this problem if I was relying on illegally downloaded rips... The irony!)

> **forestpixie said:**
> Are these proposed, security or main updates. If they are coming from proposed - turn it off (see in a minute). Further - you don't HAVE to accept updates, security updates are a good idea though.

Turn it off - open software sources - system admin menu - disable the cdrom's, check that you have main, universe, multiverse, restricted enabled. Go to 3rd party tab check the partner repo if you want. In updates - you can turn off everything other than security if you so wish.

O.K., done...

> **forestpixie said:**
> I don't think it's a problem as you would likely have to manually remove them anyway.

Understood...

> **forestpixie said:**
> I added it to the desktop and then moved the icon onto the panel, you can alos get to it through nautilus - trash:/// in the location bar will find it. To get it onto desktop and then move - open gconf-editor by typing it into run box of Alt+F2 - 

navigate to apps- nautilus - desktop - you will see trash on the right pane - enable it.

Hmmm... Not figured this one out yet, but I will read more about it... My problem could also be a different one...? When I right click a file or folder in order to trash it I now only get the option "Move to the Deleted Items Folder" where before I had "Move to Trash" (or something similar). I found the Deleted Items folder under Places, but maybe I'll get "Move to Trash" back once I've figured out where nautilus is and how it works... Thanks...

> **forestpixie said:**
> That is a few answered, you will need to have a thread or a good search for the flash thing - there are plenty about.

Big long threads like that are not at all easy to decipher - too many questions on one page, there are many here who's first language is not English.

Many thanks for your detailed answers, I will post shorter threads in the future!

Now I only have to decide whether to stick with my 64-Bit installation or go for a 32-Bit one that might be easier to configure for someone new to Ubuntu and that might be more stable...?

---

### Post by Elfy on 2008-07-03
> If this is not a bug and won't be fixed in future updates I think I'll suggest to the developers to make this easier for the user...Don't think it's a bug 0 and would be the first place I would look myself - just for your information there is an excellent oo forum which I have used myself in the past.

> Tomboy Notes sometimes closes/crashesCan't help with that I'm afraid as I don't use it myself only looked for you, I will have a bit of a dig see if I can see anything possibly related.

> Hmmm... Not figured this one out yetDo Alt+F2, a gui will open - enter 
```
gconf-editor 
```
 in the run box of the gui and enter - a new app will open - this is gconf-editor, in the left hand pane open - apps, then nautilus and you will see desktop - should be able to follow pervious now.

---

### Post by indiworks on 2008-07-04
> **forestpixie said:**
>  Do Alt+F2, a gui will open - enter 
```
gconf-editor 
```
 in the run box of the gui and enter - a new app will open - this is gconf-editor, in the left hand pane open - apps, then nautilus and you will see desktop - should be able to follow pervious now.

Got it... It's on the desktop again, the strange thing is that it is still called "Deleted Items" and not "Trash" or "Wastebasket". (I choose: /apps/nautilus/desktop/trash_icon_visible - "If this is set to true, an icon linking to the wastebasket will be put on the desktop.")

Will investigate myself what this is about. Thanks for your time.

(I just saw that there is also /apps/nautilus/desktop/trash_icon_name and no value is assigned to it - this might be what I have to edit... But maybe there is really something wrong with my system and I'd better do a clean install and go for the 32-Bit version, will see...)

---

### Post by Elfy on 2008-07-04
Yea you can chnage the name there - dbl click the name value in the right hand pane.

---


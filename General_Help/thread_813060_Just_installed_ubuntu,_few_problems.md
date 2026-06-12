---
title: "Just installed ubuntu, few problems"
date: 2008-05-30
forum: General Help
---

### Post by kablack7 on 2008-05-30
Hey all, I just installed ubuntu 8.04 on my new laptop, because I was tired of Vista. I've been having a few issues though, and they are as follows:

1. I installed the beta-version (0.5) of Songbird, by Mozilla, because I like the layout. However, I don't know where it went... haha. The only way I can seem to start the program is from the original install folder that I unzipped. A shortcut for the program doesn't appear in the applications menu, and I don't know how to add it there. 

2. My F-Spot photo manager doesn't seem to be working... when I connect my digital camera, it asks me if I want to import the photos. I click on 'yes', and nothing happens. If I try to open f-spot manually, nothing happens. Is this a common problem?

I think thats it for now. I'm totally new to ubuntu, and I don't really know what I'm doing. I can use all the help I can get :)

Much appreciated!

---

### Post by pytheas22 on 2008-05-30
I'm not familiar with Songbird and I don't use f-spot, but here are some suggestions:

1. how did you try to install Songbird?  There's a guide [here]("https://help.ubuntu.com/community/Songbird"); if you use the first option (installing with a .deb), it should be very easy.  I don't know where it would be in the menu, but you can always open a terminal and type 'songbird'; if it's install correctly it should start that way.

2. when you plug in your camera, instead of telling f-spot to import the photos, tell it to do nothing.  Then click on the Places menu, open your Home folder, and in the left pane of the Window, you should see your camera listed.  Click on it and you should be able to browse to the location of your photos that way, and then copy them to the hard drive so that they can be imported into f-spot.  Picasa is also a decent alternative to f-spot, although it's not free (as in freedom) and Google refuses to make a truly native Linux version (instead it hacks the Windows version and wine together into a .deb and pretends to offer a Linux version).

---

### Post by jimv on 2008-05-30
If fspot isn't opening, a good way to troubleshoot it is to open a terminal and type in f-spot and see if you get and error message.

---

### Post by kablack7 on 2008-05-30
```
Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

```

I get the above error when I type 'f-prot' into the console. Any idea what it means?

I tried installing songbird with the .deb above, and that seems to have worked, sortof... I think the problem now is because songbird was already installed, how do I uninstall applications that aren't in the application menu?

---

### Post by latna on 2008-05-30
With regard to songbird, it sounds like you didn't install it into the system but instead downloaded an archive that contains an executable ready to be run. Firefox and thunderbird are the same way. You can download the program, extract it and run it where it is, with no need to install.

Ignore this if you actually ran an install program though.

---

### Post by jimv on 2008-05-30
Try this:

```
sudo apt-get remove --purge f-spot
rm -r ~/gnome2/f-spot
sudo apt-get install f-spot
```

---

### Post by zvacet on 2008-05-30
```
locate Songbird
```

---

### Post by pmaconi on 2008-05-30
To add Songbird 0.5 to a menu, right click the Applications menu and choose Edit Menus. Click Sound & Video in the left column. On the right of the screen press 'New Item.' Fill in all the fields (if you don't know the path to songbird offhand, click browse and find it. Press OK. Now it will be under Sound & Video in the Applications menu. Hope that helps.

If you want to uninstall the archived one, just delete the folder that you've been executing with. Note: I'm not sure that the .deb is the newest version, so I would just uninstall that and make a launcher to the one you downloaded off of songbird's website.

---

### Post by kablack7 on 2008-05-30
Wow, thanks for all the feedback. I got songbird working correctly, thank you.

However, I tried the code that jimv suggested, and purged and reinstalled f-spot. When I try to run f-spot from the terminal, however, I still get the same error... 
Any other ideas? Does anyone know what this error means? All that code is greek to me...

---

### Post by kablack7 on 2008-05-31
bump

---

### Post by pytheas22 on 2008-05-31
Try:

```
rm -rf ~/.gnome2/f-spot
```

Not sure if it will help, but someone with a similar problem mentioned it at [http://ubuntuforums.org/showthread.php?t=682128](http://ubuntuforums.org/showthread.php?t=682128) .

---

### Post by kablack7 on 2008-06-01
That worked!

Thank you very much everyone for your help.

---


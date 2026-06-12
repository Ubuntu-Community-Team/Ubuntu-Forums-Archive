---
title: "Firefox- Add File Type Association?"
date: 2007-08-19
forum: General Help
---

### Post by CheeseQueen452 on 2007-08-19
How do I add a file type association to Firefox? I had AVI listed in the prefs, but it disappeared. Maybe I deleted it by accident? Also, how do I set it to use a different plugin? It's set to use the vlc plugin, but it doesn't work. I think this is why streaming audio won't work at a certain website I go to. HELP!!

---

### Post by gobbles414 on 2007-08-19
Hi CheeseQueen452,

You might try right-clicking on an AVI file in Firefox and doing a "save link as". That might force a screen to appear asking if you want to open or save. There is a drop-down box by the open option that might give you the ability to have another program open the file.

Since the BEST plugin for Firefox is MPlayer, you might also want to make sure that totem-mozilla and mozilla-plugin-vlc have been removed from your system. I recommend using the following command in the terminal:

**sudo apt-get --purge remove totem-mozilla mozilla-plugin-vlc**

Then install mozilla-mplayer. This is most easily accomplished in the Synaptic Package Manager. You can also use _apt-get install_ in the terminal.

---

### Post by CheeseQueen452 on 2007-08-19
I attempted to play an avi file on my hard drive via Firefox(just out of curiosity), & it didn't work. It tried to use movie player(totem plugin). However, the file plays when I use the desktop player. Now that the avi format is no longer listed in the file associations, it asks me to either open or save the file. In fact, mpg or mov files won't play in Firefox either.

I also want to play the streaming audio at [http://regent.player.abacast.com/player/?pid=wlzw](http://regent.player.abacast.com/player/?pid=wlzw)
This also attempts to use the totem plugin, but it doesn't work. If there's any plugin that'll work, please let me know.

The mplayer plugin won't install. I've had too many problems with it to bother trying anymore.

> **gobbles414 said:**
> Hi CheeseQueen452,

You might try right-clicking on an AVI file in Firefox and doing a "save link as". That might force a screen to appear asking if you want to open or save. There is a drop-down box by the open option that might give you the ability to have another program open the file.

Since the BEST plugin for Firefox is MPlayer, you might also want to make sure that totem-mozilla and mozilla-plugin-vlc have been removed from your system. I recommend using the following command in the terminal:

**sudo apt-get --purge remove totem-mozilla mozilla-plugin-vlc**

Then install mozilla-mplayer. This is most easily accomplished in the Synaptic Package Manager. You can also use _apt-get install_ in the terminal.

---

### Post by CheeseQueen452 on 2007-08-19
Anyone?

---

### Post by HermanAB on 2007-08-19
You have to install 'mozplugger' using urpmi or mcc.  Once that is installed, restart Firefox and then the file association feature in the FF setup menu will magically work.  I think it is regrettable that Mandriva doesn't install this by default.  PCLinuxOS does.

Cheers,

Herman

---

### Post by CheeseQueen452 on 2007-08-19
I installed mozplugger, but still no luck. What's urpmi & mcc?

> **HermanAB said:**
> You have to install 'mozplugger' using urpmi or mcc.  Once that is installed, restart Firefox and then the file association feature in the FF setup menu will magically work.  I think it is regrettable that Mandriva doesn't install this by default.  PCLinuxOS does.

Cheers,

Herman

---

### Post by Yfrwlf on 2007-11-09
My solution was to do a complete removal of any mozilla-vlc or mozilla-totem packages, and then to install mozplugger.  After restarting Firefox, it comes up with a bunch more extensions in the file type menu.  It still does not let you add file types though, but if you do click on a file type it should ask to save it (instead of for example trying to play it using a plugin) and I think if you check the remember action for this file type checkbox, I *think* it will then make it appear in the Firefox file extension type action menu thing. :)

For any files that *are* in the list, you can either change them or leave them to open with Mozplugger, which will pass the file to the default application that is set in Gnome.  So, if you want them to open with a different external player at that point, change your default application settings.

But ya, for in-browser media players, Totem with Xine or better codecs for gstreamer will help, or mplayer or VLC may be better.

---

### Post by maestrobwh1 on 2007-11-10
"..but if you do click on a file type it should ask to save it (instead of for example trying to play it using a plugin) and I think if you check the remember action for this file type checkbox, I *think* it will then make it appear in the Firefox file extension type action menu thing. :)

For any files that *are* in the list, you can either change them or leave them to open with Mozplugger,"

**Okay so this is what you have to do for pdf files if you want them to** 
-show up in file type list
-change it to open in firefox rather than externally

-Find a pdf file online, it will ask you to open it in adobe [acroread] and click the 'remember' box.  
-Close the file
-edit-->preferences-->content: manage, pdf is now there, change to the mozplugger option.

There!  Whew.

---

### Post by Yfrwlf on 2007-11-15
> **maestrobwh1 said:**
> "..but if you do click on a file type it should ask to save it (instead of for example trying to play it using a plugin) and I think if you check the remember action for this file type checkbox, I *think* it will then make it appear in the Firefox file extension type action menu thing. :)

For any files that *are* in the list, you can either change them or leave them to open with Mozplugger,"

**Okay so this is what you have to do for pdf files if you want them to** 
-show up in file type list
-change it to open in firefox rather than externally

-Find a pdf file online, it will ask you to open it in adobe [acroread] and click the 'remember' box.  
-Close the file
-edit-->preferences-->content: manage, pdf is now there, change to the mozplugger option.

There!  Whew.

That's a really silly way of having to do it though, there should be an Add button if there is going to be a Remove button.  Guess I'll hit up the Firefox suggestions boards...

---


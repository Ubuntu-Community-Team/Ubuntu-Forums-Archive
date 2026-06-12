---
title: "Wine problem - can't run setup.exe"
date: 2007-08-19
forum: General Help
---

### Post by RudolfMDLT on 2007-08-19
Hi there,

when I try to run the setup for a game I get this error:

> rudolf@rh:/stuff/cnc$ wine setup.exe 
Warning: could not find DOS drive for current working directory '/stuff/cnc', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found
rudolf@rh:/stuff/cnc$ 



I have no idea what the missing module is! I have looked at the wine FAQ and found nothing, any help would be appreciated!

thanks!

---

### Post by gobbles414 on 2007-08-19
Hello RudolfMDLT,

Since you don't mention in your post the name of the game you are trying to install, it is difficult to give you any spacific suggestions. However, there are some general suggestions that I can offer:

1. Did you check to make sure that the game that you are trying to install is supported by Wine? You can do so [here]("http://appdb.winehq.org").

2. Change the version of Windows that Wine is emulating. This can be accomplished by going: system --> preferences --> wine configuration. It is also possible to launch this from the terminal by typing winecfg. I recommend Windows 98 or Windows XP for games. You may also wish to tell Wine to used emulated desktop graphics. This will make it easier to quit Wine should it ever freeze.

3. To get a later version of Wine than is normally available in Synaptic or add/remove, go: system --> administration --> software sources --> updates --> and select unsupported updates (backports). After running the update manager, you will have a newer version of Wine installed. Alternatively, you can use the official installer from the Wine home page and possibly get an even newer version of the program -- some warn that this is not recommended.

4. If you are trying to play a DOS game, use dosbox. A newer version of this is also available via backports.

5. If you are trying to install a newer game, chances are it will NOT work in Wine. Click [here]("https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems") for alternatives.

---

### Post by Nekiruhs on 2007-08-19
> **RudolfMDLT said:**
> Hi there,

when I try to run the setup for a game I get this error:



I have no idea what the missing module is! I have looked at the wine FAQ and found nothing, any help would be appreciated!

thanks!
You have to specify the full path to the setup.exe so use either wine /path/to/exe or cd /folder/with/exe && wine./setup.exe

---

### Post by UK-Wobbie on 2007-08-19
> **RudolfMDLT said:**
> Hi there,

when I try to run the setup for a game I get this error:



I have no idea what the missing module is! I have looked at the wine FAQ and found nothing, any help would be appreciated!

thanks!

Why not right click on the setup file and go to ( Open with: Wine Windows Emulater ) ? :)
Or if it's not there... Right click on the setup file and go to ( Properties-> Open With ) Then click on add and put in wine in low caps!

---

### Post by g2g591 on 2007-08-19
thats not the way you're supposed to do it, thats why, I had people telling me to use the terminal when I couldn't get a certain app to work.

---

### Post by UK-Wobbie on 2007-08-19
> **g2g591 said:**
> thats not the way you're supposed to do it, thats why, I had people telling me to use the terminal when I couldn't get a certain app to work.

So why will they put the open with: Wine Windows Emulater thing there if it was not? :)

---

### Post by RudolfMDLT on 2007-08-20
Hi guys!

Thanks for all the replies! :)

I'm trying to install Command and Conquer 3: Tiberium wars.


[http://appdb.winehq.org/appview.php?iVersionId=7440](http://appdb.winehq.org/appview.php?iVersionId=7440)
As you can see it is supported.

I'm running the latest wine.

winecfg is set XP

Here is a terminal command pointing wine at the file from /

> rudolf@rh:~$ wine /stuff/cnc/setup.exe 
Warning: could not find DOS drive for current working directory '/home/rudolf', starting in the Windows directory.
wine: cannot find '/stuff/cnc/setup.exe'
rudolf@rh:~$

And right-clicking on the file and clicking the windows emulator option, only brings up a dialog in the taskbar for about 5 seconds and then disappears. 

I know that this should work because I did the install 3 days back. I also had to reformat 2 days back so I'm starting from scratch now! :)

Thanks for the help thus far!

Rudolf

---

### Post by RudolfMDLT on 2007-08-20
Wine doesn't run anything! :(

> rudolf@rh:~$ wine /stuff/Mathworks\ Release\ 14/Installer.exe 
Warning: could not find DOS drive for current working directory '/home/rudolf', starting in the Windows directory.
wine: cannot find '/stuff/Mathworks Release 14/Installer.exe'
rudolf@rh:~$ 


above is another executable -  wine just doesn't graft! is there any way to completely remove wine and all it's settings? I've tried the COMPLETELY REMOVE option in Synaptic but when I reinstall wine my settings are still there?

---

### Post by RudolfMDLT on 2007-08-20
The pas two or three threads about my system crash and Wine problems I keep talking to myself! LOL!

removed the .wine folder and reinstalled wine. works! Now to see if I can get the game to work!

---

### Post by RudolfMDLT on 2007-08-20
SWEET! :guitar::lolflag::guitar::lolflag:

See attached file! :)

Just for completeness:

In wine it seems you need to have two drives defined:

c:\ - which points to  where you want something installed
d:\ - which is /

d could be anything though but it seems that wine MUST have the / drive in there for some reason.

Cheers ,

Rudolf

---


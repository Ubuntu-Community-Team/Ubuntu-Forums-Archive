---
title: "vmware-player traps me in fullscreen mode in Gutsy"
date: 2007-11-12
forum: General Help
---

### Post by ryan408 on 2007-11-12
Hi All,

I've tried searching for an answer to this problem, but no luck so far.  Sorry if this has already been answered elsewhere.

I am using vmware-player to run a WinXP virtual machine.  Player starts in fullscreen mode.  If I hit Cntl-Alt to exit fullscreen mode the window resizes for a split second and then reverts to fullscreen.  The only way I can get out to exit vmplayer is to hit Cntl-Alt and very quickly hit alt-tab or alt-space-n to minimize the window.  It always takes a few tries and is very frustrating.  

Has anyone else experienced this problem?  Have any ideas?  This glitch is severely hurting the wife-acceptance-factor level of switching to Ubuntu, so I'm hoping I can get it resolved to bring peace back to the office.  :)

Thanks much,

Ryan

---

### Post by kbracer on 2007-11-12
I believe this is a Compiz related issue and has also been reported by people using the Remote Desktop client. Not aware of a solution, but thought I would throw out that tidbit of info.

---

### Post by ryan408 on 2007-11-12
How do I know if I'm using Compiz?  I have a very old graphics card that I don't think will support the special effects.  I'm not even sure how Compiz works, but that's a whole different story.

Isn't Compiz disabled if your graphics card won't support it?  Or am I totally exposing my ignorance here?

---

### Post by fjgaude on 2007-11-13
It might work to get a menu to just move the mouse to the top of the screen...

---

### Post by ryan408 on 2007-11-13
Thanks for the idea.  I started my VM again and increased its screen resolution so it took up my whole desktop in fullscreen mode.  Previously there was a black border around the outside in fullscreen mode. 

However, when the VM takes up the whole screen in fullscreen mode and I move the mouse to the top of the screen, the little menu bar does not drop down as I would expect it to.

---

### Post by Kalli on 2007-11-17
I'm having the same problem...

---

### Post by ryan408 on 2007-11-17
This problem has been resolved.

Not sure of the fix, but I started having a problem with vmware-player not starting.  I started it in a terminal session and was told I needed to re-run the vmware-config.pl script.  I did that and now the fullscreen trapping mode is gone.

---

### Post by fjgaude on 2007-11-18
Wonderful...

---

### Post by ryan408 on 2007-11-18
Well, unfortunately the problem is not really solved after all.

Something else has happened now where vmplayer won't run when I boot up my Gutsy system until I 'rm /etc/vmware/not_configured'.  Then it runs, but it traps me in fullscreen mode again.

If I run the /usr/bin/vmware-config.pl script all over again and let it recompile kernel modules like it wants to, then I can run vmplayer and get out of fullscreen mode at will.

So I think I may have multiple vmplayer problems converging here.  Anyone have any suggestions?  Nuke the whole vmplayer install and try again?  And why won't the kernel modules load until I recompile them now?  

Thanks,

Ryan

---

### Post by malfist on 2007-11-18
You can turn off compiz by going to System->Preferences->Apperance and setting special effects to None.

---

### Post by fjgaude on 2007-11-18
> **ryan408 said:**
> Well, unfortunately the problem is not really solved after all.

Something else has happened now where vmplayer won't run when I boot up my Gutsy system until I 'rm /etc/vmware/not_configured'.  Then it runs, but it traps me in fullscreen mode again.

If I run the /usr/bin/vmware-config.pl script all over again and let it recompile kernel modules like it wants to, then I can run vmplayer and get out of fullscreen mode at will.

So I think I may have multiple vmplayer problems converging here.  Anyone have any suggestions?  Nuke the whole vmplayer install and try again?  And why won't the kernel modules load until I recompile them now?  

Thanks,

Ryan

Might be a good idea to completely removed all things associated with vmware and start over. Might save some time instead of trying figure out what is wrong. Remember that means getting rid of all the config files. I would use Synaptic and after uninstalling vmware, I'd set it to Status and Not installed (residual config) and Make For Complete Removal all things that are vmware. Then reinstall.

---

### Post by fjgaude on 2007-11-18
> **malfist said:**
> You can turn off compiz by going to System->Preferences->Apperance and setting special effects to None.

That could be an issue... I don't use special effects... just too much!

---

### Post by ryan408 on 2007-11-18
OK, checked if compiz was running, and effects are disabled already, so Compiz should be disabled.

---

### Post by todb on 2008-04-09
Dunno if this is helpful but I ran into a similiar problem -- set a vmware image to full-screen, and could never escape. What worked -- rename the directory in which the full-screen-trapped image is held. iow, if your VM image is in:

/home/username/vm/winxp

quit the vm (hover near the top of the screen to get the quit button, or just killall like a psychopath) change the name to

/home/username/vm/winxp-freeatlast

or whatever, and that clears the "trap me in full screen" bit. I have no idea why that works -- grepping through /etc and /var for my original dirname turns up nothing (it has to be stored somewhere, though, so editing where its stored would probably be a better solution).

Naming it back to the original name with restore the fullscreen hell.

hth.


When I was full-screened on a laptop, I was able to restore to a normal window, but not when I was on an external monitor. And this never came up when I was vm'ing ubuntu on winxp.

---


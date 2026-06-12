---
title: "Firefox 2 No Title Bar"
date: 2008-06-11
forum: General Help
---

### Post by Enochuout on 2008-06-11
I'm running Ubuntu 8.04 and have removed Firefox 3 and installed Firefox 2 in its place. The installation worked fine for almost 2 weeks; however, it became problematic the other day. It now opens in fullscreen with no title bar. I'm unable to resize it at all and it covers the entire screen including my panels. It also occasionally flashes completely black. It is only Firefox that does this, all other windows display perfectly. I've attached a screenshot of what the window looks like. If anyone has an idea of how to fix this, any help would be greatly appreciated. Thank you.

---

### Post by Bubba64 on 2008-06-11
I think you have the window at full screen but I can't remember the the key sequence to bring it back. Hopefully somebody will find the problem or if this is the problem post the sequence.
[http://www.mouserunner.com/FF_Tips_Full_Screen.html](http://www.mouserunner.com/FF_Tips_Full_Screen.html)
[http://ubuntuforums.org/showthread.php?t=798151](http://ubuntuforums.org/showthread.php?t=798151)
[http://ubuntuforums.org/showthread.php?p=4695522](http://ubuntuforums.org/showthread.php?p=4695522)
here are some links f11 will make it full screen and back to normal try that 1st to see if it resets.

---

### Post by gustabuntu on 2008-06-11
Hi. If I understand correctly, the browser is in full screen mode. The key F11 sets and removes that effect.
Gustavo

---

### Post by Enochuout on 2008-06-11
Thank you both for the suggestions. The F11 key worked. I apologize if I wasted your time, but I'm very grateful, this was a nuisance.

---

### Post by Bubba64 on 2008-06-11
Hey no nuisance to me, it was good information for me to.

---

### Post by liquidchrome on 2008-06-11
shoot... helped me out too. thanks

---

### Post by nazgul42 on 2008-09-14
Good info, thanks.
I messed up my computer a few times trying to fix this... thought it was the window manager or something with the hardware driver, turned out I just needed to hit F11 twice...

---

### Post by duo001 on 2008-09-22
I am having this problem as well. 
I found that if you hit F11 twice, once puts it in true full screen, and the second fixes the window, and you have the title bar back.
There is just one problem with hitting the F11 key twice: that is not a real fix. That is a workaround.
Hopefully someone will give an answer that will actually fix the issue, not just a half-a$$ed workaround. 
I am going to be uninstalling firefox tomorrow, and will post the results. 
Hopefully they are good results. We will find out.

---

### Post by duo001 on 2008-09-22
OKAY, I may have found a nice solution. I disabled all of my add ons, opened up firefox, and it was fine, I had my title bar back. 
I then re-enabled them all, and it was still fine. Must have been something with one of the programs mucked up something. 

But at least this works, and you don't have to do this _EVERY_ time you open the program.

Try this, post if it gave yo a permanent solution.

---

### Post by 30mil on 2008-11-28
I have a fix that worked for two separate computers with the same problem.
With Firefox not running.

Make a back-up of ~/.mozilla/firefox/"your profile folder"/localstore.rdf

Then delete the original file.  

Start Firefox. This worked on both computers running different versions Ubuntu/firefox. Seems the file gets recreated automatically with no discernible consequences.

---

### Post by seniorheff on 2009-02-08
better solution from [http://ubuntuforums.org/showthread.php?t=836916:](http://ubuntuforums.org/showthread.php?t=836916:)

This is a problem that apparently is a conflict with FF and Compiz. Try "Alt-F2" to bring up the "Run Application" box and type in (without the quotes): "metacity --replace" and see if that restores the title bar. "compiz --replace" restores the eye candy and unfortunately the problem.

Thanks BGrigg

---

### Post by duo001 on 2009-04-04
It has been a while but I got this problem again. This time I didn't want to loose all of my data, ie saved passwords, so I found the one file that is the cause. Go into your `/.mozilla/firefox/profile folder/ and remove the localstore.rdf file.

---

### Post by elluce on 2009-05-19
When you delete localstore.rdf you will loose all firefox window settings (like toolbars settings). What you have to do is rename localstore.rdf and open firefox. Set the size of the window and close firefox. Using gedit open newly created localstore.rdf and find something like <RDF:Description RDF:about="chrome://browser/content/browser.xul#main-window". It will be on the begenning of the file. Copy screenY="", screenX="", width="", height="", sizemode="" values and paste it in the same place in previously renamed localstore.rdf. Delete new localstore.rdf and rename back old one. Voila!

---

### Post by iGoR83 on 2010-06-01
> **elluce said:**
> When you delete localstore.rdf you will loose all firefox window settings (like toolbars settings). What you have to do is rename localstore.rdf and open firefox. Set the size of the window and close firefox. Using gedit open newly created localstore.rdf and find something like <RDF:Description RDF:about="chrome://browser/content/browser.xul#main-window". It will be on the begenning of the file. Copy screenY="", screenX="", width="", height="", sizemode="" values and paste it in the same place in previously renamed localstore.rdf. Delete new localstore.rdf and rename back old one. Voila!
I already thought that there were no fix like this, 'cause I didn't want to lose all my FF window settings etc. Also minimazing/maximizing/unmaximizing didn't do the trick for me, it worked just until restarting my laptop... So thanks for this! I'm hopeful that this solved the problem for me.

BTW I'm using UNE 10.04 and FF 3.6.3.

---


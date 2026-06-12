---
title: "Dapper Drake: No Screen!"
date: 2007-06-05
forum: General Help
---

### Post by gottatrieit on 2007-06-05
I need some major help!
	I recently downloaded Compiz to use in my computer.  I have followed the installation instructions as close
as possible, I don't believe I've deviated from them at all.
	I'm using Dapper Drake 6.06
	My problem is this:

	I can only boot up in the terminal screen, no mouse, no screen borders, etc. Just a blank, black screen with the cursor and the command line:  gottatrieit@ubunut1:/$.  When I put in the commands, they work fine, but once the screen fills up, I cannot see the next line to input my commands!  How do I increase/decrease the window size to fit all of the screen into a useful mode?  As it is now, I have to hit <enter> several times to know that the computer is ready to accept another command and then blindly type it in as I cannot see the input directly until after I hit the <enter> key!
	Any help or advice at this point will be greatly appreciated.

		Thanks,
			gottatrieit

---

### Post by steveneddy on 2007-06-05
You are on a laptop or desktop?

If it is a desktop you can adjust the screen size from the buttons on the monitor. Right?

Or even then, the displayed monitor letters go over the edges? 

I can't seem to word the question correctly to try & help.

Can you describe in more detail what the problem is?

And what method exactly did you use to install Compiz?

---

### Post by Wim Sturkenboom on 2007-06-05
Just a workaround; use the command *clear* to clear the screen and you start from the top again. Please note that it's a **workaround**.

---

### Post by gottatrieit on 2007-06-06
1.) When I boot up, the machine automatically goes to the text screen (?). No graphics what so ever.  Just black, blank screen with the following on it :   gottatrieit@ubuntu: /$
   2.) At this point, I enter my commands and the screen displays them and the results.
   3.) When the screen fills, there is no further room for anything.  To enter any command, I cannot see the next line as the screen will not scroll. 
   4.) I have to hit <enter> at least twice to bring up the bottom of the screen so I can see where I'm at, even then, if I enter a command, it is not seen until after I hit the <enter> key.
   5.) When I enter <clear>, the screen will go blank.  I have to hit <enter> at least once to bring up the command line intro: gottatrieit@ubuntu:/$
   6.) Using the monitor controls doesn't help.  I can't resize the screen, which what I'd like to do.  For instance, maybe increase from 800x640 to 1024x728, etc.
    I'd like to give you better information, but that is the best I can describe it.
    I really don't want to wipe my hdd and start all over as I've got my system set where and how I want it.  (I've already goofed several times and had to redo everything from scratch, I don't want to do it again unless it's a last resort type situation!  :(:icon_frown:)

---

### Post by Wim Sturkenboom on 2007-06-06
Did you try to specify a video mode 'in' grub? Search the web or the forums here. Can't help you but can remember that I saw it somewhere.
That might fix your console screen.

I guess you want your normal GUI back. I don't know how Compiz affects xorg.conf, but you can try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Crafty Kisses on 2007-06-06
> **gottatrieit said:**
> 1.) When I boot up, the machine automatically goes to the text screen (?). No graphics what so ever.  Just black, blank screen with the following on it :   gottatrieit@ubuntu: /$
   2.) At this point, I enter my commands and the screen displays them and the results.
   3.) When the screen fills, there is no further room for anything.  To enter any command, I cannot see the next line as the screen will not scroll. 
   4.) I have to hit <enter> at least twice to bring up the bottom of the screen so I can see where I'm at, even then, if I enter a command, it is not seen until after I hit the <enter> key.
   5.) When I enter <clear>, the screen will go blank.  I have to hit <enter> at least once to bring up the command line intro: gottatrieit@ubuntu:/$
   6.) Using the monitor controls doesn't help.  I can't resize the screen, which what I'd like to do.  For instance, maybe increase from 800x640 to 1024x728, etc.
    I'd like to give you better information, but that is the best I can describe it.
    I really don't want to wipe my hdd and start all over as I've got my system set where and how I want it.  (I've already goofed several times and had to redo everything from scratch, I don't want to do it again unless it's a last resort type situation!  :(:icon_frown:)

Did you try installing any Video Card drivers?

---

### Post by Feba on 2007-06-06
Oh dammit, I saw this same problem on a mailing list a couple days ago, someone found a command that made the terminal not go off their screen (it was debian, but I imagine it was the same problem), I really wish I could remember it right now.

---

### Post by Crafty Kisses on 2007-06-06
> **Feba said:**
> Oh dammit, I saw this same problem on a mailing list a couple days ago, someone found a command that made the terminal not go off their screen (it was debian, but I imagine it was the same problem), I really wish I could remember it right now.

Haha, let me try to find it.

---

### Post by gottatrieit on 2007-06-06
Codename:  RE ------ my post ----------   Yes.
     I'm trying to repair my desktop.
     I followed the steps here: [http://www.compiz.org/NVidia](http://www.compiz.org/NVidia). 
     One step I skipped 'cause I couldn't get gedit to work right was the  "Disabled_Modules="nv".
     I did reboot and went to the next step and after several tries and referring to the  man pages, I finally got this part taken care of up to the the "gcc gcc-3.4 xserver-xorg-dev" command. I don't remember now what happened as I have been plugging away at it off and on for two or more days now, plus trying to cope with a text screen that is too large or too small, I'm not sure which! lol
     I followed through with the rest of the stuff from this site and it seems to have gotten installed.
     Whatever "gcc" is , though, I don't know and I don't know how to configure it.
     I also tried to edit "xorg.conf", but the corrections weren't accepted for some reason; possibly because I didn't have a proper editor application opened??  :confused:

Wim Sturkenboom:

        I will try that to see what happens.  I had forgotten that command! Thank you.

---


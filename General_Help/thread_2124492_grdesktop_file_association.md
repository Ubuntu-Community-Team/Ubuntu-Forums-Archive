---
title: "grdesktop file association"
date: 2013-03-11
forum: General Help
---

### Post by kestrel1 on 2013-03-11
I am using Ubuntu 12.04 & am using grdesktop to RDP to various servers.
To make life easier I have saved the configuration files, but if I double click on the files, they open in gedit. I would like to be able to associate these files with rdesktop, so that when I double click them they would run rdesktop & open the servers.
I have tried Ubuntu tweak, but cannot see anyway to associate these files as I cannot see a file extension on them.
I looked at assogiate, but couldn't make head nor tails of it.
Why have they removed the abbility to add custom commands to associate a file in Gnome? It is stupid & short sighted.
Please help. I love using Ubuntu at work & am not wanting to go back to Windows.

---

### Post by kestrel1 on 2013-03-11
Any ideas?

---

### Post by kestrel1 on 2013-03-11
I take it that no one has a clue then. Glad it isn't just me.

---

### Post by cortman on 2013-03-11
First: Be patient. This is a volunteer forum. No one here gets paid for offering their help.
[snip]
As far as your problem, I don't really know of any way to associate an individual file with a program. File/program association typically is for file type (i.e., all files of a certain extension) not for individual files.

---

### Post by QIII on 2013-03-11
We are a world-wide community of volunteers, here on our own time as we have the time.

It may be that the person with the best answer lives in Bangalore or  Tunisia and is either at work, having dinner, playing with the children  or talking to parents on the phone right now.

Please do not take the lack of an answer within an a few hours as a snub  or an indication that nobody wants to help.  It is simply a function of  who is here when with a good answer.

If you would, please give the community some time to address your valid  concern.  The lack of an answer just means that the person with an  answer has not seen your post.  Wait to bump for 24 hours.  An odd bump at 36 hours might catch someone who is on the other side of the world at a time when he or she is on the forum.

Thanks, and be patient.  Someone will help.

---

### Post by kestrel1 on 2013-03-11
As I have been a member since 2007, I think I am aware that this is all done on a volunteer basis, so do not really appreciate the sarcasm that I felt in that message.
With regard to the spelling, I was not using my usual machine that has a spell checker & my spelling is not good at the best of times as I am a bit dyslexic, so I do apologise for that at least.
I know I will get an answer if someone knows the answer. The questions I ask are normally a bit above the average users knowledge & do not normally get answered. 
If this sounds ungrateful, it is not meant to as I know only too well how much time & energy goes in to these things, as I normally help anyone out & all for free. I do not expect an immediate answer.

---

### Post by rnerwein on 2013-03-11
hi
i don't know if this a solution for you. i named my files which i want to execute with the ending xxxx.desktop. the contens of the file is:
[Desktop Entry]
Version=1.0
Name=bash
Comment=back to the roots
Exec=/bin/bash
Icon=/home/richi/desktop/face-cool.png
Terminal=true
Type=Application
Categories=Utility;Application;

place your configurations in a folder and then you can double-klick on the file and the command: Exec will be executed
cheers

---

### Post by cortman on 2013-03-11
> **kestrel1 said:**
> As I have been a member since 2007, I think I am aware that this is all done on a volunteer basis, so do not really appreciate the sarcasm that I felt in that message.
With regard to the spelling, I was not using my usual machine that has a spell checker & my spelling is not good at the best of times as I am a bit dyslexic, so I do apologise for that at least.
I know I will get an answer if someone knows the answer. The questions I ask are normally a bit above the average users knowledge & do not normally get answered. 
If this sounds ungrateful, it is not meant to as I know only too well how much time & energy goes in to these things, as I normally help anyone out & all for free. I do not expect an immediate answer.

No offense meant; I apologize for sounding sarcastic. Too many people come here with an entitlement complex which they often show in bumping and re-bumping their thread, and while bumping is fine, forum rules recommend you wait at least 24 hours between bumps, whereas you bumped twice in about 8 hours. 
Good English can be tough but it helps to make posts clear and concise; I will amend my original recommendation.
It appears rnerwein may have some helpful information for you in the post above.

---

### Post by kestrel1 on 2013-03-11
Thanks rnerwein,
I will have a look at this, but at present I am a bit confused by what you have said. It may become clearer when I get up in the morning. Having been at work all day & coming home to continue working I am getting a bit tired.
I will get back to you on this.
Thanks

---

### Post by kestrel1 on 2013-03-11
> **cortman said:**
> No offense meant; I apologize for sounding sarcastic. Too many people come here with an entitlement complex which they often show in bumping and re-bumping their thread, and while bumping is fine, forum rules recommend you wait at least 24 hours between bumps, whereas you bumped twice in about 8 hours. 
Good English can be tough but it helps to make posts clear and concise; I will amend my original recommendation.
It appears rnerwein may have some helpful information for you in the post above.
Hi Cortman,
I am not one to take offence easily, maybe it is because I am tired :)
I definitely do not come here with any sort of entitlement complex & I really appreciate everyone's time. Sorry for re-bumping & I will remember to be more patient. It may have been that it seemed like a long day :)
I do normally try to use a spell checker, as my typing & spelling is often bad. I blame my teachers from many years ago :) They never used to pick up on dyslexia like they do now. I have only become aware of this, because I work in education & have recognised many things in myself that they now pick up on. Although for me it is very mild & would mostly be classed as dysgraphia.
None of this is an excuse for bad English though. 
Thanks for keeping an eye on us all.
Cheers
Kestrel1 
A.K.A Glyn

---

### Post by kestrel1 on 2013-03-12
I have looked at the above from rnerwein, but it will not help with what I want to be able to do.
However it is a good solution for adding a program launcher to the desktop.
Maybe I need to wait & see if Gnome is fixed to allow the changing of the default program on files.
Once I find the solution I may well post it. I will close this post for now.
Thanks to all that helped & commented. :)

---

### Post by cortman on 2013-03-12
What if you would give the grdesktop files a custom extension (rename it mygrdesktop.dskt or something) and then right click>open with> select the program you want, and say open all files of this extension with this program? Might be worth a try. :)

---

### Post by kestrel1 on 2013-03-12
I have got it working some what, so will leave it like that.
Thanks for the input.
I have been unable to find a way to mark the thread solved. I know the option used to be on here, but since the change I have been unable to find it. Is it hidden or has it yet to be added?
Cheers

---

### Post by cortman on 2013-03-12
Glad to hear it's *sort of* working. :)
You used to be able to mark a thread [SOLVED] using the thread tools which are located in the upper right, not sure if that has been re-enabled with the new forums or not.

---

### Post by kestrel1 on 2013-03-12
No, unfortunately the option does not appear there, as I looked earlier & just now to make sure.
Apparently it should be in the advanced editor, but is not appearing for me:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---


---
title: "[SOLVED] Error: Cannot open VTS_01_0.VOB Is Making me crazy!!"
date: 2007-12-12
forum: General Help
---

### Post by concerto on 2007-12-12
OK,  I'm going crazy!  I buy a Brand spank in new Dell computer and I can't watch DVD's.  I know. I know.  Everyone has heard this one before.  Am I right?  So I do Lots of research on the problem and cant find anything so here I am pulled over and asking (begging) for directions.

This is what I have done so far:

- Went to Ubuntu Help and support
- I Installed the following packages in add/remove programs.
		
          * gxine  I installed this program which works but not on store bought DVD's. _also vlc media player Isn't helping me either_
          * libdvdnav4
          * libdvdplay0
          * libdvdread3

- I typed this in the terminal and the code worked.      (in the Gnome-terminal)

      sudo /usr/share/doc/libdvdread3/install-css.sh



      In the Command box under Video DVD Discs, type “gxine -S dvd:/” (without quotes) and then press Close.

      			-I did this and it saved but the player dosen't auto open when I insert a DVD.	





_This is the Error that I keep getting when I try to open DVD files:_

Error Message

Cannot open VTS_01_0.VOB


The filename "VTS_01_0.VOB" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


I'm begining to think my dvd player is broken...
What do you guy's think?

Who ever helps me before I go Insane will get what ever they want.  (with in reason)

---

### Post by rbmorse on 2007-12-12
[www.medibuntu.org](www.medibuntu.org)

Go to the "add repository" section and scroll down to the 7.10 section. Do what it says. 

Once medibuntu is in repository, use synaptic to install 

libdvdcss2

note: I live in the U.S. so it's against the law for me to install that particular package.  I'm told it is necessary to view encrypted DVDs and also that it works pretty well.  Not, of course, that I would know from personal experience. 

also in synaptic

ubuntu-restricted-extras

or if you don't want java and flash, then search on gstreamer0.10-plugin and install the base, good, bad and ugly packages.  

Restart the session and see if movie player or VLC will open the folder that holds VTS_01_0.VOB

---

### Post by concerto on 2007-12-13
Hey, thanks for the advice.  I will try your advice later.  I live in Pennsylvania and I will probably be shoveling snow all day but when I get some time later i will try it and then I'll get back to you.

Just to give you more information:
If I put an illegally copied CD into my computer it works fine.  no problems.
If i put a movie that i get  from like blockbuster, it doesn't work.  It's so weird.
any way.  I wont waist anymore of your time.  I'll get back to you and let you know later If it works.

---

### Post by concerto on 2007-12-13
Why isn't the link to Medibuntu given to you when you go to the help file in Ubuntu?  I feel bad that I had to bother you.  I'm sure other people had this problem also.  Anyway, I can't thank you enough for what you did.  I owe you big time so you just name it and you got it.  If I can do anything at all for you I will do it.  Thank you so much for your help.

PS.  right now when I want to watch a DVD movie i have to double click the icon and then go to the video ts folder and choose a program to run the video like vlc.

Do you know how to set vlc as my default video player? and do you know how to make my computer auto run a DVD movie?

---

### Post by rbmorse on 2007-12-14
I would not know anything about opening illegally copied material.  I consider that anathema and urge everyone to observe the provisions  and restrictions of any copyrighted material they encounter.  And, to pick up litter and be kind to animals (except cats). 

It is possible, however, that the dvd was copied with an application that automagically strips the copy protection schema off the dvd while it is copied. I'm told such things exist.  I could not say if things like anydvd or dvdfabdecrypter, or dvdshrink really work like that, and no interest in finding out, since they all run under windows and I don't have windows installed anymore.  Nor can I tell you if the linux application k9copy works for that purpose either.  In fact, if it were up to me, I probably would think about removing k9copy from the multiverse repository. 

The link to Medibuntu isn't included by default to avoid potential legal problems resulting from the the wording of various copyright laws in the U.S and Germany.  We certainly would not want Ubuntu or it's commercial sponsor, Canonical Ltd,  to have to deal with that, would we?  Also, some of the material on the Medibuntu site may not be compliant with Ubuntu's stated desire to minimize use of proprietary or otherwise non-GPL software to greatest extent possible and sill have the machine function within reasonable expectations.   

As I noted in my previous post, actually installing the file libdvdcss2 may constitute a violation of the DMCA, and because of that I most emphatically do not recommend anyone living in the U.S or Germany do so. Of course, you are free to exercise your own personal judgement, and also to confound cats whenever you feel like it. 

As for the rest, I'm sorry that I can't help. You might try the mulltimedia forum  on this site and search for "autorun dvd" or something like that.

---


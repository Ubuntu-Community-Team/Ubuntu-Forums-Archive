---
title: "strange firefox browser thing"
date: 2023-08-29
forum: General Help
---

### Post by jgw on 2023-08-29
Everytime I bring up firefox, for the first time, I am gifted with two unknown things (I think they are "web" and something else (should have written them down).  Then, I quit that one and do it again and it works fine.  I have no idea why this is happening.  I have checked the settings and there was nothing there that might help.

After I wrote the above I went to settings, again, and, this time, I went to the end of how the home screen was setup.  It listed the three things I wanted and then there was (I'm not kidding) a 100 character something there that, I assume, were the culprits.  I will not know for sure until I shut this down and then do it again.

It did it again, after I re-booted.  This time I got the two things that it was trying for as if they were addresses: "web" and "browser".  Have no idea where its coming from.  Checked the settings and nothing there qualifies. 

Should ad.  I also went to mozilla/firefox to whine at them.  Spent almost an hour trying to figure out how to post on their forum or whine anyplace.  I failed.  Its the most confusing and waste of time I have ever spent.  I can remember when one could easily do that - no more, they seem to have 'fixed' it and now its some kind of secret in a huge set of pages that say very little but are very colorful.

Thoughts?

---

### Post by Frogs Hair on 2023-08-29
> I am gifted with two unknown things (I think they are "web" and something else (should have written them down)
Sorry, I'm having a little trouble following your post. Is this a message or a popup that you can take a screen-shot of ?

---

### Post by jgw on 2023-08-29
just a question.  Firefox starts, after a boot, with two things that it cannot find because they don't exist.  I just quit firefox and restart and everything is dandy and the bad addresses go away.  The first address is 'web' and the second is 'browser'.  Its just the way my firefox starts.

In passing I have been meaning to ask if I should delete all the photos that I have (4 pages of them that I have accumulated over the years)  I haven't checked but, I think, there is a way to get that done.  I can see no reason not to do that as they are of absolutely no use to anybody.

---

### Post by Rubi1200 on 2023-08-30
Have you checked your network settings?

Could it be a corrupted Firefox profile?

Is this a snap and has it been updated recently?

---

### Post by jgw on 2023-08-30
I deleted firefox.  I found that it was installed two times.  Once in snap and once not.  I then removed everything to do with firefox.  then I re-installed it.  Same problem!  I also find that there is something that is slowing down everything for no reason. I wonder if there is any way I can find out what is going on.  When I was getting rid of firefox files, for instance, it took about a half an hour to remove all the files (there were a LOT of files).  When everything was working I downloaded a lot of nzb files and had sabnzbplus dealing with those.  I suspect something went wrong with that.  I have stopped sabnzbplus and moved all the files it was working on to a usb stick and removed the stick.  Hasn't made any difference.  I have strange things happening.  For instance, when its doing something I get a message that gives me two choices, stop whatever or wait.  That happens with almost everything that is doing something.  I have used the system monitor to see what is running and it all seems normal.  

Its driving me crazy.  I am about ready to put a new ubuntu on a different boot ssd and put that in the computer and that will, hopefully, fix the problem and then all have to do is re-populate it and, that, hopefully will fix the mess.

Any thoughts on this one would be appreciated.

---

### Post by Holger_Gehrke on 2023-08-30
Did you edit the desktop file for Firefox (/usr/share/applications/firefox.desktop) or create a personal desktop file (~/.local/share/applications/firefox.desktop) ? If you edited that file and made a mistake with copy and paste it would explain that behaviour because I can get the same effect you get by starting Firefox from the command line with 'firefox web browser'. It interprets the text as two separate URLs which obviously don't exist. Take a look at the contents of the .desktop file and specifically the line starting with 'Exec='. It should say 'Exec=firefox -new-window'.

Holger

---

### Post by jgw on 2023-09-02
I just re-did my entire system and firefox is no longer mis-bahaving (so far)  will mark this as solved...........

---


---
title: "errors after shutdown on multiple users"
date: 2006-12-09
forum: General Help
---

### Post by fazza on 2006-12-09
yesterday I was logged on to my user name (obviously) on our computer, to do some work, using Gimp and openoffice. We all (in our family) have separate user accounts, so when my mum came upstairs to check her mail, she had to switch user. When she had finished, she shut the computer down without realising I had not saved my work. This may not have anything to do with the problem I'm about to explain, but it might. 
     I logged on tonight, and the pc made its little noise to tell me it was ready to log on. I logged on, and it took ages. Then the music that normally plays while logging in didn't play. I turned the volume (that was on the speaker itself) right up and there was only a buzzing sound. Then it asked me for my password to run firestarter, our firewall. I have got this set up to start when I log in, with ```
gksu firestarter
```. It returned with the error message: 

[CENTER]Failed to run firestarter

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/CENTER]

I happen to be the second administrator of the computer. So I logged in as my mum, wanting to check out the privileges, thinking that maybe a  bad shutdown had changed what I was allowed to do. This was only based on the fact that many of the programs I also run are sudo based. My mum also had the same problem. 
     The second thing I noticed was that the sound was muted. Normally if the sound is muted, the login doesn't sound. I clicked it, and it came up with:

[CENTER]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
[/CENTER]

This was also the case on my mum's username, proving that it wasn't another access right I didn't have. This was now annoying me, so I thought I'd double check the user rights.
    I went to click the 'System' button at the top of the screen and accidentally clicked 'Applications' (I move my mouse quite fast). I saw that 'Add/Remove Applications' was missing, and several other menu entries  were missing, such as the Debian Menu. I went into Alacarte Menu Editor, and some were actually unchecked. Some of the entries, however, were still checked, but did not appear in the actual menu. The Debian Menu did not let me tick it, leading me to think that it no longer exists.
    I was now thoroughly confused, so I rebooted the computer. There were still all the same problems. I am now extremely vulnerable to hackers - the list that appears in firestarter shows that it has blocked many dangerous attacks, all of them http based (as in not samba or any others). I cannot even access the User settings as they are not in the menu. Clicking the link in Ubuntu Control Center doesn't work either. HELP!!!!!

Sorry if this reads very long, but if you can help, please do. Also, I had to make up a few words to describe where I was, so you'll need to guess what they mean!

I think that is all, although I will probably think of something else in a minute.
fazza:-|

---

### Post by fazza on 2006-12-09
*huff* and how do I add myself to the sodoers list...?

---

### Post by Malakia on 2006-12-09
What you need to do is check your system logs if you have access to them also disconnect from the internet until you resolve the problem. That way you don't have to worry about hackers. If you still can't figure out the problem your best bet is to completely wipe the harddrive out that way if somebody actually did hack your computer they no longer have access and reinstall Ubuntu.

---

### Post by fazza on 2006-12-09
*screams*  where's my system logs?!

---

### Post by Malakia on 2006-12-09
they are located in /var/log/, go to that directory and then issue "ls" in the command line and go through and check each log for anything suspicous. you can check each one by using **vim /var/log/* **

---


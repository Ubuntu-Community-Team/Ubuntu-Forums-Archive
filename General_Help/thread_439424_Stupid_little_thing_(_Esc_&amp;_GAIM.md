---
title: "Stupid little thing :( Esc &amp; GAIM"
date: 2007-05-10
forum: General Help
---

### Post by Flavian on 2007-05-10
That's a really stupid question to ask and I am kinda ashamed to ask it, but *lol* I just CAN'T find the problem :(

In Dapper using GAIM 2.0beta6 I could close single chat windows by just hitting "ESC" now it's not possible anymore. That is really annyoing, because I tend to close the windows after writing so that it pops up when a new message comes.

I've searched the preferences and plugins like 10 times and can't find an option that sets the ESC key to close chatwindows :(

I am sorry for posting this, but it annoys me so much.

---

### Post by Flavian on 2007-05-10
please help.

---

### Post by strabes on 2007-05-10
Ctrl+W is the standard "close tab" keyboard shortcut. I also miss the escape-closing of chat windows in gaim. Kopete (and all KDE applications) allow you to configure keyboard shortcuts and I think you should be able to do this. I also think there's an option in kopete or gaim to automatically close windows after you send a message. Maybe it's in the gaim plugins. I can't remember but I do know there's some sort of option to do this.

---

### Post by Flavian on 2007-05-10
Thanks for your answer!

The problem I don't understand is that I use the EXACT same Version of Gaim in feisty as I used in dapper and it does not work anymore.
It worked before in dapper, so I really don't understand why it doesn't anymore in feisty :(

---

### Post by finer recliner on 2007-05-10
first get rid of the beta application
install pidgin 2.0 (formally gaim 2.0) [http://pidgin.im/](http://pidgin.im/)

---

### Post by Flavian on 2007-05-13
:) Thanks man, I totally did NOT recognize that the final 2.0 was out. Thanks a lot.
Even though now, compiled and everything it works totally fine (MSN works now in my student flat behind a proxy YEAH! woohoo)
But the [ESC] Key function doesn't :(

Can someone help?

---

### Post by muhacir on 2007-05-13
> **Flavian said:**
> 
But the [ESC] Key function doesn't :(

Can someone help?


me too

---

### Post by mburoff on 2007-05-16
Go into ~/.gaim and edit the accels file with your favorite text editor.  Look for the line that ends with "<main>/Conversation/Close" "<control>w"   or  "<main>/Conversation/Close" "" and then put "Escape" where "<control>w" or "" is.

---

### Post by strabes on 2007-05-17
mburoff: That didn't work for me even after multiple restarts of gaim.

---

### Post by Flavian on 2007-05-17
I tried that too... even with "esc" instead of "escape", WEIRD is that even after a REBOOT the window still colses with** <control>w** ! 
[edit]
Wait, shouldn't it somewhat be a file named pidgin instead of gaim now? :confused:

---

### Post by Flavian on 2007-05-17
okay, here is what I've found out.
First of all, for pidgin users, the file is located in ~/.purple$ and then the file "accels" as written above.
BUT here comes the weird part. One reason why it does not change for you strabes is that pidgin / gaim I think rewrites the commands... so if you open the file with gedit and leave it open in the background, close and restart your gaim / pidgin, the following note will popup in gedit saying: 
> 
The file /home/flavian/.purple/accels changed on disk.
Do you want to reload it?


if you do so, the entry you just changed hops back to the default setting :(
Any ideas??

---

### Post by joshdcurry on 2007-05-18
How do I make Escape close conversation windows?

Locate the file C:\Documents and Settings\username\Application Data\.purple\accels and uncomment or add the following line: (gtk_accel_path "<main>/Conversation/Close" "Escape") This must be done while Pidgin is not running. 

See more at [http://developer.pidgin.im/wiki/FAQAllInOne](http://developer.pidgin.im/wiki/FAQAllInOne)

---

### Post by mburoff on 2007-05-25
I'm still using Gaim 2.0.0beta6 so that might be why it doesn't work.  One thing to remember is when editing the file you can't be running gaim or pidgin.  Oh, remember to also uncomment the line by deleting the ; .

---

### Post by mrashley on 2008-01-22
Was this ever solved? I'm having the same trouble and referred to pidgin website does not work any longer.

I would love to have the ease of pressing escape to close a conversation. Control+W just isn't conversational.

---

### Post by mrashley on 2008-01-22
I solved it!

Steps:

Close Pidgin.

Edit the accels text document in <home folder/.purple/accels

Find the line with /Conversation/Close

Remove the semi-colon ( ; ) at the beginning, which I think mean comment out line. (You may have seen this before as a #.)

Change the ending to read "Escape".

It will look like this.

```

...
; (gtk_accel_path "<main>/Options/Enable Sounds" "")
; (gtk_accel_path "<PurpleMain>/Help/Online Help" "F1")
; (gtk_accel_path "<PurpleMain>/Tools/sep3" "")
**(gtk_accel_path "<main>/Conversation/Close" "Escape")**
; (gtk_accel_path "<PurpleMain>/Tools/sep2" "")
; (gtk_accel_path "<main>/Conversation/Insert Link..." "")
; (gtk_accel_path "<PurpleMain>/Buddies/Sort Buddies/By status" "")\
...
```

Save the file, and restart pidgin.

---


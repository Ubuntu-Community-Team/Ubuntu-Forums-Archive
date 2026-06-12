---
title: "Thunderbird 1.0"
date: 2004-12-08
forum: General Help
---

### Post by Hendry on 2004-12-08
Is there somebody out there who is running Thunderbird 1.0 yet? Is it possible to install it instead of the 0.8 version which is installed right now? If so, can you explain to me how?

---

### Post by nigelng on 2004-12-08
Yes I do,

That's pretty quick thou.

1 - Go to [http://www.mozilla.org](http://www.mozilla.org) download thunderbird-1.0.tar.gz ... (they might change the name but it should be thunderbird<something>.tar.gz ) . I assume you will download to your home directory /home/<username>/

Then:
2 -  Open console (gnome-terminal) Applications -> System Tools -> Terminal 

3> type in "tar -xzvf thunderbird<something>.tar.gz" (u can achive that by using tab after typing thunderbird...). After this a thunderbird folder is create in your home directory. Try type "ls thunderbird/ " to make sure it's there.

4> "sudo mv thunderbird/    /opt/" 

5a> "sudo mv /usr/bin/thunderbird  /usr/bin/thunderbird-old (that's backup ur old thunderbird -> if this command return an error, that's fine no problem keep on next  instruction ; that mean your current thunderbird is staying somewhere else not in that folder)

5b> "sudo ln -sf /usr/bin/thunderbird /opt/thunderbird/thunderbird"  (edited: problem fixed from henry report)

6> "nautilus applications:///Internet"

7> now u got a nautilus open in Internet group of your launch menu. Right click 
choose "Create  Launcher" -> enter name ... in the command box type "thunderbird"

Now you got thunderbird 1.0 running. yahoooo ! well if you already use thunderbird then I'll automatically take over ur current details. No worry.

Return to me if u got any problem
Nigel

---

### Post by TravisNewman on 2004-12-09
I haven't tried 1.0 but when I installed 0.9 it decided to use the .thunderbird folder instead of .mozilla-thunderbird for storing personal data. Just to be sure your emails get picked up properly, do:

cd ~
ln -s .mozilla-thunderbird .thunderbird

That will set up a symlink to the .thunderbird directory so that no matter which it uses, you'll be safe

---

### Post by Hendry on 2004-12-09
Thank you for all the help. It's working great now, but step 5B did't work here.. I received the error message "file allready excists" . And in step 7 I changed the command line to /opt/thunderbird/thunderbird

But hey, it's working including my old settings of Thunderbird 0.8 . I'm not sure that was because I've set up the symlink . Did't want to try without it  :-D 

Thanx again!

---

### Post by nigelng on 2004-12-09
ah henry... 

Sorry about that step 5b: should be :


"ln -sf  /usr/bin/thunderbird  /opt/thunderbird/thunderbird"  

The problem will be solve.
Regards,
Nigel

---


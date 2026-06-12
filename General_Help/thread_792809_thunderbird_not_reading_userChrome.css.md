---
title: "thunderbird not reading userChrome.css"
date: 2008-05-13
forum: General Help
---

### Post by frankdn on 2008-05-13
Hi all,

I'm impressed with the level of support available here.  Hopefully someone will have run across a solution to my latest problem-- I've searched this forum w/o success:

I have an issue with the font size t-bird uses for all the panes surrounding the message pane (the message-body pane itself is OK).

This forum & the thunderbird support pages are telling me to create ~/.mozilla-thunderbird/chrome/userChrome.css, and stick some text in there, e.g.:
/* font */
* { font-size: 11pt !important;
  font-family: Verdana !important; 
} 

This has no effect however.  I find that in fact, thunderbird is not reading the file at all.  Have I put it in the wrong place?

me$ pwd
/home/me/.mozilla-thunderbird/chrome
me$ date
Tue May 13 08:59:50 EDT 2008
me$ ls -lu userChrome.css
-rw-r--r-- 1 me me 84 2008-05-13 08:57 userChrome.css
#wait
me$ date
Tue May 13 09:00:02 EDT 2008
#start thunderbird
me$ ls -lu userChrome.css
-rw-r--r-- 1 me me 84 2008-05-13 08:57 userChrome.css

note: last-access time hasn't changed

Logging out & back in doesn't change the access time, either.

UPDATE:

Yes I did put the css file in the wrong place.  For any other newbies who stumble across this in tying to configure thunderbird on 8.04 (Hardy Heron):

First, exit thunderbird.  Kill all running instances.

Then open a terminal session: Applications->Accessories->Terminal

Then start the program as follows:

% thunderbird -profilemanager

This opens a dialog.  Create a new profile for yourself.  You'll find a new directory in ~/.mozilla-thunderbird:
% cd
% ls .mozilla-thunderbird
profiles.ini xlczm6sh.Yourname

The "garbage.Yourname" file is your profile directory.  For my thunderbird problem, I had to cd down into the new directory, create a subdirectory named 'chrome', and copy the userChrome.css file into that.  Done.

Oh, BTW, now that thunderbird reads userChrome.css, try editing the file and playing with font families.  I changed 'Verdana' to 'Garamond' and I think it looks a lot better.

---

### Post by daqron on 2010-04-30
You, sir, are a gentleman and a scholar. It's actually even a bit simpler than what you describe, but your hint about creating the "chrome" folder within your profile is the key. This is sadly not reflected on the [Thunderbird help page]("http://www.mozilla.org/support/thunderbird/edit#profile"). 

**Setup userChrome.css in TB3 on Ubuntu 10.04:**

1. Find your your active profile directory. To do this, close all instances of TB. From terminal, run the command: 
```
thunderbird -profilemanager
```Hover your mouse over the default profile and it will show the path in a tooltip (see screenshot attached).

2. Navigate to the path indicated, and create the "chrome" folder inside of it.

3. Create the userChrome.css file inside the "chrome" folder. The first line of your userChrome.css file should read:
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
``` 
4. After that it's all regular CSS; you just have to find the right selector (HTML element) to customize. Good luck with that part :)

**Change new mail folders to black**
One more thing I've been hacking at in 10.04 that might be helpful for future visitors is that new messages cause the mail folder to turn light gray. This is terribly annoying because light gray on a white background is just about unreadable. To change it to black, add the following lines to your userChrome.css file:
```
treechildren::-moz-tree-cell-text(folderNameCol, newMessages-true) {
	font-weight: bold;
	color: #000000 !important;
}
```
Cheers!

---

### Post by Scott Deagan on 2011-05-05
Thanks for the post daqron. The information you provided is accurate and works perfectly on Ubuntu 11.04 (running Thunderbird 3.1.10).

I like things vertically spaced a little more than the default on my Sony Vaio laptop (that has 1920 x 1080 resolution). I have created and attached my userChrome.css if anyone's interested.

---


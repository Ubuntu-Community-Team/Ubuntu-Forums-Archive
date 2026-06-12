---
title: "firefox question"
date: 2007-06-05
forum: General Help
---

### Post by adgjm on 2007-06-05
Is it possible to import my firefox bookmarks, and settings from my windows version?

---

### Post by wjhildreth on 2007-06-05
The bookmarks for firefox are held in an HTML file under your home directory. So if you copy one to the other, I would think that would take care of your needs. This is just a guess and I may be wrong.

In Windows, your bookmarks are in

c:\documents and settings\<user name>\Application data\Mozilla\Firefox\Profiles\<some-text>.default\bookmarks.html

In Ubuntu they are in

/home/<username>/.mozilla/firefox/<some-text>.default/bookmarks.html

Now keep in mind that in Windows the Application Data folder is hidden by default and in Ubuntu the .mozilla folder is hidden by default.

I hope that helps.

Regards,

Joe Hildreth

---

### Post by viciouslime on 2007-06-05
Yup. Just copy your profile across. In windows it is stored in C:\Documents and Settings\[User Name]\Application Data\Mozilla\Firefox\Profiles\ it wants to go in your profile folder in ubuntu. This will be found in your home directory in a hidden folder called .mozilla (press ctrl+h to see hidden folders in nautilus) there should be another folder in there called firefox or profiles i think.... can't remember now and I am on my mac, but if you can't find it i will check later :)

---

### Post by viciouslime on 2007-06-05
Gah beaten to it again :p

---

### Post by adgjm on 2007-06-05
Thanks,

---

### Post by bunker on 2007-06-05
Look for a file called bookmarks.html somewhere in the application data.  Copy it directly to the ~/mozilla/firefox/<something>/.   I don't know how to derive the <something> directly, but if you only have one user profile in firefox, there will only be one directory there.  I guess if you wanted to find out which is yours, you could visit some known page and `tail` the history.dat file in each directory until you find the url.

The same applies to the windows data; it is located in '/Documents and Settings/<windows username>/Application Data/Mozilla/Firefox/Profiles/'.

Edit: foiled by my own proxy cache ;)

---

### Post by wjhildreth on 2007-06-05
> **viciouslime said:**
> Gah beaten to it again :p

Sorry Viciouslime:

That was the first time I have been able to help someone. I just could not resist answering.

Regards,

Joe

---

### Post by Lord Illidan on 2007-06-05
You can also use Foxmarks - an extension to store your bookmarks on an external server, and then put them on any computer you are working with.

---


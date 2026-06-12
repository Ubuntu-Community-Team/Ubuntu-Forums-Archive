---
title: "Problem installing Firefox new format"
date: 2023-04-26
forum: General Help
---

### Post by lou6 on 2023-04-26
I'm trying to get a replacement laptop up and running (current one working fine but getting old) and new Firefox (snap version) did not install correctly.  It isn't recognizing the new file format.  Could this be because the old Firefox (.mozilla folder) isn't on the computer?

I'm thinking that the presence of the old Firefox (.mozilla folder) is needed to install the new version correctly...

Any help very appreciated...

Update:  I back up the system daily so if restoring .mozilla will help I can do that easily...

---

### Post by ajgreeny on 2023-04-26
I'm not sure I fully understand what you mean by *** It isn't recognizing the new file format. Could this be because the old Firefox (.mozilla folder) isn't on the computer?*** 
However, it is certain that the snap version of firefox will be completely unable to access your old .mozilla configuration folder if it is somewhere other than in your home folder or, I think, mounted in /media/username in the filesystem, eg, a /home sitting on a network filesystem is completely useless for the snap version.

My knowledge of snaps is very limited as I have removed the whole snap system from my machines and use alternative installation methods for all those apps such as PPA repos for some or the downloaded .tar.gz archive direct from Mozilla for firefox.

---

### Post by lou6 on 2023-04-26
Thanks - I'm 81 years old and not close to as sharp as I once was.  I'll put a copy of the old .mozilla folder wher it belongs and go from there.  Thanks for responding.

---

### Post by Quarkrad on 2023-04-26
Your normal ff profile is located in /home/username/.mozilla/firefox/xxxxx.default-release.  If you have backed up your profile it might be somewhere else.   Anyway, you need to copy the contents of that folder and paste them into  /home/snap/firefox/common/.mozilla/firefox/yyyy.default-release.
note.  there is a difference between xxxx.default-release  and yyyyy.default-release.   Don't change the yyyyy.default-release name, just copy/paste the contents over.

---

### Post by Quarkrad on 2023-04-26
Was in a bit of a rush with the last post.   Your profile files are in the folder xxxxxx.default-release.  With the deb version of FF this folder is located at **/home/username/.mozilla/firefox.**  When the snap version of FF is installed a new .mozilla folder is created along with its new profile folder yyyyy.default-release.   (Each time a new profile is created there is a change to the name of the .default-release folder, hence I have used xxxxx and yyyyyyy - it is important not to change this name).  The new snap folder is located in **/home/username/snap/firefox/common/.mozilla/firefox** - this is where you will find the new profile folder ???????.default-release.  So, all you need to do is copy the contents of your old .........default-release folder into the new ........default-release folder and you will get your old FF back with any saved bookmarks and passwords.

---

### Post by lou6 on 2023-04-26
Thank you - as I mentioned, my mind is not what it used to be but I will try to get this as soon as I can.

---

### Post by lou6 on 2023-04-28
Thanks again - I successfully  restored the data this morning.  One last question - is the previous .mozilla folder (the hidden one) that I was backing up now obsolete?  If so, I'll delete it from my backup...

---

### Post by Quarkrad on 2023-04-29
Once you are happy that your new (snap) version of firefox is working OK - yes, you can remove the hidden .mozilla folder from both your **/home/username/** directory and your backup.  MAKE sure though that your backup environment* now includes the new location of your .mozilla folder (/home/username/snap/firefox/common/.mozilla/firefox)

* the methodology you use to perform your backups

---


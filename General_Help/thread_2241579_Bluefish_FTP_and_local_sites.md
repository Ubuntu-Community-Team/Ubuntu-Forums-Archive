---
title: "Bluefish FTP and local sites"
date: 2014-08-27
forum: General Help
---

### Post by micwit2 on 2014-08-27
There is no Bluefish forum, so I figured here would be a good place to ask...

I know in Bluefish you can edit FTP files in a few different ways, however, I am moving across from Dreamweaver, and I can't work out how to edit locally, yet save the FTP details for an easy upload. In Dreamweaver, you choose your local folder (so that would be a mapped network drive for me on a computer on the LAN running an FTP server) and this would be used for development and testing purposes. When you have the site to the stage you want it, you just use ctrl+SHIFT+u and it uploads the file you are working on (or if you have a folder/site selected, the entire folder/site gets uploaded). In Bluefish, it seems you would have to manually change between the local and ftp folders and manually upload the files. Is there any way to get both local and FTP working together for easy testing and uploading? I am working on quite a few sites, so I would like the details saved in the project file (like in Dreamweaver) so that when I switch between projects the FTP details will be correct for that project.

Any ideas?

---

### Post by nico80 on 2014-09-10
I am actually starting to have a look at Bluefish and was wondering exactly about that. 

An alternative is to use Quanta+ which is much more like DW in that sense, you can edit file locally and then tell Quanta+ to upload them to the FTP. There is also a function which scans all of your project and uploads all of the files that have been changed.

EDIT: another alternative which from a quick test I think is probably even better is using NetBeans.

---

### Post by micwit2 on 2014-09-17
Quanta+ seems to be a dead project now, plus I would like something that is cross platform so that I can use it in any OS. NetBeans looks like its come a long way since I used it last (I found it annoying to use). I'm still not 100% keen on an app that needs to run of java as well, as java seems to have compatibility issues these days. I would much rather something that installs natively (like bluefish), but I may try this at some stage.

---

### Post by andrew.46 on 2014-11-03
My own workflow is to edit locally with Bluefish and then simply use rsync to update the remote site, might be worth a look?

---

### Post by micwit2 on 2014-11-09
Thats an interesting concept. I work on heaps of sites, so I guess it would be a case of making a modified script for each site, but then it would be a pain to make a shortcut key to upload...

---

### Post by micwit2 on 2014-12-30
Problem solved! Brackets ([http://brackets.io/](http://brackets.io/)) is fully opensource, works well in ubuntu, OSX, Windows etc and is the best editor I have come across yet. The extension manager is awesome, and I use SFtpUpload which I think is better than dreamweavers (although I wish there was a simple option of pulling files down). It only recently reached version 1.0 (I have only used it for the past few weeks), but it already seems to be the best to use in my situation.

---

### Post by andrew.46 on 2014-12-30
It looks interesting! Good to hear that your issue is resolved...

---


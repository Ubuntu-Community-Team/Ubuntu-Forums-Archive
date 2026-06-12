---
title: "Is all my data really missing from Ubuntu One?"
date: 2014-03-09
forum: General Help
---

### Post by CJ_Hudson on 2014-03-09
Hi,
I don't currently have a Ubuntu distro installed because I have been working on a project that was simpler and cheaper to use Windows for the past year or so.
I haven't tried to log in to Ubuntu One since at least as far back as August 2012, but now I find after installing Ubuntu One in Windows all my backup files seem to have disappeared?
Is this in fact the case?
I seem to recall the backups were made with something called Deja Dup. Has this now been merged into Ubuntu One? Sorry been out of the loop a while, hopelessly confused!
:(

---

### Post by marco-parillo on 2014-03-09
Based on this:
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)
they have not been merged, but the default deja dup target is U1:
> [COLOR=#333333][FONT=Verdana]By default, Déjà Dup backs up your Home directory, ignoring the Trash and
> Downloads folders. It puts the backup in your [/FONT][/COLOR][Ubuntu One]("http://www.howtogeek.com/108000/how-to-synchronize-your-configuration-files-with-ubuntu-one/")[COLOR=#333333][FONT=Verdana] account.[/FONT][/COLOR]

---

### Post by CJ_Hudson on 2014-03-17
Hi  marco-parillo,
Thanks for you help. I see from the following (my underlining):

> From the Storage pane, you can customize where Déjà Dup puts your backups. If you back up to Ubuntu One (and have set up Ubuntu One on your computer) your backup will be accessible from any computer, so you can easily restore your personal data_ on any Linux system._ You can also back up to other types of remote servers, including FTP, SSH, WebDAV, and Windows shared folders.

...that I have to actually have a Ubuntu system installed in order to recover the folders. Is this correct? Because from Windows it appears my old backup, which I recovered the password for from my old email address, is completely empty. 
Thanks again.

---

### Post by marco-parillo on 2014-03-19
It seems to indicate than you can also use Windows shared folders, but I am no Windows expert.

---

### Post by CJ_Hudson on 2014-07-18
Hi again,
I think I will have one last try to get my files back and install a dual boot Ubuntu distro on my desktop (only computer.)
This is a last ditch desperate attempt because one of my back-ups has become corrupt (made around the time of the millenium, Y2K) and I have lost around 10,000 words of creative writing which is essential to my life which I thought was safely stored on a free hosting website which has closed and deleted all my data. Very very annoyed.

---

### Post by CJ_Hudson on 2014-07-19
Hi, For some reason I couldn't log in to this forum under Mogbug ID so I had to create a new account.
Anway my files seems to be downloading except there is some weird files which I don't recognise which I assume is data image thus:

/~/deja-dup/chris-System-Product-Name/duplicity-full.20111214T070532Z.vol161.difftar.gz ...downloading [Overall progress: 48%]

What is this?

---

### Post by coffeecat on 2014-07-19
> **CJ_Hudson said:**
> Hi, For some reason I couldn't log in to this forum under Mogbug ID so I had to create a new account.

I see no reason in the MogBug account settings that would prevent you from logging into it. However, you have two Ubuntu One SSO accounts, each linked to one of the forum accounts. Perhaps that's where the confusion lies. If you need help unscrambling all this, please post in the Resolution Centre:

[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by CJ_Hudson on 2014-07-19
Please can anyone tell me what these files are that downloaded from my Ubuntu One backup: there are half a dozen like this:

/~/deja-dup/chris-System-Product-Name/duplicity-full.20111214T070532Z.vol161.difftar.gz

It seems much of my supposed back files are missing so I wondered if these were some compressed archives or some such? Or maybe complete system images? Thanks.

(Sorry about the delay I had issues signing in.)

---

### Post by CJ_Hudson on 2014-07-29
Hi again, sorry to multiple post but I am really desperate now.
I have now re installed Ubuntu on my system.
I got this message from Ubuntu staff:

> This is the FINAL reminder to make  sure you have retrieved all your data from Ubuntu One filesync, as we  will be deleting all the content permanently on 31st July 2014.  After  that date, we will no longer be able to retrieve any of your files.

In  order to make it easy for you to retrieve all of your content, we have  released a new feature that lets you download all your content at once.  Our website ([https://one.ubuntu.com/](https://one.ubuntu.com/)) has been updated with instructions on how to conveniently download all your files.

In  addition, you still can use Mover.io's offer to transfer your data to  another cloud provider for free. The Ubuntu One web interface is  available for you to download individual files as well.

All of us in the Ubuntu One team would like to thank you for your support over the years.

The Ubuntu One team

I have followed the link and attemtped to recover my files but I would say at a rough guess 9/10ths of them are missing.
I now have 2 clear days to try and retrieve my backup files.
If there is anyone with the power or authority to help me recover the missing files I would be extremely grateful?
There is a whole folder with mystery files in it (see attached screendump) which I don't know what they do or what they are for. As I said I have been out of the Ubuntu loop for a few years and would really appreciate some assistance in recovering my backups?

[IMG]https://imagizer.imageshack.us/v2/1295x728q90/540/cMFX5J.png[/IMG]

---

### Post by coffeecat on 2014-07-29
> **CJ_Hudson said:**
> If there is anyone with the power or authority to help me recover the missing files I would be extremely grateful?

Not here I'm afraid. All forum members, staff included, are volunteers. None of the forum staff are employed by Canonical and we are not involved with the administration of Ubuntu One cloud storage.

---

### Post by bapoumba on 2014-07-29
To note, I had backed up my local sync folder when the news first came out. I tried the download tool when I received the email the other day. I did not use the link from the front page because I have a 32-bit arch ([https://help.ubuntu.com/community/U1/Downloader/All/Architectures](https://help.ubuntu.com/community/U1/Downloader/All/Architectures)). I had to run the script several times in a row for it to complete. One LibreOffice file never made it though.

---

### Post by CJ_Hudson on 2014-07-30
I will try running it again- otherwise it's bye bye data time. :mad:

EDIT: Hi I think I got confused because I reinstalled Ubuntu at some point and was unable/ chose not to reinstall all my previous files and folders.
I think this is why I think most of my files are still missing.
However I solved the mystery of the files with names like:  > duplicity-full.20111214T070532Z.vol1.difftar.gz

...these are Deja Dup recover-files and can be restored using the Deja Dup interface (pre installed on my version of Ubuntu.)

---

### Post by weyland42 on 2014-08-01
They look like gzip archives. Open a filemanager such as Dolphin, right click on a file, and select Extract. The rest should be easy. 

Have you looked in the manifest file, top left? Probably a list of contents or similar.

Good luck.

---

### Post by coffeecat on 2014-08-01
@CJ_Hudson, because we're moving and closing the Ubuntu One sub-forum now that Ubuntu One cloud services are fully closed themselves, I've moved this thread into General Help in case you need more help getting your data out of your downloaded archives.

---

### Post by obake2 on 2014-08-02
Hi Hudson. Those are Deja Dup recoery files. Just open Deja Dup (or just called "Backups") click on restore, choose directory.

Good luck! 
> **CJ_Hudson said:**
> 
There is a whole folder with mystery files in it (see attached screendump) which I don't know what they do or what they are for. As I said I have been out of the Ubuntu loop for a few years and would really appreciate some assistance in recovering my backups?

[IMG]https://imagizer.imageshack.us/v2/1295x728q90/540/cMFX5J.png[/IMG]

---


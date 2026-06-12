---
title: "a few questions"
date: 2008-05-22
forum: General Help
---

### Post by freespire on 2008-05-22
if you allow me i would like to ask a few things.i undersand that the newbies like me are a pain in the *** but i would appreciate any help cause in greece linux are not yet popular.so if you allow me--->

1.do i need an antivirus?cause i hate antivirus industry....
2.my system keeps telling me that it is unable to mount my external disk devices which have are ntfs
3.i have problems in playing dvds.it keeps on telling me---.error reading the source(totem player...should i give a try to ogle player...but i still can not find the installation instructions
4.and now the most important of all is what must i do with the microsoft office files....unfortunately in the university everything is based on office 2003/2007.how can i open these files+how can i write a doc. which can be read by microsoft office?
i also found these cross-platforms---->wine
win4lin
crossover
are these fit?


please help me cause i really really hate the microsoft platform...

---

### Post by bingoUV on 2008-05-22
1. You don't need an antivirus. *Ubuntu is a fellow conspirator like you in the downfall of the antivirus industry*.

2. Post the output of the following command after plugging in external disks
```

sudo /sbin/fdisk -l

```

3. Install mplayer using Applications -> "Add/Remove Programs". Right click on DVD icon, and use mplayer to play DVD. * Brace yourself, every one here will suggest a new player in trying to help you*

4. Just double click on the office files. Ubuntu should open them with OpenOffice.org, an almost Microsoft office compatible program. Most files should open with little or no formatting distortion. 

Cross over office is known to run Office 2003. 2007 compatible version will be out shortly. This will open all Office 2003 files, but might cause other instability. Mostly works fine from what I have heard.

------
You seem to be Greek. Please ask if you do not understand my English. Sorry for that. Text in italics above are jokes. Do not read them if you have problems with English.

---

### Post by ajgreeny on 2008-05-22
> **freespire said:**
> if you allow me i would like to ask a few things.i undersand that the newbies like me are a pain in the *** but i would appreciate any help cause in greece linux are not yet popular.so if you allow me--->

1.do i need an antivirus?cause i hate antivirus industry....
2.my system keeps telling me that it is unable to mount my external disk devices which have are ntfs
3.i have problems in playing dvds.it keeps on telling me---.error reading the source(totem player...should i give a try to ogle player...but i still can not find the installation instructions
4.and now the most important of all is what must i do with the microsoft office files....unfortunately in the university everything is based on office 2003/2007.how can i open these files+how can i write a doc. which can be read by microsoft office?
i also found these cross-platforms---->wine
win4lin
crossover
are these fit?


please help me cause i really really hate the microsoft platform...

Q1   No,you don't really need antivirus software if you are running Ubuntu only as a desktop and not as a server.  If you send a lot of files to Windows users, you might wish to run a check on files every so often, but in all honesty, Windows users should make sure they keep themselves safe, not expect linux users to do it for them.

Q2   Get all the ntfs packages from synaptic (ntfs-3g, ntfs-config and libntfs-3g12) and there will be a menu item in **System Tools** called **NTFS Configuration Tool** where you can set up the mounting of the disk as you want it.

Q3   Have a look at the medibuntu site to get all the packages you need for DVD playback, particularly libdvdcss2.  Go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) for much more info on how to enable and use the repos. for this and other packages.
I suggest you change the DVD player software to totem-xine rather than totem-gstreamer as well as it deals with DVDs much better, or alternatively use mplayer instead.  All are available from the repos using synaptic.

Q4   Just about all MS Office files can be opened with OpenOffice.org, the default office suite in Ubuntu.  Occasionally the formatting is a bit wonky, but it's usually possible to deal with that.  If you want you can try wine as an emulation for windows, and run one of the older MS Office suites, but to be honest it is unlikely you will need it for most docs.  The new MS Office suite which produces .docm and .docx files does present a bit of a problem but the new versions of OO promise that will be overcome, I believe.  Wine is open source and free, but Crossover Office is a commercial application and not free.

Good luck and welcome to this community.

---

### Post by freespire on 2008-05-22
than u both very much!!!!
i sak for apologise for taking too much time to reply.

unfortunately i did the step above and did not work.there was always an error in mounting the disk.so i reinstalled the os with the external device connected and switched on and all of a sudden everything worked fine.but i still have not configured out why it started working properly now...
do you have any idea?


p.s. i ******* love this ubuntu!!!:)

and i regret for all these years of microsoft captivity...:(

---


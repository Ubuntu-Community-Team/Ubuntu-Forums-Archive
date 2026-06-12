---
title: "Can iPhone Voice Memos be transferred to PC?"
date: 2024-05-02
forum: General Help
---

### Post by arius88 on 2024-05-02
I'm a musician. I've been using the Voice Memos app on my iPhone 6s to record thousands of little musical ideas, and I'd like to be able to back them up to my linux desktop computer. (Running Lubuntu 22.04.) 

Does anybody know if there's a way to do this? I can get photos off the phone no problem, but can't seem to access other types of files. The recommendation for Windows is to use iTunes (no thanks) but I can't find any info about doing it on linux.

---

### Post by yancek on 2024-05-02
You can  try the suggestion at the link below to install VLC on Ubuntu and try selecting from the Documents on iphone icon in the file manager (Nautilus).  I haven't tested the method described below.

[https://ubuntuhandbook.org/index.php/2023/12/transfer-music-ubuntu-iphone/](https://ubuntuhandbook.org/index.php/2023/12/transfer-music-ubuntu-iphone/)

I used vlc for ios downloaded to my iphone to copy an audio file from the iphone to my Ubuntu install.  Had to move the audio file to the Files folder on the iphone first.  It has always been difficult to copy/past from Linux to iphone for most anything other than photos and each ios upgrade changes things so that what worked on one version may not work on the next.

---

### Post by arius88 on 2024-05-02
Thanks yancek. I'll see if I can figure something out using the process in the link you shared and report back. Not sure if it's clear that I'm trying to copy files FROM my phone, not TO it, but if I can do one I guess I can do the other.

---

### Post by yancek on 2024-05-03
The link I posted might work in the reverse also but you probably won't see audio/music files from Ubuntu unless you first save them to the Files directory on the iphone.  You might do an online search for using ifuse from Ubuntu to your iphone although I've not had much luck with it personally.   You will need to install libimobiledevice on Ubuntu.   You might try going to iCloud to access the files but I wouldn't expect success.

Tested this on my iphone 13 with IOS 17.4 yesterday and forgot to include the details below.  Apple makes lots of changes from version to version so if you are using an iphone 6, I expect there will be several differences/options from the steps below but you should get the general idea.  I did this with one file so I have no idea how you would do a large number of files. 

The suggestion below requires vlc for ios which can be downloaded from the App Store.   Once this app is downloaded to your iphone, open it and tap on the Network tab/option and you should see Sharing via Wi-Fi which will show the IP for the iphone.  You will need this IP entered in a web browser on Ubuntu to download the file from the iphone.

Open voice memos on your iphone, tap on a recording then click the circle ellipsis icon in the upper right (circle with 3 dots inside), you will get several options and then you can go to the bottom of the options and tap on Save to Files.  Then tap on 'my iPhone' and then VLC then tap Save in upper right. 

Then go to your computer and open a web browser and enter the IP for your iphone.  Before trying to access the phone, make sure you have the iphone open (have entered your 4/6 digit passcode) and have the vlc for ios app on the phone open.  In the web browser with the IP above enterred, you should see two options, Drop Files (to copy file to phone) and Download Files to download from the iphone to your computer.  You should see the name of a file under the Download option in the web browser and clicking on it should give you the option to Open or Save.   On Ubuntu, the file should be saved to the Downloads directory.

---

### Post by yancek on 2024-05-03
I used the method described in post 4 wirelessly, with the phone not attached to the computer with a usb cord.  If you plug a usb cord to your computer and the other end to the iphone, you should see Documents on ?? iphone (the user/owner of the phone would be where the ?? are).  If you save to Files or copy/paste to files, you should see and be able to download audio or image files.  This may or may not work depending upon how old/new your phone is and the version of ios as well as which release of Ubuntu you are using.

---

### Post by hotbbqsauce on 2024-05-03
Might not be the best advice since you are on the LXQt desktop environment, there is a project called [KDE Connect]("https://kdeconnect.kde.org/"), this can bridge IOS/Android with Linux which should be compatible with Lubuntu.
You can transfer any file to your PC. This is just one of its many useful features

KDE Connect is available on KDE, and on Gnome its named as [GSConnect]("https://extensions.gnome.org/extension/1319/gsconnect/") in the extension store.
The app is available in the [app store]("https://apps.apple.com/us/app/kde-connect/id1580245991") or [testflight]("https://testflight.apple.com/join/vxCluwBF"), its named KDE Connect on IOS.

Hope this helps!

---

### Post by arius88 on 2024-05-15
Okay so I installed KDE connect and got it to recognize my iPhone. Which is great, KDE Connect is a wonderful app, but I can still only send files from my Files directory. The files I want to send are in the Voice Memos app. So it seems my only recourse is to manually save each of the 3,877 files I want to send to my computer, one by one, in the Files directory, and then use KDE Connect to send them to my desktop. I calculate that this is about 15-20 hours of labour and will probably take me weeks to complete if I dedicate an hour a day to it. As opposed to, you know, opening a Voice Memos folder, highlighting all, doing one cut and paste operation, and letting my computer do all the work while I do other stuff. I find this quite frustrating. I guess that's my best option?

(Not that this is the forum for this, but why is iPhone architecture designed like this?)

UPDATE: Turns out I'm a dummy. I actually can select Voice Memos and mass send them to my files folder, and can also Select All there and mass send them to my PC, which is still a slightly annoying work-around but will make my job WAY less time-consuming than I initially thought. Anyway, props to whoever made KDE Connect, because I wouldn't be able to do this at all without it.

---


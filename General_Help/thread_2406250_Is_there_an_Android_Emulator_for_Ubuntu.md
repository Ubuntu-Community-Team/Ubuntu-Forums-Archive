---
title: "Is there an Android Emulator for Ubuntu?"
date: 2018-11-18
forum: General Help
---

### Post by praywwjd2004 on 2018-11-18
Is there a free Android emulator for Ubuntu similar to Bluestacks? 
I am ultimately looking to do 2 different things with the emulator. First I would like to run Showbox. Second I would like to see if there was a way that I could download the Xfinity Stream app to watch live TV.

Please advise.

---

### Post by pdcooper on 2018-11-18
android sdk do  the job ? 

[https://developer.android.com/studio/](https://developer.android.com/studio/)

---

### Post by praywwjd2004 on 2018-11-18
> **pdcooper said:**
> android sdk do  the job ? 

[https://developer.android.com/studio/](https://developer.android.com/studio/)


That may just work, however I am having trouble downloading it. I used your link from above and I get the following error:

android-studio-ide-181.5056338-linux.zip Failed - Download error

Any idea why?

---

### Post by praywwjd2004 on 2018-11-18
Can anyone help me troubleshoot why I get the message "Failed - Download error" when trying to download Android sdk from the link below for linux?
[https://developer.android.com/studio/#downloads](https://developer.android.com/studio/#downloads)

Is there another android emulator that will work on Ubuntu?

---

### Post by spjackson on 2018-11-19
> **praywwjd2004 said:**
> Can anyone help me troubleshoot why I get the message "Failed - Download error" when trying to download Android sdk from the link below for linux?
[https://developer.android.com/studio/#downloads](https://developer.android.com/studio/#downloads)

There are many possible causes of a failed download which can be either  the remote end or the client end or something in between, or a  combination of these. It does not appear to be the remote end since I  can download the file.

How are you trying to download it? Which  browser or command line tool? Can you download other files? Can you  download files that are 1GB or greater in size? Do you have room for a  1GB download? Does it fail immediately or after some time?

Have you tried the android-sdk package from the repositories that downloads and installs this?
> 
Is there another android emulator that will work on Ubuntu?
Searching these forums and googling reveal that other emulators are available but I haven&#8217;t tried any so cannot offer a specific recommendation.

---

### Post by vidtek on 2018-11-19
> **praywwjd2004 said:**
> Is there a free Android emulator for Ubuntu similar to Bluestacks? 
I am ultimately looking to do 2 different things with the emulator. First I would like to run Showbox. Second I would like to see if there was a way that I could download the Xfinity Stream app to watch live TV.

Please advise.

I am using VMware to run a rather esoteric Android, Remix 3.  I just use this to control my smart home appliances (central heating etc.)

Free for personal use, it also runs any windows and unix/linux flavours too.

Tony.

---

### Post by Adam_GUI on 2018-11-19
Android-Studio is in the Software Centre as a SNAP.
It will run Android.  But, you don't get much to work with.
And you have no access to the default Play Store.  Unless I've missed something.
Which, I suppose I can understand with it being a dev program.
[ATTACH=CONFIG]281698[/ATTACH]

I've had far better luck with Android x86 in Virtual Box.
[http://www.android-x86.org/]("http://www.android-x86.org/")
Android 8 is in release candidate.  I had issues with Google Play Services stopping and preventing setup.
The last stable version is Android 7.1.  It works. And, you get access to the play store.

If you're wanting to download and use apps from the play store, this seems to be the way to go.
Turn off VirtualBox's mouse integration, or you'll have to click-to-drag.  It makes things very annoying to work with.
VirtualBox will then capture your mouse input on click.  But, you can get your mouse back to the host with Right Ctrl.

---

### Post by praywwjd2004 on 2018-11-20
> **spjackson said:**
> There are many possible causes of a failed download which can be either  the remote end or the client end or something in between, or a  combination of these. It does not appear to be the remote end since I  can download the file.

How are you trying to download it? Which  browser or command line tool? Can you download other files? Can you  download files that are 1GB or greater in size? Do you have room for a  1GB download? Does it fail immediately or after some time?

Have you tried the android-sdk package from the repositories that downloads and installs this?

Searching these forums and googling reveal that other emulators are available but I haven&#8217;t tried any so cannot offer a specific recommendation.


I was trying to download it with Google Chrome Version 70.0.3538.102 (Official Build) (64-bit).
It may have been a space issue. I uninstalled Firefox which freed up almost 300mb of memory and tried downloading it again and it downloaded this time. I guess I should tell you that I currently have Ubuntu installed and running on a 16GB microSD card. This is temporary because my 1TB internal drive died and I am waiting to get my 4TB drive.

Here are the instructions on how to install:

> To install Android Studio on Linux, proceed as follows:

[LIST=1]
[*]Unpack the .zip file you downloaded to an appropriate location for your applications, such as within /usr/local/ for your user profile, or /opt/ for shared users.
[*]To launch Android Studio, open a terminal, navigate to the android-studio/bin/ directory, and execute studio.sh.
[*]Select whether you want to import previous Android Studio settings or not, then click **OK**.
[*]The Android Studio Setup Wizard guides you through the rest of the setup, which includes downloading Android SDK components that are required for development.
[/LIST]
Tip: To make Android Studio available in your list of applications, select Tools > Create Desktop Entry from the Android Studio menu bar.
Required libraries for 64-bit machines:
If you are running a 64-bit version of Ubuntu, you need to install some 32-bit libraries with the following command:

sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386




I have unpacked the zip file and put it on the desktop. I right clicked on the folder and selected "Open 
in Terminal". I don't know how to execute studio.sh in the Terminal. I tried using studio.sh and execute 
studio.sh in the Terminal but it said "studio.sh: command not found" and "execute: command not found"
How do I execute *studio.sh* in the Terminal?

---

### Post by wildmanne39 on 2018-11-20
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by spjackson on 2018-11-20
> **praywwjd2004 said:**
>   2. To launch Android Studio, open a terminal, navigate to the android-studio/bin/ directory, and execute studio.sh.


If you have got as far as being able to open a terminal and "navigate to the android-studio/bin/ directory" within that terminal, then to execute studio.sh you would do:
```

./studio.sh

```

---

### Post by praywwjd2004 on 2018-11-20
> **spjackson said:**
> If you have got as far as being able to open a terminal and "navigate to the android-studio/bin/ directory" within that terminal, then to execute studio.sh you would do:
```

./studio.sh

```


I just tried ./studio.sh and here is the output:

donavan@donavan-SX2840:~/Desktop/android-studio$ ./studio.sh
bash: ./studio.sh: No such file or directory

---

### Post by QIII on 2018-11-20
Again: Please use the default color and font.  To encapsulate code, results and the text of your config files, please use code tags.  This will make your posts much easier to read and code tags will preserve formatting.

To use code tags, either:

1.  Click the # button in the toolbar above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Cheers!

---

### Post by spjackson on 2018-11-20
> **praywwjd2004 said:**
> I just tried ./studio.sh and here is the output:

```

donavan@donavan-SX2840:[COLOR=#ff0000]~/Desktop/android-studio[/COLOR]$ ./studio.sh
bash: ./studio.sh: No such file or directory
```
That suggests that you have navigated to the android-studio/ directory not the android-studio/[COLOR=#ff0000]bin/[/COLOR] directory as per the instructions. So
```

cd bin
./studio.sh

```

---

### Post by praywwjd2004 on 2018-11-20
Thank you after going to the bin directory I was able to execute it.

---

### Post by monkeybrain20122 on 2018-11-20
I have played around with [genymotion]("https://www.genymotion.com/fun-zone/")

---

### Post by praywwjd2004 on 2018-11-20
> **monkeybrain20122 said:**
> I have played around with [genymotion]("https://www.genymotion.com/fun-zone/")


How did you like genymotion? Can I install and run Showbox in it? Can I access the Google Play store in it?

---


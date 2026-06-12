---
title: "files don't open with program chosen by default"
date: 2017-03-28
forum: General Help
---

### Post by garyed on 2017-03-28
Running 16.04  & I can't change the default program to open my files. If I have a .jpg file & I click on open with "Image Viewer" & click "use as default for this kind of file" it will open up with Image viewer but it defaults back to the other photo program once its closed. If i right click on the file it with show open with "Shotwell" but if I go to file properties it will show "open with Image Viewer" & that's what it will always default to.  What am I missing?

---

### Post by vidtek on 2017-03-28
Same here annoying isn't it?

---

### Post by ajgreeny on 2017-03-28
Is this a standard US using xfce4 DE as it did in the past, or has US moved away from xfce4 now?

If you open thunar, right click on a file ->Properties ->Open with and make changes there, does that fix the default application problem for you?

---

### Post by vidtek on 2017-03-28
nope, doesn't stick

---

### Post by garyed on 2017-03-28
Same here, you can set the default application in properties under Thunar for the file but it still doesn't open with it. The only work around I've been able to do so far is use the "open with" every time I want to use the application that I want. What's strange is if you right click on the file, the default application it shows that it will open with at the top is different than the one it shows it will open with under properties.  The app listed under properties is the one i set as the default but it doesn't open with that app. It opens with the other app that is listed on top that I can't get rid of.  Very strange

---

### Post by Bucky Ball on 2017-03-28
Nothing strange, but you may be missing something. Right click> open with. There is a tick box at the bottom of that window that says 'Use as default for this type of file'. Tick it and the changes will stick. If you simply choose the app and hit okay, no, that's not going to stick.

---

### Post by shridhar-kapshikar on 2017-03-29
I have tested this on my ubuntu 16.04 LTS, and it worked for me. The default program to open .jpeg file was "Image viewer" earlier and i have modified as below,
Right click on file --> properties --> openwith tab --> selected other default application --> Set as detault.[ATTACH=CONFIG]274340[/ATTACH]

Next time, when I opened the same file - it got opened in desire viewer.


2nd option:

Click on setting button on right side corner and click on "About this computer" and there also you can modify the default application ,




BR,
Shridhar

---

### Post by vidtek on 2017-03-29
> **shridhar-kapshikar said:**
> I have tested this on my ubuntu 16.04 LTS, and it worked for me. The default program to open .jpeg file was "Image viewer" earlier and i have modified as below,
Right click on file --> properties --> openwith tab --> selected other default application --> Set as detault.[ATTACH=CONFIG]274340[/ATTACH]

Next time, when I opened the same file - it got opened in desire viewer.


2nd option:

Click on setting button on right side corner and click on "About this computer" and there also you can modify the default application ,




BR,
Shridhar

Tried caja, thunar, dolphin and nautilus, done everything you suggested before, none of the settings stick.

---

### Post by Bucky Ball on 2017-03-29
In your screenshot, click the image viewer you are wanting to use. The button in the bottom right hand corner of the window in your screenshot 'Set as default' should then become available. Click it. Done.

---

### Post by garyed on 2017-03-29
> **Bucky Ball said:**
> In your screenshot, click the image viewer you are wanting to use. The button in the bottom right hand corner of the window in your screenshot 'Set as default' should then become available. Click it. Done.

I've done that but it doesn't change the program that it opens with already by default.
The jpg I attached shows the same file when I first right click it & then when I click properties. You'll see it says  Open with "Shotwell" when I first right click it but when I click on properties you'll see Open with: "Ristretto Image Viewer" which is the app the i set as default. It will open with "Shotwell" every time unless I change the open with to Image Viewer each time i open the file. I can't get rid of the Open with "Shotwell" even when i set the Image Viewer as default. That's the problem. If you're wondering why the first part of the jpg is a little sloppy it's because I couldn't print the screen on the first right click so i typed out what shows up.

---

### Post by ajgreeny on 2017-03-29
Just in case some of the files and folders in your home are owned by someone other than you, which might cause this problem, run command ```
sudo chown -R garyed:garyed /home/garyed
```
I am assuming your username is garyed but if not change that in all three instances to whatever you use.

---

### Post by garyed on 2017-03-29
Thanks for the idea but all the files are already owned by me & i  tried changing permissions too but that didn't help either.  I'm starting to think it might be a bug either in Thunar or Xfce desktop for 16.04.  I didn't have this problem until i upgraded from 14.04 to 16.04 last week.

---

### Post by Bucky Ball on 2017-03-30
> **garyed said:**
> I'm starting to think it might be a bug either in Thunar or Xfce desktop for 16.04.

Doubt it. I am running virtually the same setup (Xubuntu-core (xfce4), Thunar, 16.04 LTS) on three machines and have no such issue. Unless there are others experiencing the same problem and not just you, then it is not a bug. Have you checked on Launchpad to see if you are not alone?

Have you done a full update/upgrade of the new 16.04 LTS install? Might not make a difference, but probably a good thing to do anyway. Try this:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

The last command will NOT upgrade your system to 16.10, but will upgrade everything you have installed in 16.04, including xfce4 and Thunar if they need it.

Just a suggestion but give it a go, reboot and see what happens ...

---

### Post by vasa1 on 2017-03-30
Do you problems opening other files, such as text files, music files, pdfs, etc, with applications which you set as default?

---

### Post by vidtek on 2017-03-30
Bucky-

May I politely suggest you take a moment to read through all the responses on this thread; you'll see there are others with this issue, I have tried it with Kubuntu, Mint 18 and Ultimate Edition, all 16.* exhibit this same pattern.

The system defaults cannot be changed, only for a single instance where it must be selected every single time.

Tony

---

### Post by vidtek on 2017-03-30
> **vasa1 said:**
> Do you problems opening other files, such as text files, music files, pdfs, etc, with applications which you set as default?

yes

---

### Post by ajgreeny on 2017-03-30
I have been using Xubuntu 16.04 64bit since the autumn last year (October 2016) and I do not see this problem either.
I used 14.04 prior to that and it was not there either, however, I did not run a distro upgrade from 14.04 to 16.04; I did a clean install as I always do.

Are those of you who have posted in this thread and have this problem all using ubuntu-studio, or is it some other version?
Did you all distro upgrade or clean install?

---

### Post by vidtek on 2017-03-30
ajgreeny-

se  post #15

---

### Post by vasa1 on 2017-03-30
> **vidtek said:**
> ..., I have tried it with Kubuntu, Mint 18 and Ultimate Edition, all 16.* exhibit this same pattern.
...
Re. "all 16.* exhibit this same pattern", I'm using the Openbox session of Lubuntu _16.04_. I can set gpaint as the default program to open jpg files. All other image files open with mirage as did jpg files before I made the change.

Mint 18 and Ultimate Edition are not really relevant here because they're not official Ubuntu flavors.

Edit: could you try to temporarily rename ~/.local/share/applications/mimeapps.list to something else. It's possible that that file may have been corrupted.

---

### Post by vidtek on 2017-03-30
> **vasa1 said:**
> Re. "all 16.* exhibit this same pattern", I'm using the Openbox session of Lubuntu _16.04_. I can set gpaint as the default program to open jpg files. All other image files open with mirage as did jpg files before I made the change.

Mint 18 and Ultimate Edition are not really relevant here because they're not official Ubuntu flavors.

Edit: could you try to temporarily rename ~/.local/share/applications/mimeapps.list to something else. It's possible that that file may have been corrupted.

Vasa-

Understood about the mint and Ultimate versions, only put that in as my main machine has just gone belly up, now waiting on a new mobo/processor.
It was definitely happening on Kubuntu 16.04 before the puff of smoke put paid to it.
Now on the sammy laptop and I thought I'd check out those flavours to see if they exhibited the same and they do.  Having said that they are all using a common ~/tony home directory so I'll try your mime suggestion, will report back when checked on it.

Cheers, Tony.

Edit:  Confusing results.  I tried using caja and a .ts video container file to play with VLC or Kaffeine.  The context menu defaults for this are: 
1) Bluefish editor
2) Firefox
3) Leafpad
4) Libreoffice writer
5) Pluma

Strange defaults for a common video file, wouldn't you agree?

Removed these and tried to insert VLC and Kaffeine.  
VLC now seems to be there, but no sign of Kaffeine.

Double clicking on a .ts file now does nothing.
Right-click gives me a choice of VLC.

Putting back the mimeapps.list file makes no difference either way.

I wish I'd never butted in on this thread now, I am more confused than I was when I started.

Cheers Tony.

---

### Post by garyed on 2017-03-31
> **vasa1 said:**
> Do you problems opening other files, such as text files, music files, pdfs, etc, with applications which you set as default?

The problem occurs on all those types of files too. Half of the file types open with the app I want but just to test them I tried to change the app they open with & I can't make it stick after closing on them either. Maybe it has something to do with the upgrade as opposed to a clean install but I'l live with it before I do another upgrade to see if it fixes the problem. I was hoping there was a simple fix but it doesn't look like it so far.

---


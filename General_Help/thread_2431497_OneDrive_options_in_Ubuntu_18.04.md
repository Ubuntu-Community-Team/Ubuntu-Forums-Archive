---
title: "OneDrive options in Ubuntu 18.04"
date: 2019-11-17
forum: General Help
---

### Post by roberthleeii on 2019-11-17
I am researching how to get OneDrive working in Ubuntu. From what I have seen there seem to be several different options but all that I have seen seem to be problematic and/or complicated, especially for a Ubuntu newbie like me. I got google drive working extremely easily and was surprised that there was not a similar option for OneDrive….
 
 
 I have several hundred GB of data in my OneDrive so a 100% sync will not work. Drive access with an optional folder sync wold be my ideal option if possible. Being able to move the synced folder to my second HD would also be a big plus.  
 
 
 Any advice for a good way to sync OneDrive is appreciated.  
 
 
 Thanks in advance,  
 
 
 Robert

---

### Post by esa1975 on 2019-11-18
No idea if you're looking for a paid option but [InSync]("https://www.insynchq.com/") has a very nice GUI option for this. I wouldn't be surprised if Microsoft comes out with an option before too long given their recent Linux push. No idea when that might be though,

---

### Post by Mark Phelps on 2019-11-18
I wouldn't hold your breath on Linux support from MS. 

Their "recent Linux push" has been limited to Windows Subsystem for Linux (WSL) -- which provides a BASH (shell) to run command line stuff.  GUI apps are not supported.

Here's some info on WSL -- so you can see how really limited it is: [https://docs.microsoft.com/en-us/windows/wsl/faq]("https://docs.microsoft.com/en-us/windows/wsl/faq")

---

### Post by yaminb on 2019-11-18
I got it working without too much trouble.

I pretty much followed the instructions on the wiki.
[https://github.com/abraunegg/onedrive](https://github.com/abraunegg/onedrive)
Once you have the dependencies (i can't recall if I needed any or not).

git clone [https://github.com/abraunegg/onedrive.git](https://github.com/abraunegg/onedrive.git)
(I just did this in my home directory)
cd onedrive
./configure
make clean; make;
sudo make install

then you run it the first time
[https://github.com/abraunegg/onedrive/blob/master/docs/USAGE.md](https://github.com/abraunegg/onedrive/blob/master/docs/USAGE.md)
See First Run

Then I added a startup applications with the following command:
onedrive --monitor

I use this tool to configure startup applications 'Startup Applications'
I don't know how to link to it from the store, but the description says this.

The Startup Applications Preferences app allows configuring applications to run automatically when logging in to your desktop. This app complies with the FreeDesktop.org Desktop Application Autostart Specification so it will work even if your chosen desktop is not GNOME.


I haven't played with any of the settings, but it syncs fine. Every 30 or 45 seconds or so, it scans for changed files.
I certainly wouldn't try anything complicated like working on the same file in two different systems or something like that. 
But for basic usage, I haven't had any troubles.

---

### Post by howefield on 2019-11-19
rclone might be worth a look.

I use it to mount a Onedrive folder locally.

---


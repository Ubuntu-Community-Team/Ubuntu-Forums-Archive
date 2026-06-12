---
title: "Guide for playing RMVB real media in mplayer"
date: 2007-11-18
forum: General Help
---

### Post by bhuthogg on 2007-11-18
**[CENTER]This is a copy paste but i have found it so usefull[/CENTER]**
[URL="http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/"]
Here is original link  [/URL]


How to play .rmvb files in Ubuntu
July 27th, 2007 by Ross McKillop | Print This Post Print This Post
Linux

This tutorial will take you step by step through installing all of the software necessary to play rmvb (RealMedia Variable Bitrate) files in Ubuntu Linux.

Though the steps and screenshots are specific to Ubuntu, they will likely be similar for other versions of Linux. With that said, be sure to read the MPlayer README file if you’re not using Ubuntu. Similar to some of the other tutorials on Simplehelp, this is almost certainly not the only way to play .rmvb files in Ubuntu, but it’s the easiest way I could find. If you know of a easier method, by all means please feel free to leave a comment.

   1. The first step in playing .rmvb files in Ubuntu is to use the Synaptic Package Manager to install MPlayer. When you mark MPlayer for installation, you’ll be prompted to install additional software packages (if they’re not already installed).

      play rmvb files in ubuntu linux
      click to enlarge
   2. After MPlayer has been installed, exit out of the Synaptic Package Manager and visit the MPlayer binary codec download page. Download the codec package for your platform (for example, if you’re using a 32bit Intel or AMD processor, download the Linux x86 package).

      Save the file to your desktop (or home folder). Once the download has completed, double-click that file. Select the folder to uncompress, and click the Extract button.

      play rmvb files in ubuntu linux
      click to enlarge
   3. Choose a location to extract the files (your desktop is ideal) and again click Extract.

      play rmvb files in ubuntu linux
      click to enlarge
   4. Make sure the files extracted correctly. They’ll be in a folder titled essential-date.

      play rmvb files in ubuntu linux
   5. Open up a Terminal by selecting Applications -> Accessories -> Terminal.

      play rmvb files in ubuntu linux
   6. Enter the following commands (and your password when prompted):

          cd Desktop
          cd essential-date
          sudo mkdir /usr/lib/win32
          sudo cp * /usr/lib/win32

      play rmvb files in ubuntu linux
      click to enlarge
   7. Launch MPLayer by selecting Applications -> Sound & Video -> MPlayer Movie Player. Right-click in the Mplayer - Video window and select Preferences from the menu.

      play rmvb files in ubuntu linux
   8. Select the Video tab and change the Available drivers: to x11 X11 (XImage/Shm).

      play rmvb files in ubuntu linux
      click to enlarge
   9. Select the Codecs & demuxer tab and change the Video codec family: to RealVideo decoder and the Audio codec family: to FFmpeg/libavcodec audio decoders. When you’re done, click OK and close down MPlayer.
9a
1. Open Synaptic Package Manager.
2. Search libstdc++5 and install it.
3. Download new Codec from [http://www.mplayerhq.hu/design7/dload.htm]("http://www.mplayerhq.hu/design7/dload.htm")l and install it.
      play rmvb files in ubuntu linux
      click to enlarge
  10. Locate one of your .rmvb files, right-click it and select Properties.

      play rmvb files in ubuntu linux
  11. Select the Open With tab and change whatever the default is to MPlayer Movie Player. Click Close.

      play rmvb files in ubuntu linux
      click to enlarge
  12. Double-click any of your .rmvb files and they should open up in MPlayer and start playing.

      play rmvb files in ubuntu linux 

Hope this helps someone as it did me :)

---

### Post by namanbagga on 2007-11-18
Why don't you just install [Real Playe]("http://www.real.com/linux/")r?

---

### Post by dingorunner on 2007-11-21
I believe free version of RealPlayer doesn't include all kind of options Mplayer does, such us advanced  Video Equalizer. That's why I'd prefer fix this issue rather than just installing RealPlayer..
The solution for this problem it's to follow those steps; [http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/) (I guess you already did) but there are some minor changes:
Change:
cd Desktop
cd essential-date
sudo mkdir /usr/lib/win32
sudo cp * /usr/lib/win32
To:
cd Desktop
cd essential-date
sudo mkdir /usr/lib/codecs
sudo cp * /usr/lib/codecs

Make sure you're working  with essential-20071007.

---

### Post by bluemech on 2007-11-21
> **dingorunner said:**
> 
Change:
...

To:
...

Make sure you're working  with essential-20071007.

Hmm, I've just installed Gutsy and it still referenced /usr/lib/win32. I suggest putting a symlink to be safe.

After dingorunner's changes, do this:

```

sudo ln -s /usr/lib/codecs /usr/lib/win32

```

And that'll run those .rmvb files no problem.

---

### Post by dingorunner on 2007-11-21
Now the weirdest thing is happening to Mplayer.
When I double-click a file icon in order to play any video file, the following error message shows up: Failed to open File:///<file>. But if I open the file by right-clicking the screen and the Open > Play file it works, but when I use any playback button it goes; Error! gnome_screensaver _control (). but the command works anyway. It also works by typing mplayer <file> in the terminal but with no playback buttons.

---

### Post by process91 on 2007-11-25
I get this same error too. When I double-click a file it doesn't play it at all, but when I choose to open the file from within mplayer it plays correctly.

---

### Post by Ocxic on 2008-01-01
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

the easy way

---

### Post by later on 2008-03-19
for me it works well but i hav still a little problem i can't play the movie in full screen.Is there any solution

---

### Post by rushtoshankar on 2008-05-22
try this option to make the mplayer to play in full screen.

go to preferences, then click on video tab ... please select 'xv X11/xv' instead of 'x11 X11 (Ximage/Shm)' .. it worked for me .. 
enjoy !

---


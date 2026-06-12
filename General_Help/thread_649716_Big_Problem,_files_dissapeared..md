---
title: "Big Problem, files dissapeared."
date: 2007-12-25
forum: General Help
---

### Post by xombey on 2007-12-25
I am running a dual boot xp64 Ubuntu Feisty Fawn 7.04.  While surfing the web under Ubuntu  I noticed that all of my files on the desktop have been deleted.  When I go to Places-home folder it gives the error: "Nautilus could not create the required folder "/home/xombey/Desktop".  Before running Nautilus, please create the following folder, or set permissions such that nautilus can create it".

All of the files lost are on an ext3 partition.  The OS works fine so far except for what I've listed and the missing files.

When I run "sudo Nautilus"  I can access root ,desktop and filesystem folders.  There is nothing in the desktop folder.  I can't access the trash folder in the menu bar next to the workspace switch icon. It gives me the same error listed above.  The missing files are not in the .trash folder either.  I have lost everything I have downloaded worked on or written for the last year.  ( I have an old back up, but not very recent)  About 300gb worth of files are missing.  

What happened, how did I do it,  and more importantly what should I do to repair it?

Please help.  Thank you.

---

### Post by taurus on 2007-12-25
Open a terminal and post the output of this command here.  Remove names of files/directories that you don't want people to see.

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by nick_h on 2007-12-25
> What happened, how did I do it
Have you run any commands from the terminal that you didn't fully understand?

---

### Post by xombey on 2007-12-25
ok.  I've typed that in.  I don't know what to do from here.

---

### Post by nick_h on 2007-12-25
and what was the output?

---

### Post by xombey on 2007-12-25
total 52796
drwxr-xr-x 46 xombey xombey     4096 2007-12-25 10:55 .
drwxr-xr-x  3 root   root       4096 2007-11-28 06:28 ..
-rw-r--r--  1 xombey xombey     9797 2007-12-07 00:20 9 days.ods
drwxr-xr-x  3 xombey xombey     4096 2007-12-01 16:00 .avidemux
drwxr-xr-x 10 xombey xombey     4096 2007-12-12 15:00 .azureus
drwxr-xr-x 13 xombey xombey     4096 2007-11-29 07:19 Azureus Downloads
-rw-------  1 xombey xombey     1490 2007-12-25 11:40 .bash_history
-rw-r--r--  1 xombey xombey      220 2007-11-28 06:28 .bash_logout
-rw-r--r--  1 xombey xombey     2298 2007-11-28 06:28 .bashrc
drwx------  6 xombey xombey     4096 2007-11-28 13:31 .BitTornado
drwxr-xr-x  2 xombey xombey     4096 2007-12-07 14:07 .cddb
drwxr-xr-x  5 xombey xombey     4096 2007-12-04 10:11 .comix
drwxr-xr-x  4 xombey xombey     4096 2007-11-28 12:36 .config
drwxr-xr-x  4 xombey xombey     4096 2007-12-25 10:38 .dc++
-rw-r--r--  1 xombey xombey    32395 2007-12-25 09:54 Desktop
-rw-------  1 xombey xombey       26 2007-11-28 11:33 .dmrc
-rw-------  1 xombey xombey       16 2007-11-28 11:33 .esd_auth
drwxr-xr-x  7 xombey xombey     4096 2007-12-25 10:53 .evolution
lrwxrwxrwx  1 xombey xombey       26 2007-11-28 06:28 Examples -> /usr/share/example-content
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 11:33 .fontconfig
drwxr-xr-x  4 xombey xombey     4096 2007-12-16 13:13 .frostwire
drwx------  5 xombey xombey     4096 2007-12-25 10:55 .gconf
drwx------  2 xombey xombey     4096 2007-12-25 12:10 .gconfd
-rw-r-----  1 xombey xombey        0 2007-12-25 11:22 .gksu.lock
drwxr-xr-x  4 xombey xombey     4096 2007-12-03 07:36 .gnome
drwx------ 14 xombey xombey     4096 2007-12-25 10:53 .gnome2
drwx------  2 xombey xombey     4096 2007-11-28 11:33 .gnome2_private
drwxr-xr-x  2 xombey xombey     4096 2007-11-29 08:24 .gstreamer-0.10
-rw-------  1 xombey xombey       99 2007-12-25 08:33 .gtk-bookmarks
-rw-r--r--  1 xombey xombey       88 2007-11-28 11:33 .gtkrc-1.2-gnome2
-rw-------  1 xombey xombey     2920 2007-12-25 10:55 .ICEauthority
drwxr-xr-x  2 xombey xombey     4096 2007-11-29 21:43 .icons
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 12:13 Incomplete
drwxr-xr-x  3 xombey xombey     4096 2007-12-05 03:13 .java
drwx------  3 xombey xombey     4096 2007-11-28 13:09 .kde
-rw-------  1 xombey xombey       35 2007-12-04 09:26 .lesshst
drwxr-xr-x  4 xombey xombey     4096 2007-12-07 14:09 .listen
drwx------  3 xombey xombey     4096 2007-11-28 12:32 .local
-rw-r--r--  1 root   root       1632 2007-12-01 14:27 Logitech extra keys
drwxr-xr-x  2 xombey xombey     4096 2007-12-07 14:09 .lyrics
drwx------  3 xombey xombey     4096 2007-11-29 04:58 .macromedia
-rw-r--r--  1 xombey xombey     3156 2007-12-22 23:59 .mailcap
drwxr-xr-x  3 xombey xombey     4096 2007-11-28 13:09 .mcop
-rw-------  1 xombey xombey       31 2007-12-22 23:29 .mcoprc
drwx------  3 xombey xombey     4096 2007-11-28 11:33 .metacity
drwx------  4 xombey xombey     4096 2007-11-29 04:58 .mozilla
drwxr-xr-x  2 xombey xombey     4096 2007-12-02 15:39 .mplayer
drwxr-xr-x  3 xombey xombey     4096 2007-12-07 14:09 Music
drwxr-xr-x  3 xombey xombey     4096 2007-12-25 10:53 .nautilus
-rw-r--r--  1 xombey xombey 53174272 2007-12-25 10:53 nautilus-debug-log.txt
drwx------  3 xombey xombey     4096 2007-12-19 12:58 .openoffice.org2
drwx------  9 xombey xombey     4096 2007-12-23 00:14 .opera
-rw-r--r--  1 xombey xombey      566 2007-11-28 06:28 .profile
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 13:09 .qt
-rw-------  1 xombey xombey    34700 2007-12-23 00:15 .realplayerrc
-rw-------  1 xombey xombey   130801 2007-12-25 10:56 .recently-used
-rw-r--r--  1 xombey xombey   349013 2007-12-24 17:01 .recently-used.xbel
-rw-------  1 xombey xombey     1024 2007-11-29 03:57 .rnd
-rw-r--r--  1 xombey xombey        0 2007-11-28 11:53 .sudo_as_admin_successful
drwxr-xr-x  2 xombey xombey     4096 2007-11-29 21:43 .themes
drwx------  4 xombey xombey     4096 2007-11-28 13:00 .thumbnails
drwx------  4 xombey xombey     4096 2007-12-22 23:59 .Trash
drwxr-xr-x  3 xombey xombey     4096 2007-11-29 19:06 Unknown Artist
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 11:36 .update-manager-core
drwx------  2 xombey xombey     4096 2007-11-28 11:33 .update-notifier
drwxr-xr-x  3 xombey xombey     4096 2007-11-29 07:19 .vlc
drwxr-xr-x  2 xombey xombey     4096 2007-12-08 19:23 .wapi
drwxr-xr-x  4 xombey xombey     4096 2007-12-12 22:04 .wine
-rw-------  1 xombey xombey      121 2007-12-25 10:55 .Xauthority
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 13:09 .xine
-rw-r--r--  1 xombey xombey     4442 2007-12-25 11:49 .xsession-errors

---

### Post by taurus on 2007-12-25
Isn't Desktop a directory?  You have it on your $HOME as a file!  What is it anyway?  Post the output of this command here.

```
file Desktop
```

---

### Post by xombey on 2007-12-25
desktop: ERROR: cannot open `desktop' (No such file or directory)

---

### Post by xombey on 2007-12-25
oops, (case sensitive)

Desktop: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJ"

---

### Post by taurus on 2007-12-25
> **xombey said:**
> desktop: ERROR: cannot open `desktop' (No such file or directory)

Unix/Linux is CaSe SenSiTive so desktop is not the same as Desktop.

```
file [COLOR="Blue"]D[/COLOR]esktop
```

---

### Post by taurus on 2007-12-25
> **xombey said:**
> oops, (case sensitive)

Desktop: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJ"

So, it's a jpeg.  Try to rename it and then create a new Desktop directory so you can save your stuff to it.

```
mv Desktop image.jpg
mkdir Desktop
```
Now, everything should be back to normal again.

---

### Post by xombey on 2007-12-25
I just looked in the administration tab in the system list to see if I had a back up program.  There is nothing listed before "keyring manager"  A-j is gone.

---

### Post by xombey on 2007-12-25
Thank you for helping me with that.  Any idea how all my files were deleted?  Why am I missing system tools?

---

### Post by xombey on 2007-12-25
The files disappeared while I was surfing the web.  One minute here, next gone.

---

### Post by nick_h on 2007-12-25
Were all the files that are missing in the Desktop folder?

---

### Post by xombey on 2007-12-25
Yes, although it appears that some things are missing from the system-administration menu too.

---

### Post by taurus on 2007-12-25
Did you by any chance change your groups?  What's the output of this command?

```
id
```

---

### Post by xombey on 2007-12-25
uid=1000(xombey) gid=1000(xombey) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(xombey)

---

### Post by nick_h on 2007-12-25
That list looks OK.

Have you checked your disk usage to see if it has decreased by the 300G of files that are missing?

---

### Post by xombey on 2007-12-25
Yes.  I had about 20g of free space.  Now it is ~200.  Is there any way to get the files back?

---

### Post by nick_h on 2007-12-25
Recovering files from an ext3 filesystem isn't easy.  To stand a chance you need to stop using the partition immediately.

A quick google for "ext3 data recovery" got some hits - for example [link](http://www.linuxquestions.org/questions/linux-distributions-5/best-liverescue-cd-for-ext3-data-recovery-417651/).

---

### Post by jeffus_il on 2007-12-25
would be interesting to see your "history" output at the bash prompt.

---

### Post by xombey on 2007-12-25
1  glxinfo
    2  lsmod
    3  glxgears
    4  glxinfo
    5  sudo gedit /etc/x11/xorg.conf
    6  sudo dpkg-reconfigure xserver-xorg
    7  sudo gedit /etc/x11/xorg.conf
    8  mplayer
    9  sudo apt-get install xbindkeys-config
   10  $ mplex -f -o /home/xombey/Desktop/Simpsons ready for svcd.m2v Simpsons ready.mp2
   11  mplex -f -o /home/xombey/Desktop/Simpsons ready for svcd.m2v Simpsons ready.mp2
   12  sudo apt-get install mjpegtools
   13  mplex -f -o /home/xombey/Desktop/Simpsons ready for svcd.m2v Simpsons ready.mp2
   14  $ mplex -f -o /home/xombey/Desktop/Simpsons ready for svcd.m2v Simpsons ready.mp2
   15  mplex -f -o /home/xombey/Desktop/Simpsons ready for svcd.m2v Simpsons ready.mp2
   16  sudo apt-get install vlc-plugin-alsa
   17  sudi
   18  sudo
   19  cd /usr/share/mime
   20  ls video/* | sed 's/.xml/=vlc.desktop/' | tee -a ~/.local/share/applications/defaults.list
   21  ls audio/* | sed 's/.xml/=vlc.desktop/' | tee -a ~/.local/share/applications/defaults.list
   22  sudo apt-get install realplayer killall gnome-panel
   23  sudo apt-get install realplayer10gold killall gnome-panel
   24  sudo apt-get install realplayer10GOLD killall gnome-panel
   25  chmod a+x RealPlayer10GOLD.bin
   26  chmod a+x '/home/xombey/Desktop/RealPlayer10GOLD.bin' 
   27  chmod a+x /home/xombey/Desktop/RealPlayer10GOLD.bin 
   28  cd /home/xombey/Desktop/RealPlayer10GOLD.bin
   29  cd /home/xombey/Desktop/
   30  chmod a+x RealPlayer10GOLD.bin
   31  realplayer1-GOLD
   32  realplayer10GOLD
   33  realplayer10GOLD.bin
   34  sudi apt-get install realplay
   35  sudo apt-get install realplay
   36  gksudo nautilus
   37  apt-get install testdisk
   38  sudo apt-get install testdisk
   39  testdisk /list
   40  testdisk
   41  gksudo testdisk
   42  sudo nautilus
   43  sudo testdisk
   44  ls -la~
   45  ls -la ~
   46  file desktop
   47  file Desktop
   48  ls help
   49  ls- help
   50  ls --help
   51  mv Desktop image.jpg
   52  mkdir Desktop
   53  mv
   54  mv --help
   55  id
   56  history
xombey@MetalBrain:~$

---

### Post by jeffus_il on 2007-12-25
What does 

mv Desktop image.jpg

do ?

---

### Post by taurus on 2007-12-25
> **jeffus_il said:**
> What does 

mv Desktop image.jpg

do ?

If you've read the entire thread, you would have known that somehow his Desktop was not a directory like it should.  Instead, it was a jpeg so I told him to rename it to something else, image.jpg, and then created a Desktop directory.

---

### Post by jeffus_il on 2007-12-25
Yeah, I saw that after submitting, How was an image called Desktop created, Is this the problem?

---

### Post by taurus on 2007-12-25
> **jeffus_il said:**
> Yeah, I saw that after submitting, How was an image called Desktop created, Is this the problem?

You have to ask him because I have no idea why Desktop directory became Desktop image.

---

### Post by Islington on 2007-12-25
While this may be an idiotic question, what does the jpeg look like? </idle curiosity>
I know on windows you can use a copy /b command to fuse together a rar and jpeg file.

I really hope all your files are okay.

---

### Post by jeffus_il on 2007-12-25
Would it be reasonable to say that the directory "Desktop" must have been deleted or overwritten in order to create the image?

---

### Post by jeffus_il on 2007-12-25
Have we seen an "ls -la" of the .Trash directory?

---

### Post by jeffus_il on 2007-12-25
and a "du -hs" in the home directory

---

### Post by xombey on 2007-12-25
drwx------  5 xombey xombey     4096 2007-12-25 13:56 .
drwxr-xr-x 48 xombey xombey     4096 2007-12-25 15:09 ..
-rw-r--r--  1 xombey xombey 40702179 2007-12-15 16:10 alien vs predator 2 - requiem trailer.wmv
drwxr-xr-x  2 xombey xombey     4096 2007-12-19 19:25 Assassin School-1 to 6
drwxr-xr-x  2 xombey xombey     4096 2007-11-28 14:32 _B7_B8_D7_EF_CF_D6_B3_A1_B5_F7_B2_E9CSI_20_B5_DA_B0_CB_BC_BE1-3_BC_AF_720P_x264_4099hifi
-rw-r--r--  1 xombey xombey 44847108 2007-12-13 13:04 Enigma - Return To Innocence (Escaflowne Anime).mpg
drwxr-xr-x  2 xombey xombey     4096 2007-12-19 10:55 Guitar Hero 3 Soundtrack
-rwxr-xr-x  1 xombey xombey  5790356 2007-12-22 23:30 RealPlayer10GOLD.bin

---

### Post by xombey on 2007-12-25
[email]xombey@MetalBrain:~/.Tras[/email]h$ du -hs
549M

---

### Post by jeffus_il on 2007-12-25
> **Islington said:**
> While this may be an idiotic question, what does the jpeg look like? </idle curiosity>
I know on windows you can use a copy /b command to fuse together a rar and jpeg file.

I really hope all your files are okay.

No one's an idiot, I once formatted the A: drive on a HP machine, not realizing that they had decided to call the hard drive A: and not C: as the rest of the world was doing...

A shot in the dark might just hit the target ...

---

### Post by xombey on 2007-12-25
The Desktop.jpg isn't on my system any more.  I don't know why.  I don't know what it looks like either.  

As to why or how it became changed, I have no idea.  I was reading a website when I noticed that my background was different and everything on the desktop was gone.  Here one minute, gone the next.  The friend of mine that introduced me to Linux said that someone probably "glomped" (sp?) me through my ntfs partition, or something like that.  The only people I could call enemies that I know barely know how to turn a computer on, much less attack one.  Without a hammer, that is.

---

### Post by taurus on 2007-12-25
It's not Desktop.jpg; it's image.jpg.  ](*,)

You changed Desktop file to image.jpg, remember?

---

### Post by Islington on 2007-12-25
> **taurus said:**
> It's not Desktop.jpg; it's image.jpg.  ](*,)

You changed Desktop file to image.jpg, remember?
:-k
his history says that he has been root in nautilus, is it possible that he moved his desktop folder to another location?

---

### Post by nick_h on 2007-12-25
> is it possible that he moved his desktop folder to another location?
His free space has increased from about 20 to 200G (post #20) so that it appears that he has lost files.

---

### Post by Islington on 2007-12-25
> **nick_h said:**
> His free space has increased from about 20 to 200G (post #20) so that it appears that he has lost files.

also might be idiotic, but I have to idea how to confirm this. Is the trash part of used space or free space? if it is a part of free space could the folder be in root trash? post 31 &32 show it isnt in his user trash.

---

### Post by nick_h on 2007-12-25
It would be worth the OP doing
```
sudo ls -al /root/.Trash
```

---


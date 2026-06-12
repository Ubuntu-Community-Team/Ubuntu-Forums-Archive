---
title: "playing internet radio stations"
date: 2005-10-25
forum: General Help
---

### Post by autonomy on 2005-10-25
Hello,

I'd like to play internet radio stations right after installing, but Rhythmbox keeps saying the streams ended. This doesn't look good for recommending Ubuntu/Linux/GNU. I like Rhythmbox though since I can put all of my radio stations up there instead of on my Firefox bookmarks. I've seen a thread about configuring Rhythmbox in 5.04. Are there any instructions for getting Rhythmbox to play streams in Breezy Badger? Otherwise, I'd probably just install QCD, which is a weird thing to have to do.

Thanks

---

### Post by bionnaki on 2005-10-25
do this

apt-get install streamtuner

that's all you need.

---

### Post by autonomy on 2005-10-25
thanks but i have to guess, i put that in the terminal? i couldn't find it. (applications: system tools: no dice.)

---

### Post by monkey89 on 2005-10-25
The terminal was moved to Applications -> Accessories.  You can always use synaptic though.

-Monkey

---

### Post by autonomy on 2005-10-25
Thanks, I entered apt-get install streamtuner in the terminal, but it didn't work; and I opened Synaptic; but I couldn't find streamtuner; and I didn't know what to do. I couldn't play videos in totem either.

---

### Post by kperkins on 2005-10-25
You probably need to enable universe and multiverse repositories.

---

### Post by orbinick on 2005-10-25
[quote=kperkins]You probably need to enable universe and multiverse repositories.[/quote] Right. without those repos, it won't show on synaptic.

gxine does streams too, but its menu driven as autonomy said doesn't like.

---

### Post by autonomy on 2005-10-25
[quote=kperkins]You probably need to enable universe and multiverse repositories.[/quote] I'm doing that, now.

---

### Post by Appolusionist on 2005-10-25
[quote=autonomy]How does one do that?[/quote] 
Do this from terminal

> sudo gedit /etc/apt/sources.list 
and then edit your file to look like this example.

 > #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse 
and then from terminal 

> sudo apt-get update 
and then you should be able to install streamtuner as instructed before.

---

### Post by autonomy on 2005-10-25
OK, Streamtuner is installed, but Rhythmbox still claims that an "Unexpected end of stream" was found.

---

### Post by Appolusionist on 2005-10-25
[quote=autonomy]OK, Streamtuner is installed, but Rhythmbox still claims that an "Unexpected end of stream" was found.[/quote] 
Streamtuner is a separate app for listening to Internet Radio. Please go to [http://ubuntuguide.org/#streamtuner]("http://ubuntuguide.org/#streamtuner") to review on how to refresh your gnome panel. The app will appear under Applications -> Sound & Video -> streamtuner. FYI The [ubuntuguide]("http://ubuntuguide.org") is based on Hoary 5.04, but contains excellent info that still pertains to Breezy 5.10.

---

### Post by autonomy on 2005-10-25
Thanks, I also saw that, [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#restartgnomewithoutreboot"), I think. (How to restart GNOME without rebooting the computer) I tried two radio stations, creating new preselections, and Streamtuner said, "Unable to tune in: Failed to execute child process 'xmms' (no such file or directory)."

---

### Post by orbinick on 2005-10-25
install xmms an maybe some plugins from synaptic

---

### Post by bionnaki on 2005-10-26
did you install the codecs & gstreamer stuff?

> # Get(download) and install various codecs from repositories

    * sudo apt-get install gstreamer0.8-plugins
    * sudo apt-get install gstreamer0.8-lame
    * sudo apt-get install gstreamer0.8-ffmpeg
    * sudo apt-get install lame
    * sudo apt-get install sox
    * sudo apt-get install ffmpeg
    * sudo apt-get install mjpegtools
    * sudo apt-get install vorbis-tools

# then download and install w32 codec & libdvdcss2 (search forums for links)

    * sudo dpkg -i xxxxx.deb

# REGISTER codecs

    * gst-register-0.8

# Get and install xine (or gxine)



---

### Post by autonomy on 2005-10-26
Now, a window pops up, asking for a file name for XMMS to play.

---

### Post by Foaming Draught on 2005-10-26
This thread has alerted me to Streamtuner's existence. Isn't it wonderful! I don't use pre-selections, I just highlight the station which looks as if it might be good, click on the traditional Play icon at the top of the screen, xmms springs into life and buffers the station for a few seconds then starts playing. If it's what I want, I bookmark it. Not too sure what the pre-selection facility is for.

---

### Post by Foaming Draught on 2005-10-26
Now here's a funny thing. I switched my soundcard (in System, Preferences, Sound) from my internal ESS card to Logitech USB headphones, and the next station I tried to tune to, I got the same pop-up as autonomy  -  "Choose a file". I've switched back to ESS and I get stations playing through speakers straight away again, but no sign of the xmms panel.

---

### Post by Foaming Draught on 2005-10-26
Now xmms has miraculously reappeared, all by itself, but as a skinny panel. I think that the "Play file" dialogue which autonomy and I saw/were seeing, is this same xmms panel in a different guise again.

---

### Post by autonomy on 2005-10-26
is there a solution to this?

---

### Post by autonomy on 2005-10-27
One doesn't need Streamtuner to play streams in Ubuntu. One just needs to install the audio codecs as instructed in the Ubuntu F.A.Q. Guide.

---

### Post by asnd16 on 2007-01-29
I have the same issue, is there a FIX for this issue?

---


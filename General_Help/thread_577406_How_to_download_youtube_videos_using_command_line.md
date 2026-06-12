---
title: "How to download youtube videos using command line"
date: 2007-10-16
forum: General Help
---

### Post by elexhobby on 2007-10-16
Hi..

I wanted to schedule downloads to take place at night, which I figured out to do using crontab and wget.

However, what do I use if I want to download youtube or google videos? I need a command line approach because that is what I can write in the crontab file. Can it be done using wget? If yes, how?

Thanks in advance.

---

### Post by elexhobby on 2007-10-16
Ok I found a way for youtube.. The program youtube-dl does so.. Does anybody know how to download google videos using command line?
Thanks again..

---

### Post by elexhobby on 2007-10-19
Is there no CLI method to download google videos? Please help..

---

### Post by Gun_Smoke on 2007-10-19
My first hit from Google.

[http://home.gna.org/clive/](http://home.gna.org/clive/)

---

### Post by elexhobby on 2007-10-19
Thanks for the reply.. I too had found this.. But when I tried to install it, it said I would need python-central 0.5.8, which I haven't found.. In Synaptic and on the web, I found that python-central 0.5.6 is used by Edgy.. However, I did find python-central 0.5.15.. However, when I tried to install that, it said I would need dpkg 1.14.5.. Again Edgy supports dpkg 1.13.22.. Now, I guess this will continue - with each package requiring some other recent package.. So I am looking for a simpler way to download google videos, may be a simple user-script..

---

### Post by elexhobby on 2007-10-23
So there's no CLI way to download google videos? Please help..

---

### Post by UK-Wobbie on 2007-10-23
> **elexhobby said:**
> Hi..

I wanted to schedule downloads to take place at night, which I figured out to do using crontab and wget.

However, what do I use if I want to download youtube or google videos? I need a command line approach because that is what I can write in the crontab file. Can it be done using wget? If yes, how?

Thanks in advance.

Have you got firefox? If so you can download "Fast Video Download" What will download Youtube,Google videos, And many more!

Here [https://addons.mozilla.org/en-US/firefox/addon/3590](https://addons.mozilla.org/en-US/firefox/addon/3590) \\:D/:mrgreen:](*,)):P:guitar::^o=D>:biggrin:

For Google videos [http://video.google.com/](http://video.google.com/)

---

### Post by elexhobby on 2007-10-23
Hi.. It seems you didn't get my problem.. I can obviously download them using fierfox or many other GUI applications. But that requires me to be present to click on the link.. If there is a command line approach to do the same, I can schedule the download to take place at night through crontab.. This does not require me to stay awake.. Simply leaving the computer on is enough..
Please.. The problem seems so simple.. There has to be some way.. I wish I knew a bit of kernel programming, so that I could write a shell script for myself..

---

### Post by bodhi.zazen on 2007-10-23
You could try wget or curl

wget [http://your_site.com/file_to_download](http://your_site.com/file_to_download)

---

### Post by elexhobby on 2007-10-23
I didn't get you.. What would be the file_to_download for a google video? Please could you elaborate a bit..

---

### Post by verb3k on 2007-10-24
This is absolutely what you want:
[http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)

download it to your desktop

do this in the terminal:

chmod a+x ~/Desktop/youtube-dl

sudo cp ~/Desktop/youtube-dl /usr/bin/


and then you can use it by typing this in the terminal :

youtube-dl url

put the link of the video instead of word url

and the video will be downloaded in the current working directory :)

---

### Post by elexhobby on 2007-10-25
Hehe.. Thanks for responding so nicely.. But I have mentioned exactly this way to download youtube videos in my earlier posts.. The problem I am now facing is, is there a similar such script to download google videos?

---

### Post by Roboticus on 2007-10-25
I have an absolutely horrible idea of a way that might work:  Build an html page (simple) with the links you want to download.  Then use cron to start a script that starts firefox, and then feeds keyboard events to it.  Just send it the keystrokes to click on a link and select the next link ... lather, rinse, repeat.

;^)  I *told* you it was horrible!

But it might work, and might not be too hard to cobble together.

...roboticus

---

### Post by elexhobby on 2007-10-26
Thanks robotics.. I had a similar idea yesterday, very similar to what you've said.. What I can do is ask firefox through command line  to run the google video.. This saves a copy of the video in the /tmp folder.. I can later retrieve the copy from the /tmp folder..

Thanks a lot to all those who helped!!

---

### Post by Keith Hedger on 2007-11-02
Hi,
I know this is for youtube but it should work with a bit of work for other video sites
Also the firefox plugins and youtube.dl keep breaking, this script is easier to keep updated.
I use this script to download videos to watch later on my ipod after processing with ffmpeg
You may have to look at the page source of a google video (for instance) to see exactly what parameters to pass to wget.

Usage is ./downloadvideo.sh [http://www.youtube.com/watch?v=r44OFO-MNPo](http://www.youtube.com/watch?v=r44OFO-MNPo)

For instance to download ashes to ashes by Bowie
Dont forget to set the executable flag!

---

### Post by ukripper on 2007-11-02
For PSP I use Firefox addon and PSPVC to convert works perfect together in duo

and sometimes I use AVIDEMUX 2.4 to convert  [http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml](http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml)

---

### Post by Keith Hedger on 2007-11-02
Whoops! Wrong file !
try this instead

---

### Post by crjackson on 2007-11-02
> **elexhobby said:**
> Hi..

I wanted to schedule downloads to take place at night, which I figured out to do using crontab and wget.

However, what do I use if I want to download youtube or google videos? I need a command line approach because that is what I can write in the crontab file. Can it be done using wget? If yes, how?

Thanks in advance.

I use this [http://www.getdeb.net/search.php?keywords=QtTube]("http://www.getdeb.net/search.php?keywords=QtTube").

No sure if it will work with google video or not.  It's a nice app.  I'd give it a try.

---


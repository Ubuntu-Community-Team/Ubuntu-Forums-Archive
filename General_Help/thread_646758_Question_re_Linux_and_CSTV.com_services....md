---
title: "Question re: Linux and CSTV.com services..."
date: 2007-12-21
forum: General Help
---

### Post by Mtnear on 2007-12-21
I currently subscribe to cstv.com's "all-access" service here in the states which enables me to listen and, in certain cases watch, my favorite university's sports teams via the net...on Windows with Internet Explorer.

The requirements state that Internet Explorer 6 and / or 7 is needed in conjunction with Windows Media Player 9 or 10. I've tried to workaround this via IEs4Linux, which provides me with IE 6, but once inside the browser the buttons that activate play / pause, etc. do not seem to function. I'm not sure if this is due to things that would be in place inside IE in a Windows based system that are absent on a Linux machine, but it almost works. I was hoping that someone might have some recommendations on how to get services such as this working on a Linux system, since unfortunately it's content like this that keeps me tied to Windows. I would think that cstv.com would want all customers, not just the ones they choose, but I guess not.

Thanks for any help.

---

### Post by tgalati4 on 2007-12-21
Super cheesy solution:

Go to the video you want to watch.

Go to the "Embed" box can cut and paste the info into a text editor (like gedit).

Extract the content and in a terminal:


wget [http://mfile.akamai.com/9192/wmv/cstv.download.akamai.com/9192/cstv_videos/football/1207/120507_cff_flutie_2.asx](http://mfile.akamai.com/9192/wmv/cstv.download.akamai.com/9192/cstv_videos/football/1207/120507_cff_flutie_2.asx)

(Recent Doug Flutie interview)

Install VLC if you haven't already:

>sudo apt-get update
>sudo apt-get install vlc

Open VLC and open the flutie_interview.asx watch and enjoy.  You can record the stream in VLC for later viewing.

I like Flutie Flakes!

---


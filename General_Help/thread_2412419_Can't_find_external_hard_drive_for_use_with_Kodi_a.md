---
title: "Can't find external hard drive for use with Kodi and Plex Server"
date: 2019-02-12
forum: General Help
---

### Post by dan40 on 2019-02-12
Hey all, I have a really old computer (~10 years old) that I was running Windows 10 on that I am using for my media centre.  Win*doze* was caching a lot, and when opening web pages, Chrome took upwards of 15-30 seconds to load all the content on the page, depending on what page I was on.  I thought, there's got to be a better solution, so I did a full system restore.  Much to my dismay, when I went to the web page again after it was all done, this same behaviour returned, which kind of cheesed me off.  Then I thought, why don't I install Ubuntu Workstation?  I created what I thought was a bootable DVD, but as it turns out, the computer was having trouble reading my internal cdrom drive (this is with Windows).  It's the first time I tried using it after I rebuilt Windows and started to get more and more frustrated.  Then I found a neat little utility that makes bootable USB sticks, so I put Ubuntu Workstation 18.04 on it and in a few minutes had it up and running after booting from  the USB stick, then I installed Kodi, and Plex Server.  This is not my problem.

My problem is, I keep all my media on an external hard drive that when plugged in, shows the hard drive icon on the desktop and I'm able to open it, but when adding libraries such as the folder where I keep my TV Shows, Ubuntu finds it but it's buried deep in my profile. I think the path is /usr/media/dan/mediacentre (or something like that, I'm not at home to verify), but I thought this was really unusual.  Shouldn't I just be able to go add files (to anyone familiar with Kodi) and choose the source folder?  I also thought I did this in Plex, but when I go to add a Library in Plex, I browse to what I believe is the path, but then Plex can't find the mediacentre or the path to TV Shows.  What the heck is going on?

If you plug in an external hard drive, it should be mounted automatically, shouldn't it?  And it should be an available source that you can directly browse to and add content from it, right?  Doesn't work for me.  I would sincerely appreciate any feedback anyone has or who could possibly offer me a suggestion.  Years ago when I tried Ubuntu Workstation I don't believe I had this kind of issue.  What do you suppose I'm doing wrong?

Thanks!

---

### Post by #&amp;thj^% on 2019-02-12
> **dan40 said:**
>  Shouldn't I just be able to go add files (to anyone familiar with Kodi) and choose the source folder? 
If you plug in an external hard drive, it should be mounted automatically, shouldn't it?   What do you suppose I'm doing wrong?

Thanks!
It would normally "If it was mounted"
See if this helps: [https://samhobbs.co.uk/2017/08/kodi-server-part-3-automounting-external-drives-udev](https://samhobbs.co.uk/2017/08/kodi-server-part-3-automounting-external-drives-udev)

---

### Post by dan40 on 2019-02-12
Great! Thank you! I'll give udev a try when I get home and report back.

Cheers!
Dan

---


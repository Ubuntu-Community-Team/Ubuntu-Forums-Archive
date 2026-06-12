---
title: "Firefox and Opera Download/Transfers Issues"
date: 2008-04-02
forum: General Help
---

### Post by testecletes on 2008-04-02
I use Ubuntu quite comfortably, and have learned a lot in the past year and a half of using it. Although I am not the most proficient in Ubuntu (or any other Linux distributions for that matter), I have a problem that I would like to share with you. I was researching the forums to see if any other people were having similar problems, but I see that it might be unique to my situation.

While trying to download large zips or isos on Opera and Firefox, it prematurely finishes, and leaves me with a dead and incomplete file. On Opera, it describes that my transfer has "Failed," while on Firefox, it says that my transfer is complete (when it really leaves me with a broken file). On Opera, I must mention that the transfer fails around 99.9%. I am saving these files to an internal NTFS shared mount. Would this have anything to do?

I am wondering if any of you can be of any assistance. Please post commands that I should copy/paste back to here. Any help would be greatly appreciated :)

---

### Post by bixejo on 2008-04-03
Just to let you know that I'm getting a similar issue. I also open a thread asking for help. I drop here the reference for you to check it in the case you're interested (maybe I'll get an answer earlier.)

[http://ubuntuforums.org/showthread.php?t=743949](http://ubuntuforums.org/showthread.php?t=743949)

For my part, I'll also check your thread to see whether you got a solution.

---

### Post by sekinto on 2008-04-03
You could try a different download manager, for example the Download Them All plugin for Firefox.

Or you could always try the "wget (your file)" method.

---

### Post by testecletes on 2008-04-11
I found out what it was. It's because I was saving my transfers to an NTFS drive. I don't know why this kept happening, but as soon as I got a new 750GB HDD formatted as ext2, it was fine. I think it may be a problem writing to NTFS (or maybe my NTFS partition's MFT or something was messed up.) Hope that helps.

---


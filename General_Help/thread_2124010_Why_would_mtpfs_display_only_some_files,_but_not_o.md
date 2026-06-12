---
title: "Why would mtpfs display only some files, but not others on my Galaxy Nexus?"
date: 2013-03-09
forum: General Help
---

### Post by gotnexusbluz on 2013-03-09
I have a connection between Xubuntu 12.10 and my Galaxy Nexus, but mtpfs displays only some of the files which the latter contains. It displays my folders and most types of files, but not most media files (I've noticed this with images and music so far).

What I've done, after successfully installing libmtp9 and mtpfs, is run the following commands per this web page: [http://android.stackexchange.com/questions/30284/connecting-google-nexus-7-to-linux](http://android.stackexchange.com/questions/30284/connecting-google-nexus-7-to-linux)) 
```

mkdir ~/NexusDrive
mtpfs ~/NexusDrive
thunar ~/NexusDrive

```
What this gives me when my phone is connected is a window displaying all of my folders on the NexusDrive in my home directory, with all of it's folders displayed, and many of their files, but no image files (other than epub and .pdf) and no music files. 

After rebooting my Linux system, I tried this again, but this time I ran 
```

mtpfs detect

```
before running the other two commands (the ~/NexusDrive had already been created). This time it worked different in that the NexusDrive showed up in my file browser, but no files could be displayed at all before the system timed out! And this closer to what others have recommended as the right way to connect mtpfs!

Can anybody explain such strange behavior from mtpfs, or suggest a different idea for getting a normal connection?

---

### Post by gotnexusbluz on 2013-03-10
:):(:)bump:(:):(

---


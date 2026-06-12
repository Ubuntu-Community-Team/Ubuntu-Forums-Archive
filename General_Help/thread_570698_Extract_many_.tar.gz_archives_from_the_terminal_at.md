---
title: "Extract many .tar.gz archives from the terminal at the same time"
date: 2007-10-08
forum: General Help
---

### Post by Lividity on 2007-10-08
I'm trying to extract all of the themes from the gkrellm skins archive at the same time using the command line. 

Step 1
I got the archive here: [http://www.muhri.net/gkrellm/GKrellM-Skins.tar.gz]("http://www.muhri.net/gkrellm/GKrellM-Skins.tar.gz")

Step 2
I extract the main archive:
tar xvzf GKrellM-Skins.tar.gz

Step 3
Then I enter the newly created directory:
cd GKrellM-skins

Step 4
Now I have 198 .tar.gz archives in this folder:
What command do I need to input here to extract all of the .tar.gz archives at once? or can I not do this? I can extract them individually without issue. How do I do it in batch?

I saw found this thread but mssever's advice didn't work for me. I got an error message.
[http://ubuntuforums.org/showthread.php?t=248354]("http://ubuntuforums.org/showthread.php?t=248354")

---

### Post by nick_h on 2007-10-08
What error message did you get?

---

### Post by Lividity on 2007-10-08
I found the answer myself. I was using the wrong terminology in my search. 

The answer to my question is:

find . -name "*.tar.gz" -exec tar xvfz \{\} \;

I found it here:

[http://ubuntuforums.org/showthread.php?t=295106&highlight=batch+extract+tar.gz]("http://ubuntuforums.org/showthread.php?t=295106&highlight=batch+extract+tar.gz")

---

### Post by Lividity on 2007-10-08
The error said:

tar: Failed open to read on /dev/rst0: Permission denied

---

### Post by nick_h on 2007-10-08
I think /dev/rst0 is a tape device.  Perhaps the loop didn't result in valid archives.

The find method is probably a better method anyway and will handle files at different levels of a directory tree.

---

### Post by Lividity on 2007-10-08
I'm running OpenBSD on the laptop in question 

"man tar" says 

-f archive 
    Filename where the archive is stored. Defaults to /dev/rst0.

I think that's what the error is about. For some reason the commands and combinations of wild cards I was using were giving me that error repeatedly. Thanks for trying to help me out I appreciate it : )

---


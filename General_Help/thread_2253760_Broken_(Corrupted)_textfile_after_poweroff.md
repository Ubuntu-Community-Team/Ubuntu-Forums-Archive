---
title: "Broken (Corrupted) textfile after poweroff"
date: 2014-11-22
forum: General Help
---

### Post by tricx on 2014-11-22
Hello everybody!

I am running an old netbook with a 14.04 LTS live system on a USB flashdrive for browsing, banking and so on. 
I've got an external harddrive (Intenso 1TB) with some good old memories on it (Pictures, Videos, Textfiles). I was loooking and making small changes in a textfile (called A.txt) in AbiWord, when a blackout occured. There is a second file called B.txt which i didnt touch before. I rebooted and mounted the harddrive, but i am not able to access both files via Leafpad, Abiword etc.
Leafpad error: Failed to read from file '/media/lubuntu/Harddrive/A.txt': Input/output error. Abiword just closes itself upon start. All other pictures, videos or textfiles in other folders do work, just A.txt and B.txt do not want to open anymore. I managed to copy them (while getting error messages) on a second harddrive. I can open them, but their size is reduced to 16KiB (both files! coincidence?!) while the original sizes are about 22 and 25KiB (which i can still see on my main HDD). Sadly, the most important informations are cut off.
I guess there is a small corrupt chunk after 16KiB, while other information behind that chunk is still intact? Is even my HDD corrupt?

Is there any way to restore the missing information? Big thanks in advance :)

Best wishes for the weekend,
tric

P.S.: Its not hard to see, that english isnt my native language. I gave my best!

---

### Post by cariboo on 2014-11-22
Start in recovery mode, and select Root from the menu, once at the prompt use the following command:

```
fsck /dev/sdxX
```

where /dev/sdxX = the partition the file is located on.

---


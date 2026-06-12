---
title: "using qbittorrent"
date: 2013-05-09
forum: General Help
---

### Post by Kojak Peg on 2013-05-09
Hi Everyone 
This isn't strictly a buntu question I know, but you guys have been so helpful. I was sure you could help with this one too. I downloaded a distro yesterday, using qbittorrent, and it said it was 100% complete. However when I shut it down it said it was still "sending". I could see the download on my hard drive, so I didn't think much of it. However, today when I downloaded another distro, it said the first one had "stalled". I haven't burnt the first distro to cd yet, so don't know if it works. The second distro seems fine it says it is complete, it's on the hard drive and when I closed qbittorrent down all was well.
 
So, I suppose my question is, how do I know when it has completely finished and whether it has given you a good download 

Many thanks

---

### Post by clive littlewood on 2013-05-09
Hi

When using qbitorent or any other torrent client the download will show "seeding" when finished.

The torrent on your computer is then "seeding" to others downloading.

Any .iso files can be checked using the appropriate checksum provided with the torrent.

If you wish to stop the torrent then right click and select delete, this will remove the torrent but leave the data in your downloads folder.

Hope this helps

Clive

---

### Post by Kojak Peg on 2013-05-09
Thanks Clive Littlewood

I wasn't sure what sending meant, so once you have finished you can leave qbittorrent running on your computer, to help out other users. In order for them to use some of your computing power, is that right

If so how much "sending" is considered polite. 10 minutes in the hour

Thanks

---

### Post by clive littlewood on 2013-05-11
Hi

Just to clarify it's "seeding" not "sending"

Any seeding is deemed polite but if you do have limits on your download/upload quota then it is up to you.

Clive

---

### Post by Kojak Peg on 2013-05-11
Thanks Clive. I must have read it wrong, it can't be a blonde moment as I don't have any hair. So it must be brain fog, lol

---

### Post by thnewguy on 2013-05-11
Some clients call it "sending", some call it "seeding". When mine finishes it simply reports the torrent is "verified".

When it appears as though your distribution image has completed downloading I recommend checking the ISO with an independent tool. Most distros publish checksums (either md5 or sha1). You can open a terminal and run either "md5sum" or "sha1sum" to find out the fingerprint of the file you have downloaded. the string of characters these tools print should match the fingerprint provided by the distribution.

---

### Post by Kojak Peg on 2013-05-16
Thanks thenewguy in the end I did a md5sum and all was well. 

Cheers

---


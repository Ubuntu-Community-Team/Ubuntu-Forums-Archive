---
title: "How Find File Using Specific LBA"
date: 2020-07-27
forum: General Help
---

### Post by jamoody on 2020-07-27
GSmartControl short self test is reporting consistent failure for a specific LBA.  How do I identify the file using that block so I can copy it to a new location and hopefully save the rest of the file (and get self test to complete again).  The file is (likely) a video so if 1 block is corrupted I assume that won't even be noticed.

---

### Post by pbear42 on 2020-07-29
Does the report say there's a file using the LBA?  The main point of the designation is to prevent the block from being used.  See [superuser]("https://superuser.com/a/166526").  Anyhoo, there may be a tool for working backwards from block to file name, but I've not seen it mentioned.  (Been spending the last few days learning more about how the file system works, but not an expert.)  I doubt there's one specifically for working backwards from LBAs, which aren't supposed to be used in the first place.

---


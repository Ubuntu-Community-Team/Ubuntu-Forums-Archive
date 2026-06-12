---
title: "ntfs partition corruption"
date: 2008-02-19
forum: General Help
---

### Post by austinand on 2008-02-19
I would not put this here, but I have two computers which I set up with similar symptoms so it seems too similar to be co-incidence, so I wondered if it was a documented bug or virus.

Each computer is set up to be dual booted XP and Ubuntu (both 7.04 to my memory). I had set up the partitions so that there were three main partitions (I may have put /home on a separate partition but it wasn't used as such so hence doesn't seem relevent), where I have one for the main Ubuntu installation (ext3), one for Windows (ntfs) and one which holds the Data (ntfs). The data drive is accessible in both and is where all documents are stored.

The symptoms are this. Firstly something goes wrong with the Windows partition, and you can only boot into Linux. Then after a week or so the data drive disappears, then a week or so later the Linux main partition disappears and the computer won't boot. It gives error messages about the partition being corrupted, tries to boot into a recovery shell and fails (cannot find Bash, cannot find Apt-get).

This has happened on two separate computers I have set up, sitting 50 miles from each other, one on a university network and one connected to commercial broadband. Thoughts, question?

---


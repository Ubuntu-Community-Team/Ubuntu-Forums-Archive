---
title: "Grip playing CD constantly"
date: 2004-10-12
forum: General Help
---

### Post by Anonymous on 2004-10-12
I installed Grip from the universe repository and it's displaying some strange behavior. Every time it goes to access the CD-ROM drive, it starts playing the CD. So if I insert a disc, it starts playing (even though I have all the auto-playback options I can find disabled). Next, if I select one track with a single click, that track starts playing. If I then stop playback and go to select another track, it starts playing again. Every single access starts the drive playing. Why might that be? The documentation says that it should only start playing with a double click. I thought that maybe the version in the Debian package was compiled with strange options, so I downloaded the source and compiled a version myself -- same effect. It's quite annoying. Now I'm assuming there must be some other program or daemon running somewhere that's taking over whenever Grip tries to access CDDA -- but it doesn't happen for other CD rippers, only Grip. Any ideas?

---


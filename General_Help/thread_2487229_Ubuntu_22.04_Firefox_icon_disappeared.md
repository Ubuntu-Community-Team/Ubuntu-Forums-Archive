---
title: "Ubuntu 22.04 Firefox icon disappeared"
date: 2023-05-27
forum: General Help
---

### Post by gordon33 on 2023-05-27
Hello All

ther HP 15" lap top had a Firefox icon for 5 or more years.  it was there this afternoon but is gone now.  

I can find the Firefox apt in the ubuntu software folder but I do not know how to get the icon on my search bar so I can use it.

If I use the terminal and type "firefox"  The icon appears and the yahoo page shows up.  close the terminal and both go away.

---

### Post by QIII on 2023-05-27
Since Firefox is now a snap, it should have been the Firefox snap packager's responsibility to make the icon available.  Apparently they did not.

What I did was download a firefox .png (256x256), which I saved in ~/snap/firefox/common.  I then changed the properties for the launcher image to point to that file.  I put it in /common so that if the snap updates to a new version, the .png will remain where it is expected.

---


---
title: "Unable to open Portable Hard Drive"
date: 2020-04-09
forum: General Help
---

### Post by stefankovac2266 on 2020-04-09
Hi. I was using an older type of Ubuntu where I was able to open my Portable Hard Drive.
After that I installed the latest version of Ubuntu and since then I am unable to open the Portable Hard Drive.
When I put into the Notebook the P. Hard Drive and open the folder called "Files", then it shows that it is there but when I click on it to open or "Mount" then nothing and absolutely nothing happens.
There is no problem with the P. Hard Drive since it works in my other computer under Windows 10. Also other USB drives work in this Notebook under Ubuntu.
Do you have any idea how to solve this problem?

---

### Post by cmcanulty on 2020-04-09
This sometimes works. Attach it to a windows machine and then safely remove it. Then try it again on Ubuntu. Good luck.

---

### Post by yancek on 2020-04-09
If this drive works on windows then it must contain a windows filesystem.  Since you are using windows 10 which defaults to having hibernation on, in addition to the suggestion above you might verify that hibernation is off. Also, some windows updates will turn hibernation back on so if it has been turned off, you need to verify it again after a windows update.

---

### Post by stefankovac2266 on 2020-04-13
Thank you very much. This worked.

---


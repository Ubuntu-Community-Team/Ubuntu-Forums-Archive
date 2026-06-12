---
title: "3D Acceleration - How to enable for ATI"
date: 2006-10-25
forum: General Help
---

### Post by jimhaddon on 2006-10-25
I have searched and searched on google and not been able to find the answer. How do you do that in Gnome?

---

### Post by Architeuthis on 2006-10-25
It depends on wat card you have: for ati you can use this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
for nvidia: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If you are an opensource fundamentalist you can try this out:[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I dont know the opensource driver for nvidia. You dont have 3d accel standard because you need the closed source drivers mentioned above (or the opensource drivers, but they are slower then the closed source, if you have a new card your best option is the closed source driver; if you have a card like the ati radeon 7000 you should use the opensource radeon driver) to do that. They are not installed standard because they are closed and that is against the policy of ubuntu.

---


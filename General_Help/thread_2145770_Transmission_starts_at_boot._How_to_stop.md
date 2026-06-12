---
title: "Transmission starts at boot. How to stop?"
date: 2013-05-16
forum: General Help
---

### Post by jahwire on 2013-05-16
I am running Xubuntu 12.04 on an old laptop. It works great! Just a little issue with p2p Transmission. I removed Transmission, reinstalled it. Deleted the user/.config/transmission folder and it recreated one the first time I run it. But it still loads at startup. I do not have it defined in the Settings/Sessions-Auto Startup and I don't see anything anywhere that makes it starts automatically when I boot. All folders in the user/.config/transmission folder are empty. 

Any idea on how to stop this. I just want to run it when I want, not  when I start the computer. I appreciate any feedback.

---

### Post by ajgreeny on 2013-05-16
1. Make sure that when you logout/shutdown the tick box for "Save sessions for future logins" is not selected.
2. In Session and Startup in your system settings click on "Clear saved sessions" in the Session tab.
3. Now reboot and hopefully all will be OK.

---

### Post by jahwire on 2013-05-17
>>  In Session and Startup in your system settings click on "Clear saved sessions" in the Session tab.

That did it. Thanks!!

---

### Post by Bucky Ball on 2013-05-17
To help others I have taken the liberty of marking this thread as solved. For future reference: Edit first post>click Go Advanced>Change the prefix [ubuntu] in the title to [SOLVED]. Done. ;)

---


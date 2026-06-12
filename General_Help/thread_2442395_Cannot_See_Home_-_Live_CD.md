---
title: "Cannot See /Home - Live CD"
date: 2020-05-03
forum: General Help
---

### Post by Quarkrad on 2020-05-03
Running 20.04   Boot to live CD to access **/home**.  At livecd Desktop I click ubuntu 20.04 in the left hand pane (to mount) and get a list of directories in the right hand pane (see 1.jpg).  I know this is right because I looked in **/usr/bin/** and recognised some files I had created.  When I click on *home* I was expecting to see a folder called *dad*, my username,  but as you can see the folder is empty(2.jpg).  I even switched on *Show Hidden Files.*.  Booting back to my main system my umask value for /home is  dad@dadubuntu:~$0002. Any advice appreciate as I cannot see the wood for the trees any more.

---

### Post by tea for one on 2020-05-03
If you are using Ubuntu 20.04 in a **live** session, the location of your **installed** home directory is:-

+Other Locations (usually last entry in the sidebar)

Your screenshot shows **Browse Network**, try that one.

---

### Post by Impavidus on 2020-05-03
Have you got a separate /home partition?

I see a partition called "ubuntu 20.04" (which is your root partition) and one called "ubntu home" [sic]. Try that one. If you use a separate /home partition, the home directory in the root partition is empty and the /home partition will get mounted there when you boot the installed system, but not when you run a live session.

---

### Post by Quarkrad on 2020-05-03
Doh .....  yes I do have a separate /home partition and yes, I was looking in the wrong place!  Apologies, and thanks for leading me out of the woods!

---


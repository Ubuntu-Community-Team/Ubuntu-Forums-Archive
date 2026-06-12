---
title: "Why is Ubuntu freezing up?"
date: 2006-10-16
forum: General Help
---

### Post by driggins on 2006-10-16
Greetings,

I am working on an uncomplicated installation:
-machine is an IBM 8311-XX7
-Ubuntu Server Dapper
-Freshly installed as of yesterday
-After installation, I installed ubuntu-desktop (I'm a newbie, forgive me for needing a GUI)
-After starting GUI, I allowed the automatic updates, which included an update to the kernel
-I installed Samba, configured a shared directory for my Windows workgroup colleagues. Share works/worked fine.
-Computer was running great and Ubuntu was zippy last night.

I came back to my computer this morning, having left it in a good state last night (and leaving it running). After waking the monitor from sleep mode, Ubuntu was verrrrrrrrrrrry slow. I could bring up a terminal window using my keyboard shortcut. It took a long time to appear, but finally did. Keyboard character took forever to appear in the terminal. I gave up and left the office. Now, 8 hours later, I have a mouse cursor and a black screen.

Any thoughts?

Thanks,
daryl

---

### Post by aysiu on 2006-10-16
Sounds as if it's a graphics card issue.

Do you have the proper drivers installed (Nvidia/ATI)?

You may want to check out [these suggestions](http://ubuntuforums.org/showpost.php?p=129379&postcount=21).

---

### Post by driggins on 2006-10-17
Since I have not installed a specific driver (I allowed Ubunto to auto-configure the video device), then I would assume I am using the generic nvidia driver.

My card is a Nvidia MX-440SE. My computer also has an integrated card (Intel 845G). Incidentally, I could not successfully configure the integrated card. I did not have a GUI until I installed the Nvidia card (was auto-configured and worked without my help).

I found this [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"). Would you suggest that I follow through on installation of the Nvidia driver? You may be able to sense my hesitation...the directions are long (but thankfully well written).

Thanks,
daryl

---

### Post by aysiu on 2006-10-17
Nvidia drivers are proprietary, so they don't come with a default Ubuntu installation. You would have to install them yourself, yes.

---


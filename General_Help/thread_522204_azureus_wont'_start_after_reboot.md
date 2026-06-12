---
title: "azureus wont' start after reboot"
date: 2007-08-10
forum: General Help
---

### Post by girard on 2007-08-10
i was playing around with command in linux to refresh the desktop and panels (killall). so i killedall but i did it while gyache and azureus was running. naturally, they didn't go back in the system tray where they should be. i restarted by system, and when i run azureus, it loads up everything, but it won't stay running. 

here's the error i get from running it in the terminal

> 
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=6648, tid=3084740288
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6648.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


what do i do?

---

### Post by girard on 2007-08-10
got it back!

i removed sun-java5-bin from synaptic

typed this

```

sudo update-alternatives --config-java

```

i brought it back to the gij thing

reinstalled sun-java5-bin, and then ran the update-alternatives again to set it to java option.

whew!

---


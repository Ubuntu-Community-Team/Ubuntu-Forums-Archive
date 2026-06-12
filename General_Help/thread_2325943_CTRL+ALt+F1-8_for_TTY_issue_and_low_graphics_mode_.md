---
title: "CTRL+ALt+F*1-8 for TTY issue and low graphics mode due low disc space"
date: 2016-05-26
forum: General Help
---

### Post by Kotseto on 2016-05-26
Hi all.
In reference to these threads 
[http://ubuntuforums.org/showthread.php?t=1624602](http://ubuntuforums.org/showthread.php?t=1624602)
[http://ubuntuforums.org/showthread.php?t=1566580&page=2](http://ubuntuforums.org/showthread.php?t=1566580&page=2)
[http://ubuntuforums.org/showthread.php?t=1712424](http://ubuntuforums.org/showthread.php?t=1712424)
[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error?page=2&tab=votes&newreg=99e51805107843c18ca3dcff7b22bc7e](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error?page=2&tab=votes&newreg=99e51805107843c18ca3dcff7b22bc7e)
I have the following issue:
 I am running a live usb with persistance and got low disc space leading to low graphics mode in reference to this thread [How to fix "The system is running in low-graphics mode" error?]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error")

  When i try to get to a tty with ctrl alt f1 or ctrl alt f1 to f8
  In order to execute autoclean cmd
  i get
  Ignoring BGRT invalid status 0 (expected 1) No caching mode page found Assuming drive cache: write through Permission denied Error @wl_inform single bss frame error
  Anyone knowing how to get to a terminal so i can free up some space?

By disabling Wifi I managed slightly to get rid of Error @wl_inform single bss frame error but I still cannot get to a terminal It shows error msg [s33.postimg.org/h8ij4f2en/20160526_015953.jpg]("http://s33.postimg.org/h8ij4f2en/20160526_015953.jpg") I followed [youtube.com/watch?v=o31QGpjR8KE]("https://www.youtube.com/watch?v=o31QGpjR8KE") and it turns out it is NOT a graphics error which is insane per the error message. It is a LOW disc space. 


I gather the keyboard layout on the live usb may have been set as wrongly as a default and that is why the combo ctr+alt+f*1-8 is not showing a terminal. I see some suggestions FN could be used to trigger F keys [ubuntuforums.org/showthread.php?t=1712424]("http://ubuntuforums.org/showthread.php?t=1712424") but not in my case. Any suggestions on how to open a tty to Clean up disk space and start my session???

---


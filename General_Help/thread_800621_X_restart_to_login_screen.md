---
title: "X restart to login screen"
date: 2008-05-20
forum: General Help
---

### Post by Suky on 2008-05-20
Hi,

Anyone can help to solve this problem? I notice that when I visit website with heavy flash, my X was restart to login screen. 

I'm using Hardy 64bit & Firefox 3 beta 5 and ATI X1250.

Here is deamon.log
```
May 20 11:53:00 subuntu gdm[5437]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May 20 11:53:20 subuntu hcid[5350]: Default passkey agent (:1.52, /org/bluez/passkey) registered
May 20 11:53:20 subuntu hcid[5350]: Default authorization agent (:1.52, /org/bluez/auth) registered
May 20 11:53:22 subuntu NetworkManager: <info>  Updating allowed wireless network lists. 
```

Here is syslog
```
May 20 11:53:00 subuntu gdm[5437]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 20 11:53:03 subuntu kernel: [ 2523.971978] [fglrx] PCIe has already been initialized. Reinitializing ...
May 20 11:53:03 subuntu kernel: [ 2523.980818] [fglrx] GART Table is not in FRAME_BUFFER range 
May 20 11:53:03 subuntu kernel: [ 2523.980831] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
May 20 11:53:03 subuntu kernel: [ 2523.980834] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
May 20 11:53:07 subuntu gdmgreeter[8539]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
May 20 11:53:17 subuntu pulseaudio[8618]: pid.c: Stale PID file, overwriting.
May 20 11:53:20 subuntu hcid[5350]: Default passkey agent (:1.52, /org/bluez/passkey) registered
May 20 11:53:20 subuntu hcid[5350]: Default authorization agent (:1.52, /org/bluez/auth) registered
May 20 11:53:22 subuntu kernel: [ 2538.236041] CPU0 attaching NULL sched-domain.
May 20 11:53:22 subuntu kernel: [ 2538.249286] CPU0 attaching sched-domain:
May 20 11:53:22 subuntu kernel: [ 2538.249294]  domain 0: span 01
May 20 11:53:22 subuntu kernel: [ 2538.249296]   groups: 01
May 20 11:53:22 subuntu NetworkManager: <info>  Updating allowed wireless network lists. 
```

Here is message
```
May 20 11:53:03 subuntu kernel: [ 2523.971978] [fglrx] PCIe has already been initialized. Reinitializing ...
May 20 11:53:03 subuntu kernel: [ 2523.980818] [fglrx] GART Table is not in FRAME_BUFFER range 
May 20 11:53:03 subuntu kernel: [ 2523.980831] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
May 20 11:53:03 subuntu kernel: [ 2523.980834] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
May 20 11:53:17 subuntu pulseaudio[8618]: pid.c: Stale PID file, overwriting.
```

Here is kern.log
```
May 20 11:53:03 subuntu kernel: [ 2523.971978] [fglrx] PCIe has already been initialized. Reinitializing ...
May 20 11:53:03 subuntu kernel: [ 2523.980818] [fglrx] GART Table is not in FRAME_BUFFER range 
May 20 11:53:03 subuntu kernel: [ 2523.980831] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
May 20 11:53:03 subuntu kernel: [ 2523.980834] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
May 20 11:53:22 subuntu kernel: [ 2538.236041] CPU0 attaching NULL sched-domain.
May 20 11:53:22 subuntu kernel: [ 2538.249286] CPU0 attaching sched-domain:
May 20 11:53:22 subuntu kernel: [ 2538.249294]  domain 0: span 01
May 20 11:53:22 subuntu kernel: [ 2538.249296]   groups: 01
```


Thanks in advance

---

### Post by _godbout_ on 2008-05-20
Same problem here.

---

### Post by EXCiD3 on 2008-05-20
I havent had too much trouble with flash as of a recent update on Hardy, my flash used to crash about 3 seconds into a video but a package update fixed everything. Can you give an example of a site that would crash the xserver? It is also possible that because you are using 64 that is why I have not experienced this issue. 64 bit still hasn't gotten the stability or the support of developers that it needs. All in good time though.

---

### Post by _sAm_ on 2008-05-20
This thread is about a bug in Firefox that reastart X:
[http://ubuntuforums.org/showthread.php?t=797744](http://ubuntuforums.org/showthread.php?t=797744)

Could it bee the same bug?

---


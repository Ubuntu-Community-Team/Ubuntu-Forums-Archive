---
title: "Email links won't open Firefox tabs after initial call"
date: 2024-09-04
forum: General Help
---

### Post by von Stalhein on 2024-09-04
Using Ubuntu 24.04.1 LTS.   Thunderbird 128.1.0esr & Firefox 130.0, Ubuntu GNOME desktop


     Email links will open Firefox if it's not already running, but if  it's already open the icon in the dock jiggles as a notification & a message that Firefox is ready appears, but no  automatic switching to the new Firefox tab occurs.   

As far as I can see, the correct handlers are identified in the Thunderbird account settings - any suggestions how to troubleshoot the issue please?

---

### Post by sloancli on 2024-09-08
Try **Menu** > **Help** > **Troubleshoot** **Mode...** > **Restart** > **Open**, then try opening link from Thunderbird again. This will help narrow down the issue to make sure it is not some crazy plugin interfering with Firefox. Probably be good to check the same on Thunderbird if you have plugins over there.

If still no go, try launch Firefox from terminal with ```
xdg-open "http://google.com"
```

If a different browser opens, you will need to manually set Firefox as the default browser: ```
 xdg-settings set default-web-browser firefox.desktop 
```

Give it a try and let me know.

---

### Post by von Stalhein on 2024-09-09
Thanks heaps for the reply!

1. No change in troubleshooting mode with extensions unloaded etc.
2. Checked again that Firefox is set as default but ran that cmd as well.
3. "Interesting output in Terminal from  ```
xdg-open 
```command.

```
xxx@xxx:~$ xdg-open "http://google.com"
xxx@xxx:~$ Gtk-Message: 15:55:54.903: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
[12228, Main Thread] WARNING: Theme parsing error: gtk.css:1:21: Failed to import: Error opening file /home/xxx/snap/firefox/4848/.config/gtk-3.0/colors.css: No such file or directory: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox:12228): Gtk-WARNING **: 15:55:54.965: Theme parsing error: gtk.css:1:21: Failed to import: Error opening file /home/xxx/snap/firefox/4848/.config/gtk-3.0/colors.css: No such file or directory
```

So trying to decipher that, perhaps completely removing Firefox & then re-installing might sort out what might be some missing dependencies?

---


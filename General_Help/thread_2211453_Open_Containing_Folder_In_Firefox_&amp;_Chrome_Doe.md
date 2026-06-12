---
title: "Open Containing Folder In Firefox &amp; Chrome Doesn't Highlight The File In Nautilus"
date: 2014-03-16
forum: General Help
---

### Post by gowtham-pro on 2014-03-16
Hello all,

I won't say I am new to Ubuntu, but I have been on and off for several years -- although I find myself on Ubuntu more than on Windows nowadays I still consider myself a newbie. I am currently using 13.10 and I also remember having this issue in 12.04 LS, as well.

After I download anything in Chrome or Firefox. There is this option in the downloads page of the browser (Ctrl+J) to open the file location. It is "Open containing folder" in Firefox and "Show in folder" in Google Chrome. When I click it these links in the downloads page of the browser, the "Downloads" folder opens as expected, but it still doesn't highlight the file in the directory. This becomes extremely painful to find the file especially if you have a ton of files in your Downloads folder. Of course I can switch to list view and sort the items by date and find the file. However, don't you guys think it should actually highlight the file when Nautilus opens? 

It was already posted by some other user a month ago and I think the issue was not addressed properly. [http://ubuntuforums.org/showthread.php?t=2205007&highlight=Open+Folder+Firefox](http://ubuntuforums.org/showthread.php?t=2205007&highlight=Open+Folder+Firefox)

Is it a bug or is this normal and something I have to deal with? I'm assuming it's a bug since the feature sounds pretty basic and its there on Windows and OS X.

---

### Post by dniMretsaM on 2014-03-16
As far as I know, it doesn't normally do this. I suppose it could be a setting buried in about:config somewhere, but I'm pretty sure your description is the default.

---

### Post by element13 on 2014-03-18
I don't think there is a solution to this... but you should be able to just type the first few letters of the file and it should highlight it.  Not ideal, I know, but it works.

---

### Post by mc4man on 2014-03-18
It does so now  in 14.04, at least from Firefox.
The only potential issue is a longstanding gtk bug where the nautilus window may open without focus & maybe even under the  FF downloads (Library) window.
If the downloads window auto closed this wouldn't happen, otherwise there is a small gtk patch that resolves this  but will never be used.

---

### Post by elijah-lynn on 2014-08-10
> **mc4man said:**
> It does so now  in 14.04, at least from Firefox.
The only potential issue is a longstanding gtk bug where the nautilus window may open without focus & maybe even under the  FF downloads (Library) window.
If the downloads window auto closed this wouldn't happen, otherwise there is a small gtk patch that resolves this  but will never be used.

Oh wow, it sure does highlight in Firefox but Chrome still doesn't! So -1 for Chrome, +1 for Firefox!

---

### Post by elijah-lynn on 2014-08-10
> **mc4man said:**
> It does so now  in 14.04, at least from Firefox.
The only potential issue is a longstanding gtk bug where the nautilus window may open without focus & maybe even under the  FF downloads (Library) window.
If the downloads window auto closed this wouldn't happen, otherwise there is a small gtk patch that resolves this  but will never be used.

Could you post a link to the GTK patch you mentioned? I can't find it on the Googles.

Thanks

---

### Post by mc4man on 2014-08-10
> **elijah-lynn said:**
> Could you post a link to the GTK patch you mentioned? I can't find it on the Googles.

Thanks
With recent updates in 14.04 I don't have any focus issues anymore in Firefox so haven't used of late.  (may be some other rare ones but haven't noticed.
this is the patch, line adjusted for current gtk-3-0 source in 14.04 (gtk+3.0_3.10.8-0ubuntu1.2

```
--- gtk+3.0-3.10.8.orig/gdk/x11/gdkwindow-x11.c
+++ gtk+3.0-3.10.8/gdk/x11/gdkwindow-x11.c
@@ -949,8 +949,6 @@ setup_toplevel_window (GdkWindow *window
 
   if (!window->focus_on_map)
     gdk_x11_window_set_user_time (window, 0);
-  else if (GDK_X11_DISPLAY (x11_screen->display)->user_time != 0)
-    gdk_x11_window_set_user_time (window, GDK_X11_DISPLAY (x11_screen->display)->user_time);
 
   ensure_sync_counter (window);


```

---


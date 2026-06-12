---
title: "firefox3 crashes very frequently in hardy"
date: 2008-07-01
forum: General Help
---

### Post by dexter.deepak on 2008-07-01
i never applied any new changes in ff3, but i dont know why it's crashing so many times !
whenever i open a new window, it remains open for maximum about 15 seconds.
i had previously faced crashes, but only once/twice, so i never cared...but now its geting too much, i cant use it at all.

---

### Post by pedro_orange on 2008-07-01
Is this only a problem with FF?

Have you tried re-installing it? 
(Via Synaptic or dpkg - whatever your poison is)

Have you tried an alternative browser such as Opera? Do you have the same problems there? 

:)

---

### Post by prshah on 2008-07-01
> **dexter.deepak said:**
> i never applied any new changes in ff3, but i dont know why it's crashing so many times !
whenever i open a new window, it remains open for maximum about 15 seconds.
i had previously faced crashes, but only once/twice, so i never cared...but now its geting too much, i cant use it at all.

Open a terminal, then run firefox from there with the command```
firefox
```; now keep doing something until it crashes. Your terminal should be filled with messages; post those here for a clue.

Most likely flash/java related, I'd guess..

---

### Post by dexter.deepak on 2008-07-01
i reinstalled it and it was stable for a longer time (about 1 hour), then again it started crashing.

i have tried the Epiphany browser, and it has no such problems.
i will now try running it from terminal and then report back.

---

### Post by dexter.deepak on 2008-07-02
i tried running ff through terminal and am getting this error repeatedly:
```
dpak@dpak-server:~$ firefox

** (firefox:9313): WARNING **: Invalid borders specified for theme pixmap:
        /home/dpak/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

```

---

### Post by prshah on 2008-07-02
> **dexter.deepak said:**
> 
** (firefox:9313): WARNING **: Invalid borders specified for theme pixmap:
        /home/dpak/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
[/CODE]

1) Are you using FlashGot as an extention in Firefox? If so, you should try disabling the "automatic download manager detection" in flashgot settings.

2) Looks like you are using the Mac4Lin theme, but firefox doesn't like a particular setting in it. Either change the theme or rename the /home/dpak/.themes/Mac4Lin_GTK_Aqua_v0.3 directory to disable the theme, then check if firefox is more stable.

3) Try renaming the ~/.mozilla directory and starting firefox from the  terminal. 

4) Does it happen with other user accounts?

---

### Post by kliklik on 2008-07-02
I have the exact same problem and it's not only firefox.. Check the description here. [http://ubuntuforums.org/showpost.php?p=5303849&postcount=23](http://ubuntuforums.org/showpost.php?p=5303849&postcount=23)

---

### Post by dexter.deepak on 2008-07-03
i tried all the recommendations and here's the o/p:
```
dpak@dpak-server:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

```

recently, whenever i click the send button from my mailbox, ff crashes.
even epiphany behaves strange :
[CODEdpak@dpak-server:~$ epiphany
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(epiphany-browser:7934): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(epiphany-browser:7934): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(epiphany-browser:7934): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
cairo context error: NULL pointer
cairo context error: NULL pointer

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(epiphany-browser:7934): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


][/CODE]

what else could be tried ?

---

### Post by dodle on 2008-07-03
I'm not sure, but I think this can be caused by fonts that you have installed/tried to install on your system.  

I removed the fonts that I manually installed, then deleted the ~/.fonts folder and firefox has been working fine since.

Hope this helps.

---

### Post by prshah on 2008-07-04
> **dexter.deepak said:**
> i tried all the recommendations and here's the o/p:
```
dpak@dpak-server:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

```



Are you using Google Desktop? There's a known problem with it; no solution though except to disable indexing: see [http://groups.google.com/group/Google-Desktop-Linux-Something-Broken/browse_thread/thread/1beea8d1c02c66b4](http://groups.google.com/group/Google-Desktop-Linux-Something-Broken/browse_thread/thread/1beea8d1c02c66b4) , specifically the post by pegardan.

---

### Post by mzhb@mac.com on 2008-07-04
I heard a rumor says that firefox crashes sometimes because of flash file from the web page.
Not sure whether this is the case...

---


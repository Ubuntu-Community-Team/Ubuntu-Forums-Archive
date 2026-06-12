---
title: "Thunderbird &quot;open all&quot; attachments launches multiple instantiations of app"
date: 2023-08-28
forum: General Help
---

### Post by Ralph L on 2023-08-28
I have Xubuntu 22.04LTS with latest Thunderbird 102.13.0 (64-bit) for that OS version. I recently upgraded my image viewer, Geeqie, to the latest version 2.1 using an appimage installation. I did the upgrade in order to handle .webp files, which some people have been sending me. Using Thunar>Properties I set the default app for opening .jpeg and .webp files to Geeqie-v2.1-x86_64.AppImage (default). Everything works except now, when I select "OpenAll" at the bottom right of the message pane, Tbird opens an instantiation of geeqie 2.1 for each attached file. In other words I get x instantiations of geeqie for x attached files. However, each instantiation will display all the attached image files. Before the geeqie upgrade, Tbird opened only 1 instantiation to display all the image files. To determine if the problem was in geeqie, I went back to the old geeqie 1.7.2 and tried Open All. Again Tbird opened a geeqie instantiation for each attached file. So the problem does not appear to be in geeqie. Apparently I did something to Tbird during the upgrade, but I don't know what and I can't find a way to fix it.

Does anybody else have this problem??? Does anybody know how to fix it?? I have googled all around and have found nothing describing this problem.

Any help appreciated..........

---

### Post by ajgreeny on 2023-08-29
The bottom right option in my TB message pane is not "Open" but "Save" attachments.

Have you changed anything in the Advanced configuration of thunderbird?

---

### Post by Ralph L on 2023-08-29
Thanks for the response. I appreciate it. No, to my knowledge I haven't changed anything in Advanced configuration. On my Tbird there is a "down" symbol to the right of the "Save". If you click on that it shows a menu with on choice being "Open All". That is what I am using to open all the photos and other things that people send me.

---

### Post by #&amp;thj^% on 2023-08-29
> **Ralph L said:**
> 
Does anybody else have this problem??? Does anybody know how to fix it?? I have googled all around and have found nothing describing this problem.

Any help appreciated..........
I'm not seeing that on a Flatpak install.
```
Geeqie           org.geeqie.Geeqie         v2.1       stable 
```
Maybe try running TB in the terminal then open a single image attachment, it might tell us something.
EDIT: Ralph there is a setting in TB, "Settings, Composition" off to right try to un-tick the "Check for missing attachments".

---

### Post by ajgreeny on 2023-08-29
On my TB I see the **Save** button bottom right of the message pane and at bottom left there is an expandable list of file attachment names.  If I right click on that list I also get the **Save all** or **Open all** option as well as Detach and Delete options.

See my image attached to show you my layout and what I see on my TBird

---

### Post by Ralph L on 2023-09-01
I haven't been able to fix my problem of having Tbird bring up a new instantiation of geeqie-appimage for each image, when i do an Open All on the attached .jpg files. In fact it has gotten worse. Before I installed geeqie-appimage, I had geeqie 1.7.2 installed as an ordinary app. At that time only one copy of geeqie 1.7.2 came up for all attached .jpg files. Now Tbird brings up multiple instance of geeqie 1.7.2 and I can't make it perform like it used to. I ran Tbird under Terminal and I get some errors that I don't understand. Here is the output of Terminal when I did a "Open All" on a Tbird message with 2 jpg attachments. Note that the Canon errors have something to do with pictures taken with a Canon cameral. They don't appear when non-Canon pictures are opened.```
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
Address already in use: /home/ralph/.config/geeqie/.command
(AppRun.wrapped:65558): GLib-GIO-CRITICAL **: 09:16:19.298: g_data_input_stream_new: assertion 'G_IS_INPUT_STREAM (base_stream)' failed
(AppRun.wrapped:65558): GLib-GIO-CRITICAL **: 09:16:19.299: g_data_input_stream_read_line_async: assertion 'G_IS_DATA_INPUT_STREAM (stream)' failed
(AppRun.wrapped:65576): GLib-GIO-CRITICAL **: 09:16:19.327: g_data_input_stream_new: assertion 'G_IS_INPUT_STREAM (base_stream)' failed
(AppRun.wrapped:65576): GLib-GIO-CRITICAL **: 09:16:19.327: g_data_input_stream_read_line_async: assertion 'G_IS_DATA_INPUT_STREAM (stream)' failed

```

Here is the Terminal output, when I did Open All on just one attachment. ```
ATTENTION: default value of option mesa_glthread overridden by environment.
Error: Directory Canon with 7680 entries considered invalid; not read.
Error: Directory Canon with 7680 entries considered invalid; not read.
(AppRun.wrapped:66891): GLib-GIO-CRITICAL **: 09:55:16.918: g_data_input_stream_new: assertion 'G_IS_INPUT_STREAM (base_stream)' failed
(AppRun.wrapped:66891): GLib-GIO-CRITICAL **: 09:55:16.918: g_data_input_stream_read_line_async: assertion 'G_IS_DATA_INPUT_STREAM (stream)' failed

```
I looked at all the Config Editor settings that came up when I searched for "attachment" and "open", but none seemed to apply to my problem. I also switched in Setting>Files and Attachments the jpeg app to use, from geeqie-appimage to risretto, and it ALSO opened a risretto instance for each image file. However, when I switched to qpdfview, I got only 1 instantiation of qpdfview. It opened the jpg files fine.
Anybody got an explanation of any of this behavior?????????

---

### Post by #&amp;thj^% on 2023-09-01
This would qualify as a Bug that needs a fix, I'm just not sure where i would file it against and I still have no problems with the Flatpak geeqie, so I'm no help there.
Out of curiosity what is the command used in thunar pref's with "geeqie"

---

### Post by Ralph L on 2023-09-01
1fallen: I always set the Thunar "Open With" to geeqie-appimage  for version 2.1 and to 'geeqie' for the old 1.7.2 version that was installed as a normal app. I used this to set Tbird's File and Attachments.

---

### Post by #&amp;thj^% on 2023-09-01
> **Ralph L said:**
> 1fallen: I always set the Thunar "Open With" to geeqie-appimage  for version 2.1 and to 'geeqie' for the old 1.7.2 version that was installed as a normal app. I used this to set Tbird's File and Attachments.

Thank You, well i have a theory " qpdfview" is set default for images .jpg .jpeg yada yada is set to single page mode.
some referance 
```
enum class 	PageMode { SinglePage, MultiPage }
enum class 	ZoomMode { Custom, FitToWidth, FitInView }
```
You just have a wonky setting or Bug for the imageviews you mention open each and all at once??? I'm stumped.

---

### Post by Ralph L on 2023-09-02
!fallen,
I guess I am not computer savvy enough to understand your last post. I vaguely know what enum is, but I don't know what you are telling me to do with it, and when I type "enum" into Terminal, it says I don't have it installed. Are you telling me to just type those enum commands into Terminal? Don't I have to specify somehow what app I am doing the enumeration for, or enter it as part of bash script?

---

### Post by #&amp;thj^% on 2023-09-02
> **Ralph L said:**
> !fallen,
I guess I am not computer savvy enough to understand your last post. I vaguely know what enum is, but I don't know what you are telling me to do with it, and when I type "enum" into Terminal, it says I don't have it installed. Are you telling me to just type those enum commands into Terminal? Don't I have to specify somehow what app I am doing the enumeration for, or enter it as part of bash script?
Ralph L, I'm sorry it sounded confusing, all I'm saying is that I would expect qpdfview not to open all images at once, it's main function is a PDF reader, and only opening a page at time is what it dose for images.
So I was hoping to help with the difference with your question is all:
> Anybody got an explanation of any of this behavior????????? 

This is just an odd duck of a problem, and i just don't know how to suggest anything to help you with this one.

---


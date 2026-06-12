---
title: "Editing File Browser Settings"
date: 2019-10-27
forum: General Help
---

### Post by ravrak on 2019-10-27
I'm trying to turn off/remove the "Recent" and "Starred" options on the left side bar of the file browser.  I right click and remove is there, but it's grayed out and I can't select it.  Also, I'd like to show extra drives in that list instead of having the "Other Locations" option in the sidebar.  Is there any way to do these things?  I'm coming from Windows 10/Linux Mint, and both of those OSes allow this function.  

Any help is greatly appreciated.  :)

---

### Post by #&amp;thj^% on 2019-10-27
Too many choice's to guess from, include this also:
```
echo $DESKTOP_SESSION

```

---

### Post by ravrak on 2019-10-27
> **1fallen said:**
> Too many choice's to guess from, include this also:
```
echo $DESKTOP_SESSION

```

That code returns "ubuntu" in the terminal.  I'm running Ubuntu 19.10, just installed it, basic/default settings/DE/etc.

---

### Post by #&amp;thj^% on 2019-10-27
You Picked the hardest to play/tweak with:p I just won't use Nautilus period.

Unfortunately the auto-detection of whether to show the 'Starred' panel based on whether you have any starred items was decided against. I don't know why it is shown even without Tracker being available, though.

**Note: that the sidebar is actually a single unit provided by Gtk,** not an editable collection of random items &#8211; but still sufficiently customizable for this purpose.
Please be aware I won't be held responsible for breakage as a result of following the below. (It worked a year or two ago)
**Option 1**: Override the built-in UI description.[list]

    [*]Create a location for the overrides:
```

    mkdir ~/.config/nautilus/ui
```

    [*]Extract the resource description of the main window:
```

    gresource extract /bin/nautilus \
              /org/gnome/nautilus/ui/nautilus-window.ui \
              > ~/.config/nautilus/ui/nautilus-window.ui
```

    [*]Edit the properties of the GtkPlacesSidebar object:
```

    <object class="GtkPlacesSidebar" id="places_sidebar">
      ...
      <property name="show-recent">False</property>
      <property name="show-starred-location">False</property>
      ...
    </object>
```

    [*]Set the environment variable to make GLib use this override:
```

    export G_RESOURCE_OVERLAYS="/org/gnome/nautilus/ui=$HOME/.config/nautilus/ui"
```

    [*]Due to Nautilus being started via D-Bus, you will likely need to set this via ~/.pam_environment&#8230;
```

    G_RESOURCE_OVERLAYS DEFAULT="/org/gnome/nautilus/ui=/home/<yourusername>/.config/nautilus/ui"

    &#8230;or via ~/.config/systemd/user/dbus.service.d/environment.conf:

    [Service]
    Environment="G_RESOURCE_OVERLAYS=/org/gnome/nautilus/ui=/home/<yourusername>/.config/nautilus/ui"
```[/list]
**NOTE: **You will need to change the code I just showed from "_<yourusername>_" to your _real user name_.
**Option 2:** Recompile Nautilus with this patch applied:
```

diff --git a/src/nautilus-window.c b/src/nautilus-window.c
index 0d1234f15..7a6d567f6 100644
--- a/src/nautilus-window.c
+++ b/src/nautilus-window.c
@@ -1347,6 +1347,12 @@ nautilus_window_set_up_sidebar (NautilusWindow *window)
                                         | GTK_PLACES_OPEN_NEW_TAB
                                         | GTK_PLACES_OPEN_NEW_WINDOW));

+    gtk_places_sidebar_set_show_recent (GTK_PLACES_SIDEBAR (window->places_sidebar),
+                                        FALSE);
+
+    gtk_places_sidebar_set_show_starred_location (GTK_PLACES_SIDEBAR (window->places_sidebar),
+                                                  FALSE);
+
     g_signal_connect_swapped (window->places_sidebar, "open-location",
                               G_CALLBACK (open_location_cb), window);
     g_signal_connect (window->places_sidebar, "show-error-message",


```
Easy Peasy, LOL

---

### Post by ravrak on 2019-10-27
Jesus lol.  That seems like a lot to remove an option from the bookmark menu.  

Is there another file manager I can use that works?  I'm not tech savvy enough to recompile things lol.

---

### Post by #&amp;thj^% on 2019-10-27
> **ravrak said:**
> Jesus lol.  That seems like a lot to remove an option from the bookmark menu.  

:lolflag: Now you know why I don't use Nautilus. ;)
A handful of us use Nemo.
**[COLOR="#FF0000"]**WARNING**[/COLOR]**Unless you have a strong disliking of Nautilus/Files, you should not try to experiment like this with the default file manager. Changing an integral component may lead to conflicts and broken systems. If you are an advanced user who knows what&#8217;s he/she is doing, you may follow the rest of the tutorial.  [https://itsfoss.com/install-nemo-file-manager-ubuntu/](https://itsfoss.com/install-nemo-file-manager-ubuntu/)
Good Luck. :D

---

### Post by ravrak on 2019-10-27
> **1fallen said:**
> :lolflag: Now you know why I don't use Nautilus. ;)
A handful of us use Nemo.
**[COLOR=#FF0000]**WARNING**[/COLOR]**Unless you have a strong disliking of Nautilus/Files, you should not try to experiment like this with the default file manager. Changing an integral component may lead to conflicts and broken systems. If you are an advanced user who knows what’s he/she is doing, you may follow the rest of the tutorial.  [https://itsfoss.com/install-nemo-file-manager-ubuntu/](https://itsfoss.com/install-nemo-file-manager-ubuntu/)
Good Luck. :D

Thanks for the help.  I think I'm going to keep it simple and just move away from Ubuntu, either back to Mint or maybe on to some other distro.  Hell, I still have a copy of Windows 10 floating around somewhere.  

Thanks again!

---

### Post by #&amp;thj^% on 2019-10-27
> **ravrak said:**
> Thanks for the help.  I think I'm going to keep it simple and just move away from Ubuntu, either back to Mint or maybe on to some other distro.  Hell, I still have a copy of Windows 10 floating around somewhere.  

Thanks again!
You can just install "nemo" and just use it, without making it default.
And there are many flavors of Ubuntu to pick from.

---

### Post by ravrak on 2019-10-28
> **1fallen said:**
> You can just install "nemo" and just use it, without making it default.
And there are many flavors of Ubuntu to pick from.

I could, but the more I played with Ubuntu the more quirky, head-scratching things I found.  And since I tried MATE and then moved back to Gnome, a lot of stuff is broken (it warned me before I switched, so fair's fair.)  Like, Super+L doesn't lock my screen anymore, the login screen is still MATE even though I'm back to Gnome, my screen no longer times out at 10 minutes like it was supposed to.  On and on.  

If Ubuntu is feature-lacking out of the box, and then breaks when I try to work around that lack of features...it just doesn't feel finished to me.  I was going to just sell the desktop and work on my iPad, but I've downloaded Linux Mint again and I think I'll give that a whirl one more time.  It, at least, worked out of the box.  

I dunno.  I guess I want more customization than Ubuntu allows.  And more stability.  

Anyway, thanks again for the help.  I really do appreciate it.  :)

ETA: Turns out Ubuntu also broke my 1TB media drive, so now I have to reformat it and move the 700GB of media I had on it back.  Thank God I back everything up in triplicate or all that data would be lost, compliments of Ubuntu.  :/

---


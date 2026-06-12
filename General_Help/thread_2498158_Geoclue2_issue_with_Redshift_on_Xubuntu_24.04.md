---
title: "Geoclue2 issue with Redshift on Xubuntu 24.04"
date: 2024-06-01
forum: General Help
---

### Post by mnosam on 2024-06-01
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293831&stc=1[/IMG]

I'm getting this error message after installing via apt and attempting to run redshift/redshift-gtk on Xubuntu 24.04. The icon for redshift will appear in the notification bar but a few moments later this message pops up. I've even tried using the redshift.conf file with my location info (copied to ~/.config/redshift/) that worked for me on previous LTS releases. No luck. Not sure if this simply a random bug with 24.04 being pretty new?

---

### Post by guiverc on 2024-06-01
Check your post; you mention that you're using Ubuntu 22.04 LTS but also 24.04 LTS, so which is it??

FYI:  My *redshift* config has remained pretty much unchanged since 14.04, and works now on *oracular *or what will be 24.10 on release.. I didn't require change at 24.04 or *noble*. Redshift hasn't changed.

Redshift is an **Xorg** program though, and won't work on Wayland systems, and I do note mention of Wayland in your message..  that is expected as its not intended to be used there.  If using Wayland, use something else, but Redshift can be used on Xorg sessions without issue.

I use Redshift if using Xubuntu/Xfce, Lubuntu/LXQt... but use *Night Light** if using GNOME/Ubuntu and Wayland (*this install of mine is multi-desktop*)

[*Night Shift edited to correctly say Night Light*]("https://help.gnome.org/users/gnome-help/stable/display-night-light.html.en")

---

### Post by mnosam on 2024-06-01
Yeah, sorry, it's 24.04.

Does Night Shift go by another name? I don't see it via apt search in terminal.

Thanks.

---

### Post by guiverc on 2024-06-01
Sorry.. typo..

[I meant the feature provided by GNOME, which is **Night Light**]("https://help.gnome.org/users/gnome-help/stable/display-night-light.html.en").

---

### Post by mnosam on 2024-06-01
If there's a way to somehow import that from GNOME into xfce then that's beyond me.

Thanks though.

---

### Post by mnosam on 2024-06-01
No luck with gammastep either.

---

### Post by &amp;KyT$0P# on 2024-06-02
I'm using that version of gammastep backported to Xubuntu 22.04 and it works without error for me.  But I set location manually in the config.

For automatic location, do you have package [FONT=monospace]geoclue-2.0[/FONT] installed?

---

### Post by mnosam on 2024-06-02
It's installed.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293836&stc=1[/IMG]

---

### Post by mnosam on 2024-06-02
Ok, weird. Now gammastep appears to be working. It obtained location data automatically.

No clue what I might have done other than uninstall/purge it once then re-install.

---


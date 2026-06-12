---
title: "How do i stop lubuntu from hanging and nagging for file during password prompts?"
date: 2016-01-09
forum: General Help
---

### Post by xander2077 on 2016-01-09
I don't really know where to start. since many actions in system settings require the root password or fake root, i find myself entering my password often, and i don't mind that at all, however when i do, there seems to be an issue that persists on my desktop, and that is when i begin entering the password at prompt, the rest of the screen has a translucent overlay other than the prompt window, and then the system hangs as if it is searching for a script, then it eventually returns to normal, but in the mean time i cant see what is going on, and i would love to find a way to eliminate this minor annoyance, because it is more than likely trying to run a process that is either waiting for a dependency that doesn't exist, or searching for a file that doesn't exist. now it has not borked my system, but i know something is not right. i don't even know what i should look for in a log file or how to generate one to track this down. has anyone ever heard of this occurring before? i got rid of everything i had installed to get cairo dock to work and it still didn't work, so i switched to docky and just left it at default settings without all the flashiness. i think this is a delayed reaction to what i had installed with cairo dock or a leftover from that failure, but i cant get it to go away. i finally got rid of drop shadows and other unnecessary garbage that just interferes with a nice clean view, but this overlay still happens every time i get a password prompt.

the error i get is this:

682: Unable to find include file: "apps/xfce4-notifyd.rc"

what is calling for this file that i need to eliminate in order to get it to stop hanging? i can accept an overlay if it will stop hanging. is there a way to remove the overlay? all i could fine by googling was how to add translucent overlays and shadow effects, but they dont say how to remove them if you have them and want to get them gone. and i prefer not to have them. it just bogs thing down.

Edit: the problem was not the translucent overlay, but the missing file. the translucent overlay is coded into the gui and probably can be tweaked to reduce opacity to zero, but i still need to figure out that tweak, so it is not the issue.

---

### Post by xander2077 on 2016-01-10
PLEASE MARK THIS SOLVED.

it turns out after scouring a bit more in these forums i found the answer to why it is hanging simply by following the prompt and doing a little reverse engineering. of course this is probably not the way it is supposed to look, but it stopped hanging as long as it was and only hangs a tad (like normal) when doing a password check.

here is what i did to stop it from nagging about the missing file

i logged into "root" and went to the folder /usr/share/themes/Lubuntu-default/xfce-notify-4.0

there i located a file that would work called "gtkrc" and copied it

pasted it into the folder /usr/share/themes/Lubuntu-dark-panel/gtk-2.0/apps and then renamed it to "xfce4-notifyd.rc"

the nag stopped and it did not hang any more looking for a file that didn't exist. for whatever reason it was not there or uninstalling something else took the file with it and there are leftover parts of packages still asking for that file.

hope this helps someone. glad i have this forum to log my thoughts so i can trace things down and record it here.

if anyone has any tips on how to clean xfce4-notifyd.rc up and remove unnecessary dialog from it, or what to comment out so that it is more trim, i would appreciate it.

here are the contents of my reverse engineered "xfce4-notifyd.rc" for reference:
```
style "notify-window"
{
    XfceNotifyWindow::summary-bold = 1
    XfceNotifyWindow::border-color = "#ffffff"
    XfceNotifyWindow::border-radius = 10.0
    XfceNotifyWindow::border-width = 0.0
    bg[NORMAL] = "#111"
}

style "notify-button"
{
    bg[NORMAL] = "#202020"
    bg[PRELIGHT] = "#404040"
    fg[NORMAL] = "#ffffff"
    fg[PRELIGHT] = "#ffffff"
    engine "murrine" {
        roundness = 4
    }
}

style "notify-text"
{
    fg[NORMAL] = "#ffffff"
    GtkWidget::link-color = "#a7a7a7"
}

style "notify-progressbar"
{
    xthickness   = 1
    ythickness   = 1

    fg[PRELIGHT] = "#000000"
    bg[NORMAL]   = "#dbdbdb"
    bg[SELECTED] = "#dbdbdb"

    engine "murrine" {
        gradient_shades = {1.1,0.95,1.1,0.85}
        contrast    = 0.5
        border_shades    = { 0.9, 0.9 }
        progressbarstyle    = 0
    }
}

class "XfceNotifyWindow" style "notify-window"
widget_class "XfceNotifyWindow.*<GtkButton>" style "notify-button"
widget_class "XfceNotifyWindow.*.<GtkLabel>" style "notify-text"
widget_class "XfceNotifyWindow.*.<GtkProgress>" style "notify-progressbar"
widget_class "XfceNotifyWindow.*.<GtkProgressBar>" style "notify-progressbar"

```

granted, i did not get rid of the overlay, but this will suffice for a quick fix on the hanging issue.

---


---
title: "Is there a way to change the background of notify-osd without a nonsense PPA?"
date: 2014-09-24
forum: General Help
---

### Post by Roasted on 2014-09-24
Hello friends. I'm not one for wallpaper, as I normally just set it to a darker default and be done with it. I just took a picture of my daughter and converted it to black and white with deeper contrasts (thanks, Gimp). I set it as my wallpaper. Of course, the launcher lit up in obnoxious white influenced ways, but I fixed that via unity-tweak-tool. My only gripe now is the notify-osd bubbles are very light, which is a bit difficult to read against white text. Through reading around, it sounds like the only way to do anything *period* with notify-osd is through additional PPAs to add in a patched version of notify-osd to make further changes. Meh.

I can't help but to wonder if there's another way. It's obvious that notify-osd pulls its background color/darkness from the wallpaper image. I looked through the tweak tool but found nothing that was related. Is there any way to simply control what color the background is? Or else break the connection that causes it to be so light based on wallpaper? To be completely blunt about it, it's pretty stupid to base it against wallpaper, given that 99% of the time, your wallpaper is not what you're looking at. On a higher resolution screen while reading a web page, it's often sitting on top of a blank white area, which of course further instigates my frustration with this seemingly simple thing. 

(It's times like this I look at Gnome with their deep black background colors and easy to read text and think... yes... YES)

[IMG]http://i.imgur.com/8IMeTys.png[/IMG]
[IMG]http://i.imgur.com/kIl4Tax.png[/IMG]

---

### Post by vasa1 on 2014-09-24
The notification system used by XFCE is customizable: [http://xubuntugeek.blogspot.com/2012/10/how-to-customize-xfce-desktop.html](http://xubuntugeek.blogspot.com/2012/10/how-to-customize-xfce-desktop.html)

---

### Post by Roasted on 2014-09-24
> **vasa1 said:**
> The notification system used by XFCE is customizable: [http://xubuntugeek.blogspot.com/2012/10/how-to-customize-xfce-desktop.html](http://xubuntugeek.blogspot.com/2012/10/how-to-customize-xfce-desktop.html)

I just tried that, but changing the opacity settings followed by consecutive "test" notifications yielded no change in the transparency. It's still lighter than I prefer. I wonder if I have to kill the daemon after each change vs just closing out the GUI dialog??

Also, if I were to switch to this xfce4-notifyd alternative, would I still have notify-osd hanging around, thereby duplicating notifications? (as in, one from notify-osd, one from xfce4-notifyd), or would I be able to turn off notify-osd so xfce4-notifyd takes over?

---

### Post by vasa1 on 2014-09-24
There are posts on askubuntu.com on the topic. I'll see if I can dig some out.

---

### Post by vasa1 on 2014-09-24
[http://askubuntu.com/a/239928](http://askubuntu.com/a/239928)
[http://askubuntu.com/questions/150438/xfce4-overrode-my-gnome-notifications-notify-osd-how-do-i-get-them-back/343291#343291](http://askubuntu.com/questions/150438/xfce4-overrode-my-gnome-notifications-notify-osd-how-do-i-get-them-back/343291#343291)

Just search for "xfce4-notifyd" for more.

Edit: I control (to the extent possible) the appearance of the notification by playing with /home/vasa1/.themes/MyGreybird/xfce-notify-4.0/gtkrc. Right now, it looks like this: ```
style "notify-window"
{
    XfceNotifyWindow::summary-bold = 1
    XfceNotifyWindow::border-color = "#555555"
    XfceNotifyWindow::border-radius = 10.0
    XfceNotifyWindow::border-width = 0.0
    bg[NORMAL] = "#111"
}

style "notify-button"
{
    bg[NORMAL] = "#202020"
    bg[PRELIGHT] = "#404040"
    fg[NORMAL] = "#777777"
    fg[PRELIGHT] = "#777777"
    engine "murrine" {
        roundness = 4
    }
}

style "notify-text"
{
    fg[NORMAL] = "#777777"
    GtkWidget::link-color = "#777777"
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
        contrast	= 0.5
        border_shades	= { 0.9, 0.9 }
        progressbarstyle    = 0
    }
}

class "XfceNotifyWindow" style "notify-window"
widget_class "XfceNotifyWindow.*<GtkButton>" style "notify-button"
widget_class "XfceNotifyWindow.*.<GtkLabel>" style "notify-text"
widget_class "XfceNotifyWindow.*.<GtkProgress>" style "notify-progressbar"
widget_class "XfceNotifyWindow.*.<GtkProgressBar>" style "notify-progressbar"

```It's less "elegant" than the Unity one :)
I don't have transparency on my laptop and so I don't do anything with the opacity setting.

---


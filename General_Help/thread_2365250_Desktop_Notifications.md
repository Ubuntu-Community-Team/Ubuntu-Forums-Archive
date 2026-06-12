---
title: "Desktop Notifications"
date: 2017-07-04
forum: General Help
---

### Post by Dennis N on 2017-07-04
If it can be done, where can I configure the position of the Desktop notifications for Ubuntu Budgie? Thanks.

---

### Post by #&amp;thj^% on 2017-07-04
Dennis N I have not yet played with this: [http://www.omgubuntu.co.uk/2016/11/budgie-desktop-picks-indicator-applet-support](http://www.omgubuntu.co.uk/2016/11/budgie-desktop-picks-indicator-applet-support)
I don't know how full featured it is.

---

### Post by davidmohammed on 2017-07-04
It is coded to appear in a specific part of the screen - [https://github.com/budgie-desktop/budgie-desktop/blob/f9b0c4e1e5cd63ec6b749f7b067afa6dd7e5b3be/src/raven/notifications_view.vala](https://github.com/budgie-desktop/budgie-desktop/blob/f9b0c4e1e5cd63ec6b749f7b067afa6dd7e5b3be/src/raven/notifications_view.vala)

---

### Post by Dennis N on 2017-07-04
> **1fallen said:**
> Dennis N I have not yet played with this: [http://www.omgubuntu.co.uk/2016/11/budgie-desktop-picks-indicator-applet-support](http://www.omgubuntu.co.uk/2016/11/budgie-desktop-picks-indicator-applet-support)
I don't know how full featured it is.

Thanks for the link. I checked this out and find the indicator applet is installed by default in Budgie 17.04. It allows applications to place notification icons the panel. By Desktop notifications, I meant the bubbles that pop up to announce stuff. Usually configurable in some dialog. There is a settings dialog for notifications, but no positioning options there.

Also then found:
[https://github.com/budgie-desktop/budgie-desktop/issues/613](https://github.com/budgie-desktop/budgie-desktop/issues/613)
so maybe not available yet - a future enhancement. But then I think: the position is defined somewhere in this system.

---

### Post by #&amp;thj^% on 2017-07-04
> **davidmohammed said:**
> It is coded to appear in a specific part of the screen - [https://github.com/budgie-desktop/budgie-desktop/blob/f9b0c4e1e5cd63ec6b749f7b067afa6dd7e5b3be/src/raven/notifications_view.vala](https://github.com/budgie-desktop/budgie-desktop/blob/f9b0c4e1e5cd63ec6b749f7b067afa6dd7e5b3be/src/raven/notifications_view.vala)
Thanks.
So is it hard coded then?
```
 private void configure_window(NotificationWindow? window)
    {
        int x = 0;
        int y = 0;
        Gdk.Rectangle rect;

        unowned NotificationWindow? tail = stack.peek_head();
        var screen = Gdk.Screen.get_default();

        int mon = screen.get_primary_monitor();

        screen.get_monitor_geometry(mon, out rect);

        if (tail != null) {
            int nx;
            int ny;
            tail.get_position(out nx, out ny);
            x = nx;
            y = ny + tail.get_child().get_allocated_height() + BUFFER_ZONE;
} else {
```

---

### Post by davidmohammed on 2017-07-04
its coded to appear on the primary monitor is the current location - so no user overrides available.  The code will need to be tweaked to allow positioning across the  primary monitor maybe via a gsetting key/keys.  That will be for an awesome dev to submit a PR to-do that.

---

### Post by #&amp;thj^% on 2017-07-04
> **davidmohammed said:**
> its coded to appear on the primary monitor is the current location - so no user overrides available.  The code will need to be tweaked to allow positioning across the  primary monitor maybe via a gsetting key/keys.  That will be for an awesome dev to submit a PR to-do that.

Thank You Sir! 
And Agree that would be an awesome feature to undertake! :D

---

### Post by Dennis N on 2017-07-04
> **davidmohammed said:**
> its coded to appear on the primary monitor is the current location - so no user overrides available.  The code will need to be tweaked to allow positioning across the  primary monitor maybe via a gsetting key/keys.  That will be for an awesome dev to submit a PR to-do that.

I agree - should be user configurable.

---


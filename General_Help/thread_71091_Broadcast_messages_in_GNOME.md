---
title: "Broadcast messages in GNOME"
date: 2005-10-02
forum: General Help
---

### Post by NiceGuyUK on 2005-10-02
Does anyone know how I get a broadcast message (or something similar) to appear under a GNOME session, ie, in a popup box?

I realise this can be done by launching a terminal window, but I need users to be able to get the message even if they don't have a terminal window open.

Thanks,

NiceGuyUK

---

### Post by Brendt2 on 2007-08-13
That would be very cool... does anyone have any idea how to send messages using the terminal... or otherwise?

---

### Post by yoda2031 on 2007-12-19
@Brendt2:

To send messages between terminals:

Open terminal twice.

Type "who" in the first terminal.

You should get an output similar to this:

```

uname       tty7         2007-12-19 08:31 (:0)
uname  pts/0            2007-12-19 17:00 (:0)
uname  pts/1            2007-12-19 15:36 (:0)

```

Right, assuming you're in pts/0 (I'm not sure how to tell which terminal you're using at any given time, it's a lot simpler when you're talking to someone who SSH'd or otherwise has a terminal open on your box but is accessing it through the network because it will show you their IP in who), just type "write uname pts/1".

Hit enter, begin typing.  Each time you hit enter the message is sent to pts/1.

Common syntax:

-o = "Over" = I'm done talking, it's your turn.
oo || -oo = "Over and Out" = I'm done talking to you, get back to work!

To exit the write program, simply Ctrl+C it.  Note that for a user to reply, they will have to execute the write command also, so don't expect this to work with novice users.

As for apps that create popups in a different X display - that's up to the individual net/sys admin - I plan to develop such an app but have many projects ongoing at the moment and it's at the bottom of my list!

Hope this helps,
Ciao,
Chris "Yoda" Browne

---


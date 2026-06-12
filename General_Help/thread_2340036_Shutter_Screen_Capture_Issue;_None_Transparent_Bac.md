---
title: "Shutter Screen Capture Issue; None Transparent Background - Tiled"
date: 2016-10-15
forum: General Help
---

### Post by imzack2 on 2016-10-15
I don't know what I did; but whatever I do, I cant get shutter to work.

I have uninstalled and reinstalled, and changed every setting possilbe.

When I try a screen capture, all I see is the picture attached.  When I try to make a selection, and hoping that I will actually grab what is behind the selection overlay; it acutally grabs the overlay instead.

I hope I am explaining this properly.

Any help would be greatly appreciated!

Thanks

[IMG]http://i65.tinypic.com/30964uf.png[/IMG]

---

### Post by ajgreeny on 2016-10-15
Is there a configuration folder somewhere in your home for shutter as you may need to remove that to get back to the default manner of screenshot behaviour.

I've never used shutter so do not know where it puts any config folders or files so have a good search and move them to trash if you find them.
You can probably find any configs in your home with commands ```
sudo updatedb && locate shutter | grep *username*
```using your username of course.

---

### Post by Habitual on 2016-10-15
> **ajgreeny said:**
> Is there a configuration folder somewhere in your home for shutter as you may need to remove that to get back to the default manner of screenshot behaviour.

```
rm -fr $HOME/.shutter/
``` on shutter 0.90.

---

### Post by ajgreeny on 2016-10-15
Thanks Habitual!

@ OP
Try that command from habitual and start shutter again to see if it overcomes your proble.

---

### Post by imzack2 on 2016-10-15
Unfortunatley It didn't fix it.

Maybe an issue with Shutter and my desktop environment?

---

### Post by howefield on 2016-10-15
> **imzack2 said:**
> ...Maybe an issue with Shutter and my desktop environment?

What version of Ubuntu and desktop environment are you using ?

---

### Post by imzack2 on 2016-10-15
I'm using gdm3 I believe.

root@user:~# $DESKTOP_SESSION
bash: /usr/share/wayland-sessions/gnome-wayland: No such file or directory


Not sure if this is any help.

---

### Post by howefield on 2016-10-15
> **imzack2 said:**
> I'm using gdm3 I believe.

root@user:~# $DESKTOP_SESSION
bash: /usr/share/wayland-sessions/gnome-wayland: No such file or directory

Try..

```
echo $XDG_CURRENT_DESKTOP
```

and which distro ?

---

### Post by imzack2 on 2016-10-15
Gnome; and is there a command to know what dist I am on?  Ive done dist upgrades... not sure anymore

---

### Post by howefield on 2016-10-15
> **imzack2 said:**
> Gnome; and is there a command to know what dist I am on?  Ive done dist upgrades... not sure anymore

Try...

```
cat /etc/*-release
```

---


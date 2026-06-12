---
title: "Running GUI apps in LXC Container"
date: 2015-01-08
forum: General Help
---

### Post by terminator14 on 2015-01-08
I finally got around to trying LXC, and it seems awesome.
The only issue I'm having is running any GUI apps.
Attaching to a running LXC container with:
```
sudo lxc-attach -n CONTAINER
```
I run "xeyes", but all I see is:
> Error: Can't open display: :0
How difficult is it to run GUI apps from an LXC container?
Does it have something to do with using xhost to allow clients
to connect to the X server on the host? I tried that and it didn't
seem to help, but maybe I did it wrong. Or is it something else?

---

### Post by ajgreeny on 2015-01-08
I am not aware of LXC but in view of the error I wonder if you need to add an "EXPORT to display" first as you do when running GUI apps from a crontab
```
export DISPLAY=:0 && command
```
Play around with that, though be careful as I have to admit no knowledge at all of what you're trying to do, and proceed with caution if using a GUI app with root permissions.

---

### Post by terminator14 on 2015-01-08
> **ajgreeny said:**
> ```
export DISPLAY=:0 && command
```

I've had to do this in cron before, so it was one of the first things I tried with LXC. Didn't help.
I'm not sure, but I think LXC might need to be configured somehow to allow GUI apps to run.
Anyone have any experience with this?

---

### Post by paul.gevers on 2015-01-10
On my system, I have xauth running, so my $DISPLAY is limited to access to the key. I haven't gotten this working with unix sockets in the lxc (I like to hear how to do that) but I commented out "-nolisten tcp" in /etc/kde4/kdm/kdmrc (I use KDE). I was then able to use my ~/.Xauthority (mounted) in the lxc container and by adding $DISPLAY=<IP_of_host>:0 it worked.

---


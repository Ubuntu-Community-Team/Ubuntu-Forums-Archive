---
title: "Run a flatpak with firejail-like --overlay-tmpfs?"
date: 2021-01-17
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-01-17
firejail has a handy option [FONT=Courier New]--overlay-tmpfs[/FONT]
```
       --overlay-tmpfs
              Mount a filesystem overlay on top of the current filesystem. All filesys&#8208;
              tem modifications are discarded when the sandbox is  closed.  Directories
              /run,  /tmp  and  /dev are not covered by the overlay.  If the sandbox is
              started as a regular user, nonewprivs and a default  capabilities  filter
              are enabled.

              OverlayFS  support  is  required in Linux kernel for this option to work.
              OverlayFS was officially introduced in Linux kernel version  3.18.   This
              option is not available on Grsecurity systems.

```

I would like to be able to use something like this with some apps I have installed as flatpak.  But I can't use firejail for this, because flatpak does its own sandboxing, which is not compatible with being inside a firejail sandbox.

So does flatpak have its own option like firejail's [FONT=Courier New]--overlay-tmpfs[/FONT]?  If not, is there any other way to achieve the same effect?

---

### Post by &amp;KyT$0P# on 2021-01-25
bump

---

### Post by &amp;KyT$0P# on 2021-06-09
bump

---

### Post by Tadaen_Sylvermane on 2021-06-10
Im curious what app you are trying to run. Docker may be more appropriate?

---

### Post by &amp;KyT$0P# on 2021-06-10
> **Tadaen_Sylvermane said:**
> Im curious what app you are trying to run.

I don't have a specific app in mind.  Could be any app I have installed as flatpak.  In practice it'll probably mostly be various web browsers.

> Docker may be more appropriate?

Some of the time I'm already working in a disposable VM.  I find [FONT=Courier New]--overlay-tmpfs[/FONT] to be a helpful layer even there.

---

### Post by Tadaen_Sylvermane on 2021-06-10
Docker by it's nature is immutable. You create an image and it doesn't change. Whatever you do is lost when the container is stopped. There are ways to put browsers into them.

[https://leimao.github.io/blog/Docker-Container-GUI-Display/](https://leimao.github.io/blog/Docker-Container-GUI-Display/)

I think there are ways to do sound as well but I'm not entirely sure. I know for me I've done Kodi in a docker and piped the pulse audio to a remote pulse server on my lan.

---

### Post by &amp;KyT$0P# on 2021-06-10
Just to check: I was under the impression that Docker is VM based.  Is this wrong?  Would Docker work inside a VirtualBox 6.0.24 VM?

Can Docker images be set up offline from a host OS that already has everything needed to run the app?

---

### Post by Tadaen_Sylvermane on 2021-06-12
If you have a local repo when you create the image yes. It will just run. Look up what a Docker file is. Once it's built via the Docker file you can just run it with a terminal command, which could be put in a .desktop file if you wanted.

---

### Post by &amp;KyT$0P# on 2021-06-12
Thanks Tadaen_Sylvermane.  I read a little about Docker and it seems I maybe actually completely unfamiliar with it and don't understand it at all.  I'll need to find time to do a lot more reading about Docker and play with it a bit before getting back to this.

---

### Post by &amp;KyT$0P# on 2022-05-09
I finally found the time to look into Docker in a bit more detail.  Unfortunately Docker seems way too involved for what I'm seeking here.

Searching about this issue now, indicates pretty clearly this is not directly possible. :(

The closest that can be done is:

1) Tighten the flatseal sandbox so that the app does not have direct write access to anything outside its [FONT=Courier New]~/.var/app/[COLOR="#FF0000"]<flatpak_app_id>[/COLOR][/FONT] directory.

2) Run the flatpak in a wrapper script that:
[LIST]
[*]creates a backup copy of the [FONT=Courier New]~/.var/app/[COLOR="#FF0000"]<flatpak_app_id>[/COLOR][/FONT] directory,
[*]runs the app,
[*]after the app quits, replaces the [FONT=Courier New]~/.var/app/[COLOR="#FF0000"]<flatpak_app_id>[/COLOR][/FONT] directory with the backup copy from before running the flatpak.
[/LIST]

More details about such wrapper script in [this thread]("https://ubuntuforums.org/showthread.php?t=2473907").

---


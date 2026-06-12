---
title: "gvfsd-trash fills /var/log/syslog"
date: 2022-05-01
forum: General Help
---

### Post by palteater on 2022-05-01
22.04 fresh install. My /var/log/syslog is filled to the brim with hundreds of GB of the same message:

[FONT=fixedsys]May  1 13:10:50 XXXXX gvfsd[1936]: message repeated 5 times: [ (process:1936): GLib-GIO-WARNING **: 11:10:50.552: fail: Error accepting connection: Too many open files]
May  1 13:10:50 XXXXX gvfsd[1936]: (process:1936): GLib-GIO-WARNING **: 11:10:50.553: fail: Error accepting connection: Too many open files
[/FONT]
This continues until I kill process gvfsd-trash. Then I truncate with sudo tee /var/log/syslog </dev/null

What can cause this thing?

Thanks

---

### Post by palteater on 2022-05-01
I should add that the remedy is temporary - the process restarts after a while and begins spamming /var/log/syslog again.

---

### Post by vsomdvfjso on 2022-05-01
I have the same issue since i upgraded to 22.04

It seems like this is reported here: [https://gitlab.gnome.org/GNOME/gvfs/-/issues/606](https://gitlab.gnome.org/GNOME/gvfs/-/issues/606)

---

### Post by palteater on 2022-05-03
Yep - seems like DING is the culprit. Removing /usr/share/gnome-shell/extensions/ding@rastersoft.com cured it.

---

### Post by ActionParsnip on 2022-05-03
You can truncate files easily with
```

>  /var/log/syslog

```
Nice and short :)

---

### Post by palteater on 2022-05-03
I should mention this:
Running[FONT=courier new] "sudo gnome-extensions disable [email]ding@rastersoft.com[/email]" [/FONT]did **not** work. 

Then I ran "[FONT=courier new]sudo apt install dconf-editor" [/FONT]and after that "[FONT=courier new]gnome-extensions disable [email]ding@rastersoft.com[/email][/FONT]" did work. 

No idea if it was the lack of sudo or because I had then installed dconf-editor, and I ain't about to recurse the steps just to find out.

I figured that may be a less intrusive way of fixing this than my first method during troubleshooting: moving the folder in /usr/share/ to another place.

---

### Post by macachuto on 2022-05-04
I my case - I use Xubuntu, I do not have DING. Or at least I do not see it in "dpkg -l"
But I kill gvfsd-trash and clean logs through journalctl at least 3 times per day

---


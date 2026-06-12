---
title: "flatpak search returns new warning, &quot;was of type addon but had no extends&quot;"
date: 2021-01-16
forum: General Help
---

### Post by Paddy Landau on 2021-01-16
When searching flatpak, I have noticed a new pair of warnings. For example:
```
$ flatpak search dropbox

(flatpak search:45134): As-WARNING **: 14:05:28.665: org.freedesktop.LinuxAudio.BaseExtension was of type addon but had no extends

(flatpak search:45134): As-WARNING **: 14:05:28.665: org.freedesktop.LinuxAudio.BaseExtension was of type addon but had no extends
Name          Description                                                      Application ID             Version   Branch Remotes
Dropbox       Access your files from any computer                              com.dropbox.Client         112.4.321 stable flathub
...
```

[ATTACH=CONFIG]287753[/ATTACH]

I see that this has been [reported to Redhat]("https://bugzilla.redhat.com/show_bug.cgi?id=1913496"), but this most likely has nothing to do with Redhat (unless Redhat controls flatpak).

I tried, as an experiment, installing org.freedesktop.LinuxAudio.BaseExtension, but that made no difference.

Do you know what this warning means, and how to solve these warnings? An internet search has left me unenlightened.

---

### Post by deadflowr on 2021-01-16
It looks like it's that particular package that has the issue
[https://github.com/flathub/org.freedesktop.LinuxAudio.BaseExtension/issues/4#issuecomment-755435188]("https://github.com/flathub/org.freedesktop.LinuxAudio.BaseExtension/issues/4#issuecomment-755435188")
Nothing on the end user side we can do about it, at least not yet.

---

### Post by Paddy Landau on 2021-01-16
> **deadflowr said:**
> It looks like it's that particular package that has the issue…
Thank you. At least they are aware, and so I hope that it's solved reasonably soon.

I've made a note on the Redhat bug report.

---


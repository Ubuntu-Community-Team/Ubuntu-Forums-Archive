---
title: "What are these error messages from &quot;flatpak search&quot;?"
date: 2023-03-15
forum: General Help
---

### Post by Paddy Landau on 2023-03-15
I'm unsure where to ask this question, so I hope that it's OK here.

Since quite recently, when I issue the command "flatpak search", I get a huge number of spurious errors. The command works perfectly, apart from the mass of error messages.

The message is always the same except for the number (whatever the number means) and of course the time. Here's an extract:
```
[COLOR=#000080]$ flatpak search gedit[/COLOR]

(flatpak search:103378): GLib-CRITICAL **: 17:21:06.432: g_once_init_leave: assertion 'g_atomic_pointer_get (value_location) == 0' failed

(flatpak search:103378): GLib-CRITICAL **: 17:21:06.432: g_once_init_leave: assertion 'g_atomic_pointer_get (value_location) == 0' failed

(flatpak search:103378): GLib-CRITICAL **: 17:21:06.432: g_once_init_leave: assertion 'g_atomic_pointer_get (value_location) == 0' failed

[COLOR=#4b0082]...
... repeated 3,010 times!
...[/COLOR]

(flatpak search:103378): GLib-CRITICAL **: 17:21:06.653: g_once_init_leave: assertion 'g_atomic_pointer_get (value_location) == 0' failed
**Name                    Description                                  Application ID                             Version          Branch          Remotes**
gedit                   Text editor                                  org.gnome.gedit                            44.2             stable          flathub
Apostrophe              Edit Markdown in style                       org.gnome.gitlab.somas.Apostrophe          2.6.3            stable          flathub
Text Editor             Edit text files                              org.gnome.TextEditor                       43.1             stable          flathub
Tau                     GTK frontend for the xi text editor          org.gnome.Tau                              0.12.0           stable          flathub
ThemeGenerator          Generate Styles with Style.                  io.github.thiefmd.themegenerator           0.1.1            stable          flathub
```
Other flatpak commands (install, refresh, uninstall) all work fine.

What does this error message mean, and, more importantly, how do I get rid of it?

Also, where do I report this bug?

Thanks

---

### Post by Dennis N on 2023-03-15
I vaguely remember seeing such errors once in the past, but they did not reappear. You could filter out the error messages with grep -v on one of the words they all have in common, for example:

```
flatpak search gedit | grep -v failed
```

---

### Post by #&amp;thj^% on 2023-03-15
Along with the above what shows with;
```
flatpak repair
```
I have 2 Debian systems both show what you see.
On Arch no errors/warnings shown

---

### Post by Paddy Landau on 2023-03-15
> **Dennis N said:**
> ```
flatpak search gedit | grep -v failed
```
That won't work, because the error messages go to stderr. I can use:
```
flatpak search gedit 2>/dev/null
```
but that eliminates all error messages. I don't know how to pipe only stderr to grep while leaving stdout untouched.
> **1fallen said:**
> Along with the above what shows with…
I had to use sudo, otherwise it assumed dry run.
```
$ sudo flatpak repair
Working on the system installation at /var/lib/flatpak
[103/103] Verifying flathub:runtime/org.kde.Platform.Locale/x86_64/5.15-21.08…
Checking remotes...
Pruning objects
Erasing .removed
```
This didn't solve the problem.

---

### Post by #&amp;thj^% on 2023-03-15
> **Paddy Landau said:**
> 
I had to use sudo, otherwise it assumed dry run.
```
$ sudo flatpak repair
Working on the system installation at /var/lib/flatpak
[103/103] Verifying flathub:runtime/org.kde.Platform.Locale/x86_64/5.15-21.08&#8230;
Checking remotes...
Pruning objects
Erasing .removed
```
This didn't solve the problem.
No it did not,(I meant to run it with no changes made) I was hoping for something to jump out, from the return.
anything show from this:
```
G_DEBUG=fatal_warnings flatpak update
Looking for updates&#8230;

Nothing to do.

```
or better:
```
G_DEBUG=fatal_warnings flatpak search gedit
Name           Description                         Application ID                    Version Branch Remotes
gedit          Text editor                         org.gnome.gedit                   44.2    stable flathub
Apostrophe     Edit Markdown in style              org.gnome.gitlab.somas.Apostrophe 2.6.3   stable flathub
Text Editor    Edit text files                     org.gnome.TextEditor              43.1    stable flathub
Tau            GTK frontend for the xi text editor org.gnome.Tau                     0.12.0  stable flathub
ThemeGenerator Generate Styles with Style.         io.github.thiefmd.themegenerator  0.1.1   stable flathub


```
Folks over at Faltpak call it a GLib bug. (fwiw)

---

### Post by &amp;KyT$0P# on 2023-03-15
> **Paddy Landau said:**
> I don't know how to pipe only stderr to grep while leaving stdout untouched.

Try this? -
```
flatpak search gedit 2> >(grep -v -P 'g_once_init_leave|^$')
```

---

### Post by MAFoElffen on 2023-03-15
This bug was reported and opened up 2 weeks ago: [https://github.com/flatpak/flatpak/issues/5323](https://github.com/flatpak/flatpak/issues/5323)

---

### Post by Paddy Landau on 2023-03-16
> **1fallen said:**
> anything show from this&#8230;
```
$ G_DEBUG=fatal_warnings flatpak update
Looking for updates&#8230;


Nothing to do.
```
```
$ G_DEBUG=fatal_warnings flatpak search gedit


(flatpak search:9353): GLib-CRITICAL **: 13:47:36.269: g_once_init_leave: assertion 'g_atomic_pointer_get (value_location) == 0' failed
Trace/breakpoint trap (core dumped)
```
That returned with error code 133. Do you know where the core would have been dumped to?
> **1fallen said:**
> Folks over at Faltpak call it a GLib bug. (fwiw)
Ah, thanks.

> **halogen2 said:**
> Try this? -
```
flatpak search gedit 2> >(grep -v -P 'g_once_init_leave|^$')
```
Thank you! I had completely forgotten about that format.
> **MAFoElffen said:**
> This bug was reported and opened up 2 weeks ago: [https://github.com/flatpak/flatpak/issues/5323](https://github.com/flatpak/flatpak/issues/5323)
Thanks. I see that it was closed because it was fixed, but Ubuntu hasn't incorporated the fix yet. It has been redirected to [this Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/2006110"). I've voted for the bug, but that makes only two people voting for it. In my experience, that means that the bug will be ignored and closed in about four years.

---

### Post by Paddy Landau on 2023-03-16
Thanks to the previous posters, I have realised something important.

The default flatpak that comes with Ubuntu, which is version 1.12. 7, doesn't have this bug.

I had added PPA flatpak/stable, which upgraded flatpak to version 1.14.3, and that has the bug.

Removing the PPA flatpak/stable and reverting to the default Ubuntu flatpak has resolved the issue.

---

### Post by Dennis N on 2023-03-16
> **Paddy Landau said:**
> Thanks to the previous posters, I have realised something important.

The default flatpak that comes with Ubuntu, which is version 1.12. 7, doesn't have this bug.

I had added PPA flatpak/stable, which upgraded flatpak to version 1.14.3, and that has the bug.

Removing the PPA flatpak/stable and reverting to the default Ubuntu flatpak has resolved the issue.

And the PPA calls it stable. Not quite, I appears.
FWIW, I'm using Manjaro Gnome right now, and it has an even newer version:  flatpak 1.15.2 -- I have not seen any problems here.

```
[dmn@Sydney ~]$ flatpak --version
Flatpak 1.15.2

```

---

### Post by Paddy Landau on 2023-03-16
> **Dennis N said:**
> And the PPA calls it stable. Not quite, I appears.
I think that it has to do with the library libappstream, not with flatpak itself.
> **Dennis N said:**
> FWIW, I'm using Manjaro Gnome right now, and it has an even newer version:  flatpak 1.15.2 -- I have not seen any problems here.
Where did you get that version? If it's easily installed on Ubuntu, I'll try it.

---

### Post by MAFoElffen on 2023-03-16
> **Paddy Landau said:**
> Thanks. I see that it was closed because it was fixed, but Ubuntu hasn't incorporated the fix yet. It has been redirected to [this Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/2006110"). I've voted for the bug, but that makes only two people voting for it. In my experience, that means that the bug will be ignored and closed in about four years.
Yes. Sad, but mostly true... LOL

---

### Post by #&amp;thj^% on 2023-03-16
> **Paddy Landau said:**
> I think that it has to do with the library libappstream, not with flatpak itself.

Where did you get that version? If it's easily installed on Ubuntu, I'll try it.

Manjaro is an Arch Based Distro, so it was built for that OS:
But here is what's available for All Ubuntu's
```
 flatpak | 0.11.3-3         | bionic/universe          | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.0.9-0ubuntu0.4 | bionic-security/universe | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.0.9-0ubuntu0.4 | bionic-updates/universe  | source, amd64, arm64, armhf, i386, ppc64el, s390x
 flatpak | 1.6.3-1          | focal/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.6.5-0ubuntu0.4 | focal-security/universe  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.6.5-0ubuntu0.4 | focal-updates/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.12.7-1         | jammy/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.14.0-2         | kinetic/universe         | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 flatpak | 1.14.3-1         | lunar/universe           | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```
I'm using Lunar now:
```
flatpak --version
Flatpak 1.14.3

```
and:
```
~$ flatpak search gedit
Name     Description             Application ID           Version Branch Remotes
gedit    Text editor             org.gnome.gedit          44.2    stable flathub
Apostro&#8230; Edit Markdown in style  &#8230;gitlab.somas.Apostrophe 2.6.3   stable flathub
Text Ed&#8230; Edit text files         org.gnome.TextEditor     43.1    stable flathub
Tau      GTK frontend for the x&#8230; org.gnome.Tau            0.12.0  stable flathub
ThemeGe&#8230; Generate Styles with S&#8230; &#8230;.thiefmd.themegenerator 0.1.1   stable flathub

```
I'm glad your sorted out though.
and on Debian unstable it is --version 1.15.3

---

### Post by Dennis N on 2023-03-16
> Where did you get that version? If it's easily installed on Ubuntu, I'll try it. 
I checked on this, and see that it's apparently a pre-release version. Manjaro has released it as a 'stable' update, however. 
[https://github.com/flatpak/flatpak/releases](https://github.com/flatpak/flatpak/releases)
See Feb 6.
Sorry for the confusion. Eventually, it will get to Ubuntu.

---

### Post by Paddy Landau on 2023-03-17
> **Dennis N said:**
> I checked on this, and see that it's apparently a pre-release version.
OK, thanks.

---


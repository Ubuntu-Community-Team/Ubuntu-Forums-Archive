---
title: "What's with the new Windows-like &quot;Restart &amp; Update&quot; in 22.04?"
date: 2022-09-05
forum: General Help
---

### Post by Paddy Landau on 2022-09-05
In Ubuntu 22.04, every few days there's an update that requires me to restart and update, just as Windows tends to do. This is new — and surprising!

There are also software updates that refuse to be installed; see lower down for an explanation.

I'd like to understand more about this.

[SIZE=4]Background[/SIZE]

I have two different machines, as follows.

[LIST]
[*]My **main** machine has a recent installation of Ubuntu 22.04 (just over a week old).
[LIST]
[*]I installed flatpak.
[*]I replaced Ubuntu Software Store with Gnome Software Store ([FONT=courier new]gnome-software[/FONT]), because Gnome Software Store supports flatpak as well as snap. (Gnome Software Store is otherwise nearly identical to Ubuntu Software Store.)
[/LIST]

[*]My **test** machine has a fresh installation of Ubuntu 22.04 (a couple of days old), where I have installed neither flatpak nor Gnome Software Store.
[/LIST]
[SIZE=4]Summary

[/SIZE]A summary of the situation, which I expand on below, applies only to selected packages (today's examples are listed below). I don't know why. Other packages are processed normally.

[LIST]
[*]Ubuntu Software Store and Software Updater both ignore such updates, as if they don't exist.
[*][FONT=courier new]sudo apt upgrade[/FONT] offers to update some of those packages while holding others back.
[*]Gnome Software Store will offer to update all of those packages but only through a "restart & update" process similar to Windows.
[/LIST]
[SIZE=4]More details[/SIZE]

On both machines, sometimes there are updates that refuse to install. (I've seen others with this same problem.)

[LIST]
[*]Software Updater ([FONT=courier new]update-manager[/FONT]) simply ignores them as if they don't exist.
[*]Ubuntu Software Store also simply ignores them as if they don't exist.
[*][FONT=courier new]sudo apt upgrade[/FONT] updates some of them, but holds others package back. Today (see examples below), it was happy to update all except for [FONT=courier new]gnome-remote-desktop[/FONT].
```
The following packages have been kept back:
  gnome-remote-desktop
The following packages will be upgraded:
  gjs libgjs0g
```
[*]Gnome Software Store (present only on my main machine, not my test machine) does update them, but it only does so by restarting; see the details below.
[/LIST]
[SIZE=4]Gnome Software Store[/SIZE]

On my **main** machine, when I run the Gnome Software Store > Updates, this is how it prompts me to "Restart & Update":
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290992&stc=1[/IMG]
Pressing the button leads to the prompt "Restart & Install Updates":

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290994&stc=1[/IMG]

The machine restarts, installs updates, and restarts again. Very Microsoft Windows-like, isn't it? Except that it's fast; it takes about a minute for the entire restart + install + restart.

Finally, once I've logged back in, Gnome Software Store shows me what has been updated; but, everything is doubled. Here are today's updates:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290995&stc=1[/IMG]
[SIZE=4]So…[/SIZE]

What's up with all of this? :confused: Specifically:

[LIST]
[*]Why are some packages ignored by default?
[*]Why does sudo apt upgrade hold some back?
[*]Why is Gnome Software Store happy to install them, but requires a restart + install + restart? And why does it double the display at the end?
[/LIST]

---

### Post by sudodus on 2022-09-05
My experience is that **[FONT=Courier New]sudo apt update && sudo apt full-upgrade[/FONT]** is reliable. If/when some package is held back it is because that package needs some other package (that it depends on) to be upgraded before it is ready for upgrading.

It is normal that upgrading of the kernel needs a reboot for it to get active unless you have LivePatch running.

I don't use any GUI applications for update and upgrade and I don't know why they behave like you describe and if it is really necessary [with reboot].

I think important reasons for our different experiences are

1. We use different methods for update and upgrade
2. We have different sets of software

---

### Post by ajgreeny on 2022-09-05
I do exactly what [COLOR="#FF0000"]**sudodus**[/COLOR] does for update and upgrade, ie for the upgrade I always run ***sudo apt full-upgrade && ls /var/run | grep reboot-required*** which is more reliable than just the upgrade option, and that final part tells me if a reboot is needed.
This has always worked fine for me, but I do still sometimes see that packages are held back, perhaps for the dependency reasons mentioned by sudodus but also sometimes possibly because of the **phased updates/upgrades** system in use.

Incidentally, I did notice a few days ago that upgrading using synaptic, which I now do not normally use, apparently bypassed the held-back packages system and upgraded them all.  Whether that was just a lucky chance of timing or synaptic always works that way I do not know so I mention it just for information.

---

### Post by Paddy Landau on 2022-09-05
> **sudodus said:**
> **[FONT=Courier New]sudo apt full-upgrade[/FONT]**
I have already tried this, and I just tried again, but it makes no difference.
> **sudodus said:**
> when some package is held back it is because that package needs some other package (that it depends on) to be upgraded before it is ready for upgrading.
That's a good point. Maybe that's exactly what's happening, and it will be upgraded when the dependency is also updated in a few days?

How can I tell why [FONT=courier new]sudo apt upgrade[/FONT] is holding the package back? There is no explanation.
> **sudodus said:**
> It is normal that upgrading of the kernel needs a reboot for it to get active unless you have LivePatch running.
I am aware of this. However, when a kernel update is available, the system updates it without restarting, and then prompts you to restart in order to start using the new kernel. It's not like what I've described, where the machine restarts, performs an update (without any prompt), and restarts again back to the login screen. It is very different.
> **sudodus said:**
> 1. We use different methods for update and upgrade
True.
> **sudodus said:**
> 2. We have different sets of software
Also true.

Still, I'm curious about these changes.

---

### Post by Paddy Landau on 2022-09-05
I've just found a [thread stating]("https://ubuntuforums.org/showthread.php?t=2477612") that apt-upgrade also caters for phased rollouts now. That most likely explains why some items are held back.

---

### Post by Paddy Landau on 2022-09-05
> **ajgreeny said:**
> ls /var/run | grep reboot-required
[FONT=courier new]/var/run[/FONT] has been deprecated in favour of just [FONT=courier new]/run[/FONT].

Also, using [FONT=courier new]ls /run | grep reboot-required[/FONT] is a strange way of doing it. I just check if the file [FONT=courier new]reboot-required[/FONT] exists; from the CLI, it's:
```
ls /run/reboot-required
```
and from a Bash script, it's
```
[[ -e /run/reboot-required ]]
```
> **ajgreeny said:**
> upgrading using synaptic … apparently bypassed the held-back packages system and upgraded them all.
Interesting. I just installed Synaptic on my test machine, but it ignored the held-back package, and offered to update only the other two packages (in the examples that I quoted in the OP).

---

### Post by deadflowr on 2022-09-05
Restart and Updates applies only to gnome-software's updater mechanism.
Something about it discussed here: [https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283]("https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283")
I do agree with the selected solution that it is a rather overly-paranoid way of doing things.
Using update-manager (Software Updater) or apt will still run the same as it always as has.

Sidenote, I have a personal dislike of the behavior of both gnome-software and snap-store of always running in the background.
I understand the why, which is because both would take an excruciatingly long time to fully load otherwise.
(They can make the load times of even the slowest snap packages seem lightning fast in comparison)
But what is even more excruciating is the fact that disabling them is designed to be difficult.
It's just annoying.

---

### Post by Paddy Landau on 2022-09-05
> **deadflowr said:**
> Restart and Updates applies only to gnome-software's updater mechanism.
Something about it discussed here: [https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283](https://ask.fedoraproject.org/t/gnome-software-center-wants-me-to-restart-to-install-updates/1283)
I do agree with the selected solution that it is a rather overly-paranoid way of doing things.
Using update-manager (Software Updater) or apt will still run the same as it always as has.
Thank you. That was informative, and it answers my question. I'll mark the thread as solved.
> **deadflowr said:**
> Sidenote, I have a personal dislike of the behavior of both gnome-software and snap-store of always running in the background.
I understand the why, which is because both would take an excruciatingly long time to fully load otherwise.
(They can make the load times of even the slowest snap packages seem lightning fast in comparison)
But what is even more excruciating is the fact that disabling them is designed to be difficult.
It's just annoying.
Hmm. This is, I think, because of their philosophy for their target market. Canonical's target market is businesses and other organisations that can afford reasonable hardware, and want things to "just work".

Ubuntu is definitely not the ideal distro for people who love to tinker and mess around a lot. It's more for people who want to just load and go, or for people like me who want things to just work, but are happy to tinker a little bit.

---


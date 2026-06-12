---
title: "LibreOffice trying to print to an old printer via Chrome?"
date: 2022-04-06
forum: General Help
---

### Post by Paddy Landau on 2022-04-06
Something bizarre is happening to me with LibreOffice.

I tried to print something from LibreOffice. Unknown to me, it was showing the wrong printer. Naturally, nothing printed. But Chrome started to use 100% CPU. On closing Chrome, the CPU usage stopped.

On looking to see what the problem might be, LibreOffice had offered me an old printer from literally years ago, a long time before I even got my current computer. It doesn't show the correct printer at all.

My Ubuntu Settings has the correct printer, with no sign of my old printer (and why would it show the old one? I got rid of it a few years before I got my current computer).

So…

[LIST]
[*]Ubuntu has the correct printer in Settings > Printers.
[*]LibreOffice is offering me only an old printer from years ago, long gone to recycling.
[*]When printing to that printer from LibreOffice, my Chrome browser uses 100% CPU.
[/LIST]
What's going on?

How did LibreOffice get hold of my old printer, and why is Chrome going nuts when I (accidentally) try to print to that old non-existent printer?

My guess is that somehow Chrome has a record of my old printer, maybe from an old Chromebook? And then LibreOffice is bizarrely trying to print to that old computer via Chrome?

How can I remove that printer?

I am utterly stumped as to what could be going on, and how to fix it.

[LIST]
[*]Ubuntu 20.04
[*]LibreOffice 7.3.2.2
[*]Chrome 100.0.4896.75
[/LIST]
Please help.

Thank you

---

### Post by ActionParsnip on 2022-04-06
Look in the CUPS config page ([http://localhost:631](http://localhost:631))
Is the old printer there? If so, delete it

---

### Post by Paddy Landau on 2022-04-06
> **ActionParsnip said:**
> Look in the CUPS config page ([http://localhost:631](http://localhost:631))
Is the old printer there? If so, delete it
Thanks for the reply. I didn't know about the CUPS page.

It shows only one printer, the correct one. The old one isn't there.

I'm using the snap version of LibreOffice. Do you think that it makes a difference?

---

### Post by Paddy Landau on 2022-04-06
I have searched the configuration folder in LibreOffice. I have found that the old printer is mentioned in two different places. I might have copied the configuration over from my old computer.

[LIST]
[*][FONT=courier new].config/libreoffice/4/user/registrymodifications.xcu
[/FONT]This holds the old printer as the last printer used.
[*][FONT=courier new].config/libreoffice/4/user/psprint/psprint.conf[/FONT]
This holds two things: Global settings > don't disable CUPS, and the old printer.
[/LIST]
I deleted the old printer from psprint.conf, which means that LibreOffice no longer offers me any printer at all (well, it offers "Generic Printer" and "Print to File", but those don't count). I tried setting CUPS to disabled, but that didn't help.

So, I now have a situation where LibreOffice has stopped showing me the wrong printer, but it's still not showing me the right printer.

I've been through the LibreOffice settings, and I don't find anything that can help me.

Why isn't LibreOffice using the printer that's already set up on my system? (I can print to the correct printer from a different app, e.g. Document Viewer.)

---

### Post by #&amp;thj^% on 2022-04-06
Paddy *if and only *if LibreOffice is a snap package (you don't mention)
try:
```
snap connect libreoffice:cups-control :cups-control
```
EDIT: ah ha you do mention the snap version.

---

### Post by Paddy Landau on 2022-04-06
> **1fallen said:**
> ```
snap connect libreoffice:cups-control :cups-control
```
I did it, and no difference.

I tried again, and restarted the computer.

Sadly, no difference :(

I'm going to try installing the PPA version directly from the LibreOffice website. I'll report back here whether or not it works.

---

### Post by #&amp;thj^% on 2022-04-06
> **Paddy Landau said:**
> I did it, and no difference.

I tried again, and restarted the computer.

Sadly, no difference :(

I'm going to try installing the PPA version directly from the LibreOffice website. I'll report back here whether or not it works.

Thanks Paddy, there was a bug submitted in 2017 about the "auto-connect" not being active, but not enough votes or interest so here we sit.
EDIT: found it: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1711186](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1711186)

---

### Post by Paddy Landau on 2022-04-06
> **1fallen said:**
> EDIT: found it: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1711186](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1711186)
According to the linked Snapcraft request, this has been enabled.

It doesn't work for me :(

I've installed the PPA version from the LibreOffice website, and it works!

So, I've copied across my configuration (there's a lot of tailored stuff including macros), and uninstalled the snap version.

From now on, I'll use the PPA version. Maybe at some point I'll try out the flatpak version.

Now we know that the snap version — for me, at any rate — doesn't see the system printers.

Thank you for your time!

---

### Post by #&amp;thj^% on 2022-04-06
> **Paddy Landau said:**
> 

Now we know that the snap version — for me, at any rate — doesn't see the system printers.

Thank you for your time!
It was same for me, and Thanks for your participation.

---


---
title: "LibreOffice won't start [undefined symbol: _ZN11LanguageTagD1Ev]"
date: 2020-06-17
forum: General Help
---

### Post by rhyshowitt on 2020-06-17
Hi, my LibreOffice Writer suddenly stopped working despite no changes to the system.  I was using some very old MS Word documents so maybe I've confused it.  I've had a go at removing LibreOffice and reinstalling without success.
From looking at places like UbuntuForums, I gather it might be a config or java problem.
Log includes:
Jun 18 06:03:59 rhys-CQ1151AN gnome-software-service.desktop[2084]: Warning: failed to read path from javaldx
Jun 18 06:04:00 rhys-CQ1151AN gnome-software-service.desktop[2084]: /usr/lib/libreoffice/program/soffice.bin: symbol lookup error: /usr/lib/libreoffice/program/libmergedlo.so: undefined symbol: _ZN11LanguageTagD1Ev
Jun 18 06:05:06 rhys-CQ1151AN systemd-resolved[602]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.

Any ideas?  I'm using 18.04.  I can use the terminal but please spell out the commands as I'm rusty on linux terminology.

Thanks,
Rhys

---

### Post by Holger_Gehrke on 2020-06-18
Try and start LibreOffice Writer from the command line with 'lowriter'. This probably won't work either, but you'll get an error message which should lead you to the problem responsible for the failure.

The three messages from the logs are probably unrelated. You only need Java if you're executing macros for LO that are written in Java (you can write macros for LO in any language that has bindings for LO's libraries; there are some wizards included with LO that use Java which won't work without it, but otherwise it works just fine), according to objdump the undefined symbol is a dynamic symbol so it should either get defined at runtime or get imported from another library and the third message is not about LO at all but about name resolution in the network.

Uninstalling and reinstalling a program will not remove or reset the user specific configuration since the package manager never touches files in users' home directories. Your configuration for LibreOffice should be in $HOME/.config/libreoffice. Renaming that directory to something else should make LO create a new configuration.

Holger

---

### Post by rhyshowitt on 2020-06-18
Thanks Holger.  Actually I kept googling and muddled through (using forums and google) to an answer.  I'm not quite sure what I did, but it included reinstalling uno-libs3 from Synaptic and then reinstalling libreoffice from Synaptic.

---


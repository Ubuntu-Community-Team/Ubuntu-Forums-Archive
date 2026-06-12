---
title: "Clicking on a link opens the Muon package manager to install firefox"
date: 2013-05-01
forum: General Help
---

### Post by manolomanolo on 2013-05-01
Hi to all,

I'm not able to launch firefox except when loading it by command line.
If instead I try and open a link on Thunderbird or try to click on the firefox fast launcher on the panel or search for Firefox through the K menu (see attached picture) then the only thing I get is directly launching Muon package manager which in turn opens on a page related to Firefox and related components. 

Actually it seems that despite firefox is installed the system still behaves just like firefox is not installed since, except for the command line, all the rest seems to refer to Mozilla Firefox Browser Installer.

I tried to reinstall firefox, but nothing changed.
I tried to disable all FF the components shown in Muon, but nothing changed.
I tried to look for somethin related to file association in the setting menu, but it seems to be ok (there's a file association related to "firefox" command and not to any installation package).

What should I do?
Thanks,
regards.

---

### Post by oldos2er on 2013-05-01
Can you run the following command, and copy & paste its output here? ```
apt-cache policy firefox
```

---

### Post by manolomanolo on 2013-05-02
Thanks for your reply.

I solved the problem uninstalling and reinstalling Firefox through Muon.
However, I did not reinstall also all the related packages as suggested for Firefox by Muon. Hope the problem will not arise anymore in case of reinstalling those.

In conclusion, i run your command and that's the result:
```
apt-cache policy firefox
firefox:
  Installato: 20.0+build1-0ubuntu2
  Candidato:  20.0+build1-0ubuntu2
  Tabella versione:
 *** 20.0+build1-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status

```

---


---
title: "Acme -installation problems"
date: 2022-02-03
forum: General Help
---

### Post by ligustri on 2022-02-03
[COLOR=#000000][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Reinstallation of acme (multi-platform crossassembler) failed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]First I installed this package:[/FONT][/COLOR]

[https://launchpad.net/ubuntu/+...rig.tar.xz]("https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/acme/1:0.97~svn20201116+ds-1/acme_0.97~svn20201116+ds.orig.tar.xz")[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]..and it was wrong for my Ubuntu![/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]During the installation I chose to do the 'make install' before the 'make'. Maybe this messed the installation, I've no idea.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]After this I removed folder where I did the wrong version extraction and tried to install right version for my Ubuntu from here:[/FONT][/COLOR]
[https://launchpad.net/ubuntu/+...rig.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/acme/1:0.96.4-5/acme_0.96.4.orig.tar.gz")[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]This time 'make' and 'make install' in correct order.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]But it didn't help.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Terminal don't recognize acme -command.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Should I remove toacme folder from /usr/local/bin -folder and then do reinstallation? Would it help? Or what would?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please, help![/FONT][/COLOR]

---

### Post by dragonfly41 on 2022-02-04
Perhaps try this download .deb
[https://launchpad.net/ubuntu/impish/amd64/acme/1:0.97~svn20201116+ds-1](https://launchpad.net/ubuntu/impish/amd64/acme/1:0.97~svn20201116+ds-1)

---


---
title: "Getting rid of program"
date: 2020-08-31
forum: General Help
---

### Post by Panawe on 2020-08-31
Hi,

I installed a screenwriting software program called Ghostwriter. Having tried it and other programs out I have opted for another program but I can't seem to be able to uninstall Ghostwriter.

Another suggestions welcome.

TIA

---

### Post by Holger_Gehrke on 2020-08-31
If [this]("https://github.com/wereturtle/ghostwriter") is the ghostwriter you're talking about and you installed it by following the instructions on the linked page, then a simple 'sudo apt remove ghostwriter' in a shell should remove the program. If you also want to get rid of any system-wide configuration files ghostwriter might have set up, you can insert the option '--purge' after 'remove'. To also remove the PPA from which ghostwriter was installed from the list of sources for software, you can run 'sudo add-apt-repository --remove ppa:wereturtle/ppa'.

If it's some other program or you installed it in a different way, then the way to remove it depends on that and you should tell us how you did it.

Holger

---

### Post by Panawe on 2020-08-31
Many thanks, looks like that's done the job.

:)

---


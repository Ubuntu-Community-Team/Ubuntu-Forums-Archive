---
title: "How to restore APT cache with all package dependencies?"
date: 2008-01-15
forum: General Help
---

### Post by Marcelo Ramone on 2008-01-15
I need restore my Apt cache with all installed packages with all dependencies.

Agradezco cualquier sugerencia ya que no se como hacerlo y no tengo los paquetes en la cache!

When I try reinstall any package, Apt don't install the package dependencies because they are installed.

Thanks in Advance,
Marcelo.-

---

### Post by curly_nostrill on 2008-01-16
I'm no guru by any means, but try [COLOR="black"][FONT="Courier New"]sudo apt-get autoremove[/FONT][/COLOR] 

I picked up a little habit a while back with wajig >[FONT="Courier New"] sudo apt-get install wajig[/FONT] it does more than just aptitude but that comes later.  It has many more commands than just plain aptitude or apt-get or synaptic and you can do a lot of things without having to type "sudo apt-get blah blah" every gawl-danged time.

So, " [FONT="Courier New"]sudo apt-get (for the last time) wajig[/FONT] " leave out "(for the last time)".

Then [FONT="Courier New"]wajig update[/FONT] then [FONT="Courier New"]wajig purge *whatever-package-you-removed*[/FONT]

or something... Then whenever you see instructions saying 'apt-get blah blah' substitute wajig for apt-get which normally will be 'sudo apt-get blah'.  You can [FONT="Courier New"]wajig search package [/FONT] without the [FONT="Courier New"]sudo[/FONT] command, etc.  Type [FONT="Courier New"]wajig commands | less[/FONT] for a complete list of input commands or [FONT="Courier New"]man wajig[/FONT]

I'll check in later if you still have probs.

---


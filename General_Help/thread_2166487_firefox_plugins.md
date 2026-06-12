---
title: "firefox plugins?"
date: 2013-08-09
forum: General Help
---

### Post by john8 on 2013-08-09
k so plugins for firefox are stored in /usr/lib/mozilla/plugins but how come putting making an example.so (for example) doesint show up in firefox or crash firefox? is there no way to create extensions or rename extensions that will be reflected in firefox?

i know this means the extension wouldint work but im trying to write my own broser as a project and this has my head wrecked 

where does firefox get its extension data from  its not in
/home/user/.mozilla/firefox/profile extensions.ini so how does firefox know what plugins aree available?? there aint allot of information on firefox forums

thanks any info on how plugins"not addons" are registered in ubunut firefox would be great thanks

---

### Post by pqwoerituytrueiwoq on 2013-08-09
[FONT=courier new]extensions.ini[/FONT] is for addons not plugins
you can also place plugins so files in [FONT=courier new]~/.mozilla/plugins/[/FONT]
i think ff just checks for certain file names in the locations

---

### Post by pqwoerituytrueiwoq on 2013-08-09
duplicate

---

### Post by john8 on 2013-08-10
thanks for reply i tried making a [FONT=courier new]~/.mozilla/plugins/  folder and putting plugins into it but this didint work ff didint read them

and thanks for pointing out extensions.ini is for addons untill yesterday i tought addons and plugins where same thing oops you live you hopefully learn [/FONT]

---


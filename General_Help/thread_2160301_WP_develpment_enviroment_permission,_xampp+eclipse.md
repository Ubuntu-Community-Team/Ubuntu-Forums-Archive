---
title: "WP develpment enviroment permission, xampp+eclipse"
date: 2013-07-06
forum: General Help
---

### Post by jacopo3001 on 2013-07-06
Hi All.
I am trying to setup an enviroment for Wordpress development on ubuntu 12, but I am having troubles with permissions (I am quite new to this).

The last unsolved problem is that I cannot manage to get Eclipse to modify files (permission problem).
 
So, here is what I did:
first, I installed Xampp, using root.
Htdocs results having own:root, group:root.  fine(?).

Then, unpacked WP downloaded from their site.
WP has owner:nobody, group:nogroup. Apache is reading it, so fine...(?)

Then I install Eclipse using software center, and I add various plugins, all fine.

Now, I launch Eclipse and try to modify my WP project. It can't, no permission!
Somebody suggested me to launch eclipse as root (gksu eclipse).
I tried that, but it seems all the plugins are gone this way (they where installed under a different user?).

I need to fix the Eclipse file editing issue, but most of all, I need to understand the whole things: how should this be setup?

thank you so much for reading through this and for the patience of explaining me.

---

### Post by Double.J on 2013-07-06
Hi there, afraid I don't know the answer to why the project is returning a permissions error, however I noticed that you are using ```
 gksu eclipse
``` instead of ```
 gksudo eclipse 
``` if you have enabled the root account on your system it would explain why the plugins are gone?

---

### Post by jacopo3001 on 2013-07-06
tried gksudo and got the same problem:
the PHP project wizard are gone, and if I try to open a PHP file i get this error:
"Could not open the editor: No editor descriptor for id org.eclipse.php.editor"

now, I could try to re-install all plugins using gksudo, i don't mind.
I am just wondering if this is the right way to go.
Is it normal to have to gksudo eclipse in order to work on a web dev project!?

or what is the *manual way*?

---

### Post by jacopo3001 on 2013-07-06
I confirm the plugins where gone when i gksu/gksudo eclipse.
I re-installed them and now I can edit the files.

So:
WP is [COLOR=#000000]has owner:nobody, group:nogroup.
[/COLOR]
Eclipse in order to work (write files within WP) has to be launched as gksu/gksudo.

is this fine? or should I better change something?

---


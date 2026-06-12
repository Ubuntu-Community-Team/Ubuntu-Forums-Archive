---
title: "indicate a route of an archive that contain space"
date: 2015-03-27
forum: General Help
---

### Post by joan_carles2 on 2015-03-27
I'm working to configure the templates folder in kubuntu.

To do that I must indicate the URI of the template. And the problem is that I don't know how to do it because the URI contain and archive with space

The URI that I must indicate is this one

URI=/home/joan/Plantillas/contract sale.odt

I've tried

URI="/home/joan/Plantillas/contract sale.odt"

URI=/home/joan/Plantillas/'contract sale.odt'


And many other combinations. How I can indicate the URI of an archiuve than contain space?

---

### Post by ajgreeny on 2015-03-27
Where is it that you must indicate the URI of the template and which templates folder are you talking about?  Is this the **/home/*username*/Templates** folder that seems to be a default folder in all user's homes, or is this related to templates for Libreoffice?   If for LO you need to look at [B]~/.config/libreoffice/4/user/template/ folder.
[/B]
I do not know KDE any more so if it is specific to KDE I don't understand where or why you need to use the syntax of URI=/home/joan/Plantillas/contract sale.odt

---

### Post by joan_carles2 on 2015-03-27
To include more templates must be done editing an archive.desktop to next location

~/.kde/share/templates/

This is the way to do it an inside this archive you must indicate the location of the file that you want to use as a template. I can't indicate the URI because of the problem that I detail in the first comment.

---

### Post by steeldriver on 2015-03-27
I haven't played with KDE in a while and can't test it, but given that it seems to be expecting a URI type syntax you could try replacing the space by an HTML-encoded space i.e. %20

```

URI=/home/joan/Plantillas/contract%20sale.odt

```

---


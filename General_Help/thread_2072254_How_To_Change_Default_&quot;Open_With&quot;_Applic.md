---
title: "How To Change Default &quot;Open With&quot; Application Globally?"
date: 2012-10-17
forum: General Help
---

### Post by Kirk Schnable on 2012-10-17
I am trying to change the "default Open With application" for PDF files on a Ubuntu 10.04 machine.  

I'm troubleshooting another issue, and I want to replace Evince with Adobe Reader as the default application to open PDF files.

Apparently, removing the "evince" package results in the removal of the "ubuntu-desktop" metapackage, so that's not an option.

After installing Adobe and asking it to be the default PDF reader, PDF files still open in Evince. 

I've checked these files:
/etc/gnome/defaults.list
/usr/share/applications/defaults.list

They both indicate that Adobe Reader should be launching the PDF files.

I need to be able to do this at a large scale, so modifying a file or running a CLI command is preferred.  Using the right-click context menu to set the default program is not an option due to the amount of machines this will be deployed on.

I appreciate any input you might have!

Thanks,
Kirk Schnable

---

### Post by Kirk Schnable on 2012-10-17
My coworker found this:
[http://unix.stackexchange.com/questions/41372/changing-file-associations-in-gnome](http://unix.stackexchange.com/questions/41372/changing-file-associations-in-gnome)

It turns out there's user-specific MIME application defaults lists, which I figured might be the problem...

We had to change the info in:
$HOME/.local/share/applications/defaults.list
$HOME/.local/share/applications/mimeapps.list

In my case, I am going to remove the file entirely and it seems to resolve the problem.

Kirk Schnable

---


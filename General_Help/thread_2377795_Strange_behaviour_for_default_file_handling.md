---
title: "Strange behaviour for default file handling"
date: 2017-11-16
forum: General Help
---

### Post by ktat on 2017-11-16
Hi,

I am running a piece of software called [Vym]("http://www.insilmaril.de/vym/"), files saved with this software have the extension .vym.

The default application for opening is the Archive Manager and the file icon is the little box.  This is incorrect, so I changed my preference for opening .vym files to the Vym software.

Now I have a new problem, Ubuntu tries to open all my zipped files with Vym!

I have no idea why this is happening as they have different extensions, why would they be getting lumped together??  And, how do I fix?

Thank you.

---

### Post by mc4man on 2017-11-16
It's being seen as a zip archive so if you change the default for that mimetype it sets the new default for all zip files (Zip archive (application/zip)

You could set a new mimetype for .vym, what I'm clueless but possibly it doesn't really matter..?

Ex. - 
In ~/.local/share/mime/packages create a new file named 
user-extension-vym.xml

Put this in it (or put something like this if you don't want to use text/..
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="text/x-vym">
        <comment xml:lang="en">vym file</comment>
        <glob pattern="*.vym" />
    </mime-type>
</mime-info>
```

Then run this - 
```
update-mime-database -V ~/.local/share/mime/
```

Your .vym file icons should now look like a blank text file with no set app association  so you can open it from context menu with vym & it'll be the default for such files..

---

### Post by ktat on 2017-11-17
Thank you,  I tried your solution - double clicking on *.vym file now gives this result:

```
could not display "*.vym"
There is no application installed for "vym file" files.
```

Also, when I open up the file permissions the "opens with" tab has disappeared.  So there is no option to select the default software for opening the file.

---

### Post by mc4man on 2017-11-18
> **ktat said:**
> Thank you,  I tried your solution - double clicking on *.vym file now gives this result:

```
could not display "*.vym"
There is no application installed for "vym file" files.
```

Also, when I open up the file permissions the "opens with" tab has disappeared.  So there is no option to select the default software for opening the file.
Well then you have issues superseding any of this..

(- if this is a 17.04 > 17.10 upgrade things don't always work out well..

---


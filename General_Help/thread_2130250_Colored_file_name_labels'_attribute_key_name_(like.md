---
title: "Colored file name labels' attribute key name (like Mac OSX Finder color labels)"
date: 2013-03-28
forum: General Help
---

### Post by OrangeVixen on 2013-03-28
Does anyone know if there is a standard setting (such as in gio/gvfs attributes) to set/store color label attributes for individual objects/files/directories/links/etc similar to how it is done on Mac OSX Finder?

I'm writing an app that currently uses gio to set a color attribute on individual files but I'm not sure what the key name for that attribute should be. I'm using "metadata::color-name" for now and the value would be "red" or "blue" for example.

I scowered the net and found a few references to Marlin (alt for Nautilus file manager) to set color labels but it does not specify what attribute key name it uses.

Does anyone know of a standard key name?

Edit: here are some other ideas I was thinking of for key names:

"metadata::label-color-name"
"metadata::text-color-name"

I wanted to add the "-name" at the end so it's know that it's a color spec name like "red" or "blue" instead of a hexidecimal value like "#ff0000"

---


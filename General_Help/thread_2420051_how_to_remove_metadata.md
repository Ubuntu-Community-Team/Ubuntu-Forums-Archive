---
title: "how to remove metadata::"
date: 2019-05-29
forum: General Help
---

### Post by csynt on 2019-05-29
Thx to a crap googledrive sync app I have files that are tagged with a sync/no-sync emblem.
Now I am trying to figure out how to remove that  "metadata::emblems: [synchronizing]" on the icons.

oh well, "gio"'s  man page is crap as well...

thx

---

### Post by #&amp;thj^% on 2019-05-29
Well with all this crap I'll give you a couple of choices. :p

Yes, there is a tool to remove metadata called **"exiv2"**.[http://manpages.ubuntu.com/manpages/disco/en/man1/exiv2.1.html](http://manpages.ubuntu.com/manpages/disco/en/man1/exiv2.1.html)
Usage: 
```
exiv2 rm /path/to/location/files
```
And:
> 

    [list]The Metadata Extract Tool includes a number of 'adapters' that extract metadata from specific file types. Extractors are currently provided for:

        [*]Images: BMP, GIF, JPEG and TIFF.
        [*]Office documents: MS Word (version 2, 6), Word Perfect, Open Office (version 1), MS Works, MS Excel, MS PowerPoint, and PDF.
        [*]Audio and Video: WAV, MP3 (normal and with ID3Tags), BFW, FLAC.
        [*]Markup languages: HTML and XML.
        [*]Internet files: ARC
[/list]
    If a file type is unknown the tool applies a generic adapter, which extracts data that the host system 'knows' about any given file (such as size, file name, and date created).

For more information, and to download visit Metadata Extraction Tool see:[http://meta-extractor.sourceforge.net/](http://meta-extractor.sourceforge.net/)

---

### Post by csynt on 2019-06-01
thanks! [COLOR=#000000][FONT=&quot]exiv2 did the trick nicely![/FONT][/COLOR]

---


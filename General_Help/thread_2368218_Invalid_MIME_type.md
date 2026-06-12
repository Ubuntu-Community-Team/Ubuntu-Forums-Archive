---
title: "Invalid MIME type"
date: 2017-08-08
forum: General Help
---

### Post by Do$ on 2017-08-08
Hi.
I'm using Ubuntu 16.04 and trying to install via ssh TeamViewer program and I'm getting error:
Error in file "/usr/share/applications/evince.desktop": "" is an invalid MIME type ("" does not contain a subtype)
Error in file "/usr/share/applications/evince-previewer.desktop": "" is an invalid MIME type ("" does not contain a subtype)

Here is the listing of evince.desktop:
```

[Desktop Entry]
[Desktop Entry]
Name=Document Viewer
Comment=View multi-page documents
Keywords=pdf;ps;postscript;dvi;xps;djvu;tiff;document;presentation;
TryExec=evince
Exec=evince %U
StartupNotify=true
Terminal=false
Type=Application
Icon=evince
X-GNOME-DocPath=
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=evince
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.18.2
Categories=GNOME;GTK;Office;Viewer;Graphics;2DGraphics;VectorGraphics;
MimeType=application/pdf;application/x-bzpdf;application/x-gzpdf;application/x-xzpdf;application/x-ext-pdf;application/postscript;application/x-bzpostscript;application/x-gzpostscript;image/x-eps;image/x-bzeps;image/x-gzeps;application/x-ext-ps;application/x-ext-eps;application/x-dvi;application/x-bzdvi;application/x-gzdvi;application/x-ext-dvi;image/vnd.djvu;application/x-ext-djv;application/x-ext-djvu;image/tiff;application/x-cbr;application/x-cbz;application/x-cb7;application/x-ext-cbr;application/x-ext-cbz;application/x-ext-cb7;;application/oxps;application/vnd.ms-xpsdocument;
X-Ubuntu-Gettext-Domain=evince





```

Here is the listing of evience-previewer.desktop:
```

[Desktop Entry]
Name=Print Preview
Comment=Preview before printing
TryExec=evince-previewer
Exec=evince-previewer %U
StartupNotify=true
Terminal=false
Type=Application
Icon=document-print-preview
NoDisplay=true
X-GNOME-DocPath=
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=evince
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.18.2
Categories=GNOME;GTK;Office;Viewer;Graphics;2DGraphics;VectorGraphics;
MimeType=application/pdf;application/x-bzpdf;application/x-gzpdf;application/x-xzpdf;application/x-ext-pdf;application/postscript;application/x-bzpostscript;application/x-gzpostscript;image/x-eps;image/x-bzeps;image/x-gzeps;application/x-ext-ps;application/x-ext-eps;application/x-dvi;application/x-bzdvi;application/x-gzdvi;application/x-ext-dvi;image/vnd.djvu;application/x-ext-djv;application/x-ext-djvu;image/tiff;application/x-cbr;application/x-cbz;application/x-cb7;application/x-ext-cbr;application/x-ext-cbz;application/x-ext-cb7;;application/oxps;application/vnd.ms-xpsdocument;
X-Ubuntu-Gettext-Domain=evince



```


I don't see something strange. Please help.

---

### Post by jeremy31 on 2017-08-08
There are two semicolons in x-ext-cb7;;application in both files.  Chances are that if one semicolon was removed the issue would be fixed

---

### Post by portam on 2017-09-04
Managed to solve? I have the same error.

---

### Post by dan-j on 2017-09-17
> **jeremy31 said:**
> There are two semicolons in x-ext-cb7;;application in both files.  Chances are that if one semicolon was removed the issue would be fixed

Thank you!  This fixed it for me!

---


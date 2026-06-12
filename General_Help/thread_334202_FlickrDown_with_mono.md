---
title: "FlickrDown with mono"
date: 2007-01-08
forum: General Help
---

### Post by pjman on 2007-01-08
I'm having trouble getting a neat tool called [FlickrDown]("http://blog.greggman.com/pages/flickrdown.htm") to work with mono. I'm getting the following error:

```


** (FlickrDown.exe:11036): WARNING **: The following assembly referenced from /home/username/.wine/drive_c/Program Files/FlickrDown/FlickrDown.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=2)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/username/.wine/drive_c/Program Files/FlickrDown/).


** (FlickrDown.exe:11036): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (FlickrDown.exe:11036): WARNING **: Missing method EnableVisualStyles in assembly /home/username/.wine/drive_c/Program Files/FlickrDown/FlickrDown.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.


```

Is there anything I can do to get it to work in Ubuntu?

---


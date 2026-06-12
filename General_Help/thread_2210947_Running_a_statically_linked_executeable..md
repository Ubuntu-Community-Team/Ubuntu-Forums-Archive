---
title: "Running a statically linked executeable."
date: 2014-03-13
forum: General Help
---

### Post by deamon_knight on 2014-03-13
I'm trying to run Free:AC on Lubuntu. I've made a .desktop file for this purpose but it does not launch. I'm able to launch the executeable from the file manager and from the terminal in that directory. Launching from the terminal in another directory fails with the error:
```
error while loading shared libraries: libsmooth-0.8.72.so.0: cannot open shared object file: No such file or directory

```
I suspect I need to define the directory the executeable needs to run from in the freac.desktop file I've made, but i don't know how to do this, or if it is possible.

Here is an example of my freac.desktop file
```

[Desktop Entry]
Type=Application
Icon=/home/{USER}/freac-20140223/icons/freac.png
Name=Free:AC
Comment=Audio Converter
Categories=AudioVideo
Exec=/home/{USER}/freac-20140223/freac %U
StartupNotify=true
Terminal=false

```

any suggestions on how to do this?

Thanks

---

### Post by steeldriver on 2014-03-13
:confused: did you mean for your title to be "Running a **dynamically **linked executable"? afaik you wouldn't be getting shared library errors if it was statically linked

If the required library is in /home/*user*/freac-20140223/ you could try using env to set a LD_LIBRARY_PATH

```

Exec=/usr/bin/env LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/home/*user*/freac-20140223/ /home/*user*/freac-20140223/freac %U

```

or you could do essentially the same with a wrapper script e.g. put something like

```

#!/bin/bash

LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/home/*user*/freac-20140223/ /home/*user*/freac-20140223/freac "$1"

```

or

```

#!/bin/bash

export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/home/*user*/freac-20140223/ 

/home/*user*/freac-20140223/freac "$1"

```

in your ~/bin dir and call *that* from the .desktop file

---

### Post by stevenswall on 2014-04-02
^So, I tried to follow the advice given above, and made a .sh file. I made it executable, put it on my desktop, and it has the following contents:

-----
#!/bin/bash


LD_LIBRARY_PATH=${/opt/freac-20140223/}:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"
-----

I have also tried this one without the brackets:

-----
#!/bin/bash


LD_LIBRARY_PATH=$/opt/freac-20140223/:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"
-----

When I try to run it from the terminal with "~/Desktop/Freac.sh" it returns this:

-----
/home/USER/Desktop/Freac.sh: line 3: ${/opt/freac-20140223/}:/opt/freac-20140223/: bad substitution
-----

So far, I've tried making a Freac.desktop file in /usr/share/applications, but I notice that this doesn't work, and the I can only execute the program by clicking on the freac file that doesn't have an extension. Additionally, I notice that many .desktop files are linked to execute bin files in a different directory.

Does anyone have any additional ideas?

(Also tried: Manage Launcher, and Create Launcher, from Ubuntu Software Center. The created launchers do not work.)

Fre:ac was downloaded from this link:

<http://sourceforge.net/projects/bonkenc/files/snapshots/20140223/freac-20140223-linux-x64.tar.gz/download>

---

### Post by steeldriver on 2014-04-02
> **stevenswall said:**
> 
LD_LIBRARY_PATH=${[COLOR=#ff0000]**/opt/freac-20140223/**[/COLOR]}:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"

LD_LIBRARY_PATH=[COLOR=#ff0000]**$**[/COLOR]/opt/freac-20140223/:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"

/home/USER/Desktop/Freac.sh: line 3: ${/opt/freac-20140223/}:/opt/freac-20140223/: bad substitution


Both of these are incorrect - don't substitute the LD_LIBRARY_PATH with anything, that's what the command is for. The idea is that [COLOR=#0000ff]**${LD_LIBRARY_PATH}**[/COLOR] expands to the current value of the variable, then [COLOR=#0000ff]**:/path/to/somewhere/**[/COLOR] appends your additional library path.

The two forms that should work are

```

LD_LIBRARY_PATH=[COLOR=#0000ff]**${LD_LIBRARY_PATH}**[/COLOR]:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"

```
or
```

LD_LIBRARY_PATH=[COLOR=#0000ff]**LD_LIBRARY_PATH**[/COLOR]:/opt/freac-20140223/ /opt/freac-20140223/freac "$1"

```

although if you're putting it in a separate shell script I'd suggest **exporting **the variable

```

export LD_LIBRARY_PATH=[COLOR=#0000ff]**${LD_LIBRARY_PATH}**[/COLOR]:/opt/freac-20140223/

/opt/freac-20140223/freac "$1"

```
or
```

export LD_LIBRARY_PATH=[COLOR=#0000ff]**LD_LIBRARY_PATH**[/COLOR]:/opt/freac-20140223/

/opt/freac-20140223/freac "$1"

```

---

### Post by deamon_knight on 2014-04-18
Thanks for the responses guys. I'm still working on this desktop linux thing and confused static with dynamic.

---


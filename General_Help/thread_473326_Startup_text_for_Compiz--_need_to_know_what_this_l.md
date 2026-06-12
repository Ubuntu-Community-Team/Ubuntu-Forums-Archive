---
title: "Startup text for Compiz-- need to know what this line SHOULD be"
date: 2007-06-13
forum: General Help
---

### Post by 213374U on 2007-06-13
If someone could just enter

[HTML]sudo nano /usr/bin/compiz[/HTML]

and tell me what the line towards the end that has

[HTML]$COMPIZ_OPTIONS[/HTML] 

in it says

---

### Post by SendDerek on 2007-06-13
```

#!/bin/sh

GLXINFO='/usr/bin/glxinfo'
EXT_TFP='GLX_EXT_texture_from_pixmap'

COMPIZ_OPTIONS="--no-fbo --ignore-desktop-hints"

# Check whether the GLX_EXT_texture_from_pixmap extension is available in
# direct or indirect rendering contexts. If it is available only in indirect
# rendering contexts, force compiz to use indirect rendering.
#if test `$GLXINFO 2> /dev/null | grep -c $EXT_TFP` -lt 3; then
#	echo "$EXT_TFP is not available with direct rendering."
#
#	export LIBGL_ALWAYS_INDIRECT=1
#	if test `$GLXINFO 2> /dev/null | grep -c $EXT_TFP` -lt 3; then
#		echo "$EXT_TFP is not available with indirect rendering. Aborting!"
#		unset LIBGL_ALWAYS_INDIRECT
#		exit 1
#	else
#		echo "$EXT_TFP is available with indirect rendering."
#	fi
#else
#	echo "$EXT_TFP is available with direct rendering."
#fi

# start the gtk-window-decorator if present
#if [ -x /usr/bin/gtk-window-decorator ]; then
#	/usr/bin/gtk-window-decorator --replace &
#fi

# load the gconf plugin if present
if [ -f /usr/lib/compiz/libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS gconf"
fi

if [ "`pidof Xgl`" ]; then
    if [ -f /usr/lib/nvidia/libGL.so.1.2.xlibmesa ]; then
	LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz.real $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS
    fi

    if [ -f /usr/lib/fglrx/libGL.so.1.2.xlibmesa ]; then
	LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz.real $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS
    fi
fi

# always load the gconf plugin
/usr/bin/compiz.real $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || metacity

```

---


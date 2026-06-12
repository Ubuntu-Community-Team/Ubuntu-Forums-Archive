---
title: "Beryl and Xgl advice"
date: 2006-12-26
forum: General Help
---

### Post by wgscott on 2006-12-26
I'm running Xubuntu Edgy and installed Beryl, which I really like.  I followed instructions to create a file that initiates beryl and xfce4 this way:

```


#!/bin/bash -f
    # Start up Xgl and Xfce
    # Run Xgl server on :1, on top of normal X

Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &

    # Tell subsequent X programs to access the Xgl server at :1

DISPLAY=:1

    # Start Xfce

/usr/bin/beryl-manager
exec xfce4-session


```

This works fine with my account, but all other accounts don't work unless I change both instances of :1 to :0.

In addition, my "super" key (which is the Apple key on my 3rd-party keyboard) only works if I have this use :0.

However, the graphics are a lot slower if I do things this way (which presumably is why the directions have you start it on :1 rather than :0).

Can I simply bypass all of this and use Xgl as my primary X-server.  If so, do I change stuff in /etc/X11/xorg.conf or something like that?  I guess I don't really understand the motivation for doing things this way.

---

### Post by bmhm on 2006-12-27
sAME Superkey problem here, windows keyboard.

---

### Post by FenrisAbraxas on 2006-12-30
Im still trying to get a workaround for this error, right now i know what the problem is, XGL is using the default keymap (and thats pc101 us ) so as soon as you login do this :

```

setxkbmap -model pc105 -layout us -variant basic

```

Adjust to your needs mine is pc105 -layout es -variant basic, and problem solved, but it's annoying to type it everytime i log in :S hope to get a perm solution soon.

Ok got the perm solution a little "untidy" :D in your xgl startup scritp (mine is in /usr/bin/startxgl ) add the setxkbmap like this:

```

#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4
export DISPLAY=:1
/usr/bin/beryl-manager
setxkbmap -model pc105 -layout es -variant basic
exec startkde


```

adjust to your needs, that solved my problem and now im happy :)

Cya

---


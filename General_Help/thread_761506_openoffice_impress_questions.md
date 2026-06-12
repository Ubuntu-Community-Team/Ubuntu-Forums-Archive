---
title: "openoffice impress questions"
date: 2008-04-21
forum: General Help
---

### Post by tanozfood on 2008-04-21
Hello,
I run openoffice impress in a kiosk ubuntu box, and should do some
things:

1. eliminate the pause that occurs after all the slides were displayed
    before restart the loop
2. work in fullscreen at start
3. when another file is updated (by a php page as web), I would
    like to know if there is a way to make openoffice re-read the
    file (signals?)

Thanks,
                   tano

---

### Post by pointone on 2008-04-21
From your description, I assume you're just using it to display a slideshow on the kiosk?

I would suggest using the glslideshow screensaver for XScreenSaver available in the xscreensaver-gl package, instead.

---

### Post by tanozfood on 2008-04-21
Yes, but the file that are uploaded are produced by M$ Powerpoint
from a client. :-(

---

### Post by -Zeus- on 2008-04-21
well then open them in OpenOffice and save then as some other format

---

### Post by tanozfood on 2008-04-21
No, the situation is this:

the linux box run apache and php, and to this box is connected
another machine by wi-fi that run windows xp and produce
powerpoint files. The kiosk must play the slideshow at loop,
until another file is uploaded, than the php script rename it
as the default slideshow, and openoffice must re-read it (or
must be killed and restarted)

---

### Post by -Zeus- on 2008-04-21
This script will check for a new file on the webserver every 2 minutes and if it's different, start openoffice with the new file and continue

```
cd /tmp
while [ true ]
do      wget "location of ppt file" -O ./file.ppt.new
        if [ `diff ./file.ppt ./file.ppt.new` ]
        then    mv file.ppt.new file.ppt 
                killall soffice.bin
                ooffice /tmp/file.ppt&
        fi
        sleep 2m
done
```

---

### Post by tanozfood on 2008-04-21
I am looking for a better solution: doing this in the php script.
There is no need to check every 2 minutes if you know exactly
when the file is changed. I know how to kill openoffice from
php, however I have some difficulties to reopen it (I think
it has to do with the X server)

---


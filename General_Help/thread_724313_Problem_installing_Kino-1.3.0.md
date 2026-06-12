---
title: "Problem installing Kino-1.3.0"
date: 2008-03-14
forum: General Help
---

### Post by cyberfin on 2008-03-14
Hi there folks!

I wonder if anyone could shed some light on this.

I get the below error when installing Kino-1.3.0.

I have succesfully installed Kino 1.1.1, manually. However I'm having issues with exporting and some other features which I was not having in the 1.1.0 version that is in the repos. So I uninstalled and tried 1.3.0.

Anyway, when issuing the command 'sudo make install' I get this:

```
cyberfin@cyberfin-desktop:~/Desktop/kino-1.3.0$ sudo make install
Making install in po
make[1]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/po'
/bin/sh /home/cyberfin/Desktop/kino-1.3.0/install-sh -d /usr/local/share/locale
linguas="ca da sv fr es cs it no nb eu de hu ru fi uk "; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /bin/sh /home/cyberfin/Desktop/kino-1.3.0/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/kino.mo; \
            echo "installing $lang.gmo as $dir/kino.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/kino.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/kino.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/kino.mo.m; \
            echo "installing $lang.gmo.m as $dir/kino.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/kino.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/kino.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/kino.mo
installing da.gmo as /usr/local/share/locale/da/LC_MESSAGES/kino.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/kino.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/kino.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/kino.mo
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/kino.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/kino.mo
installing no.gmo as /usr/local/share/locale/no/LC_MESSAGES/kino.mo
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/kino.mo
installing eu.gmo as /usr/local/share/locale/eu/LC_MESSAGES/kino.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/kino.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/kino.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/kino.mo
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/kino.mo
installing uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/kino.mo
make[1]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/po'
Making install in ffmpeg
make[1]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg'
make                    -C libavutil   all
make[2]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavutil'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavutil'
make                    -C libavcodec  all
make[2]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavcodec'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavcodec'
make                    -C libavformat all
make[2]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavformat'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavformat'
make                    -C libavdevice all
make[2]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavdevice'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libavdevice'
: make       -C libpostproc all
make -C libswscale  all
make[2]: Entering directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libswscale'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg/libswscale'
touch .libs
gcc -L"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libavdevice -L"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libavf                             ormat -L"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libavcodec -L"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libav                             util -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libavcodec -Wl                             ,-rpath-link,"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libavformat -Wl,-rpath-link,"/home/cyberfin/Desktop/kino                             -1.3.0/ffmpeg"/libavutil -Wl,-Bsymbolic -g -L"/home/cyberfin/Desktop/kino-1.3.0/ffmpeg"/libswscale -o ffmpeg_g-k                             ino ffmpeg.o cmdutils.o -lavdevice-kino -lavformat-kino -lavcodec-kino -lavutil-kino -pthread -lm    -lswscale-k                             ino
cp -p ffmpeg_g-kino ffmpeg-kino
strip ffmpeg-kino
install -d "/usr/local/bin"
install -c -m 755 ffmpeg-kino "/usr/local/bin"
install -d "/usr/local/share/man/man1"
install -m 644 doc/ffmpeg-kino.1 "/usr/local/share/man/man1"
install: cannot stat `doc/ffmpeg-kino.1': No such file or directory
make[1]: *** [install-man] Error 1
make[1]: Leaving directory `/home/cyberfin/Desktop/kino-1.3.0/ffmpeg'
make: *** [install-recursive] Error 1
cyberfin@cyberfin-desktop:~/Desktop/kino-1.3.0$
```

Any input, _and I mean any_, is utmost appreciated.

Thank you!

---

### Post by cyberfin on 2008-03-15
Bump?

---

### Post by cyberfin on 2008-03-15
Please?

---

### Post by erben22 on 2008-03-29
Not a pretty solution, but got me rolling as I hit this same issue:

```

user@machine:~/source/kino-1.3.0$ make
user@machine:~/source/kino-1.3.0$ cp src/ffmpeg-kino.1 ffmpeg/doc/
user@machine:~/source/kino-1.3.0$ sudo make install

```

---

### Post by cyberfin on 2008-04-09
Thank you!

I'll try it immediately!

---

### Post by cyberfin on 2008-04-09
It worked!!!!!!!

Thank you ever so much. I was stuck as I was editing our honeymoon video!

---


---
title: "Installed a package from source.. how to uninstall??"
date: 2007-02-19
forum: General Help
---

### Post by billdotson on 2007-02-19
I downloaded avant window navigator 0.1.1 from [http://code.google.com/p/avant-window-navigator/]("http://code.google.com/p/avant-window-navigator/")

and I want to uninstall it.  How do I uninstall a package I installed using ./configure, make, make install?

Thanks

---

### Post by taurus on 2007-02-19
In the same directory where you ran those three commands, you would run

```
sudo make uninstall
```
to uninstall it.

---

### Post by Maestro23 on 2007-02-19
.

---

### Post by rogblake on 2007-02-19
> **billdotson said:**
> How do I uninstall a package I installed using ./configure, make, make install?


If there is no "make uninstall" available you would normally just delete the program's files. Most source packages install under /usr/local.

---

### Post by billdotson on 2007-02-19
I deleted the directory after it was installed..
No!!! :(

---

### Post by taurus on 2007-02-19
Then download the same source and try something like

```
./configure
make 
sudo make uninstall
-or-
sudo make install  <-- it will just install over itself
sudo make uninstall
```

---

### Post by billdotson on 2007-02-20
I got this extemely long # of lines describing how those things did not work.. here is the output.. sorry for the length

sgtmattbaker@sgtmattbaker:~/Desktop/avant-window-navigator-0.1.1$ sudo make install
Making install in src
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'avant-window-navigator' '/usr/local/bin/avant-window-navigator'
/usr/bin/install -c avant-window-navigator /usr/local/bin/avant-window-navigator
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
Making install in data
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
Making install in active
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
make[3]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/avant-window-navigator/active" || mkdir -p -- "/usr/local/share/avant-window-navigator/active"
 /usr/bin/install -c -m 644 'glow.png' '/usr/local/share/avant-window-navigator/active/glow.png'
 /usr/bin/install -c -m 644 'glow2.png' '/usr/local/share/avant-window-navigator/active/glow2.png'
 /usr/bin/install -c -m 644 'glow3.png' '/usr/local/share/avant-window-navigator/active/glow3.png'
 /usr/bin/install -c -m 644 'glow4.png' '/usr/local/share/avant-window-navigator/active/glow4.png'
 /usr/bin/install -c -m 644 'glow5.png' '/usr/local/share/avant-window-navigator/active/glow5.png'
 /usr/bin/install -c -m 644 'glow6.png' '/usr/local/share/avant-window-navigator/active/glow6.png'
 /usr/bin/install -c -m 644 'glow7.png' '/usr/local/share/avant-window-navigator/active/glow7.png'
 /usr/bin/install -c -m 644 'glow8.png' '/usr/local/share/avant-window-navigator/active/glow8.png'
 /usr/bin/install -c -m 644 'glow9.png' '/usr/local/share/avant-window-navigator/active/glow9.png'
make[3]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
make[3]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
make[3]: Nothing to be done for `install-exec-am'.
if [ -z "" ]; then \
                GCONF_CONFIG_SOURCE="" /usr/bin/gconftool-2 --makefile-install-rule  avant-window-navigator.schemas; \
        fi
Attached schema `/schemas/apps/avant-window-navigator/bar/rounded_corners' to key `/apps/avant-window-navigator/bar/rounded_corners'
Installed schema `/schemas/apps/avant-window-navigator/bar/rounded_corners' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/corner_radius' to key `/apps/avant-window-navigator/bar/corner_radius'
Installed schema `/schemas/apps/avant-window-navigator/bar/corner_radius' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/render_pattern' to key `/apps/avant-window-navigator/bar/render_pattern'
Installed schema `/schemas/apps/avant-window-navigator/bar/render_pattern' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/pattern_uri' to key `/apps/avant-window-navigator/bar/pattern_uri'
Installed schema `/schemas/apps/avant-window-navigator/bar/pattern_uri' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/pattern_alpha' to key `/apps/avant-window-navigator/bar/pattern_alpha'
Installed schema `/schemas/apps/avant-window-navigator/bar/pattern_alpha' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/glass_step_1' to key `/apps/avant-window-navigator/bar/glass_step_1'
Installed schema `/schemas/apps/avant-window-navigator/bar/glass_step_1' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/glass_step_2' to key `/apps/avant-window-navigator/bar/glass_step_2'
Installed schema `/schemas/apps/avant-window-navigator/bar/glass_step_2' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/glass_histep_1' to key `/apps/avant-window-navigator/bar/glass_histep_1'
Installed schema `/schemas/apps/avant-window-navigator/bar/glass_histep_1' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/glass_histep_2' to key `/apps/avant-window-navigator/bar/glass_histep_2'
Installed schema `/schemas/apps/avant-window-navigator/bar/glass_histep_2' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/border_color' to key `/apps/avant-window-navigator/bar/border_color'
Installed schema `/schemas/apps/avant-window-navigator/bar/border_color' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/bar/hilight_color' to key `/apps/avant-window-navigator/bar/hilight_color'
Installed schema `/schemas/apps/avant-window-navigator/bar/hilight_color' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/window_manager/show_all_windows' to key `/apps/avant-window-navigator/window_manager/show_all_windows'
Installed schema `/schemas/apps/avant-window-navigator/window_manager/show_all_windows' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/app/active_png' to key `/apps/avant-window-navigator/app/active_png'
Installed schema `/schemas/apps/avant-window-navigator/app/active_png' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/title/text_color' to key `/apps/avant-window-navigator/title/text_color'
Installed schema `/schemas/apps/avant-window-navigator/title/text_color' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/title/shadow_color' to key `/apps/avant-window-navigator/title/shadow_color'
Installed schema `/schemas/apps/avant-window-navigator/title/shadow_color' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/title/italic' to key `/apps/avant-window-navigator/title/italic'
Installed schema `/schemas/apps/avant-window-navigator/title/italic' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/title/bold' to key `/apps/avant-window-navigator/title/bold'
Installed schema `/schemas/apps/avant-window-navigator/title/bold' for locale `C'
Attached schema `/schemas/apps/avant-window-navigator/title/font_size' to key `/apps/avant-window-navigator/title/font_size'
Installed schema `/schemas/apps/avant-window-navigator/title/font_size' for locale `C'
test -z "/usr/local/share/applications" || mkdir -p -- "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'avant-window-navigator.desktop' '/usr/local/share/applications/avant-window-navigator.desktop'
test -z "/usr/local/share/avant-window-navigator" || mkdir -p -- "/usr/local/share/avant-window-navigator"
 /usr/bin/install -c -m 644 'avant-window-navigator.svg' '/usr/local/share/avant-window-navigator/avant-window-navigator.svg'
 /usr/bin/install -c -m 644 'avant-window-navigator-24.png' '/usr/local/share/avant-window-navigator/avant-window-navigator-24.png'
 /usr/bin/install -c -m 644 'avant-window-navigator-48.png' '/usr/local/share/avant-window-navigator/avant-window-navigator-48.png'
test -z "/etc/gconf/schemas" || mkdir -p -- "/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'avant-window-navigator.schemas' '/etc/gconf/schemas/avant-window-navigator.schemas'
make[3]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
Making install in po
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/po'
/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/install-sh -d /usr/local/share/locale
if test -n ""; then \
          linguas=""; \
        else \
          linguas="en_GB"; \
        fi; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/avant-window-navigator.mo; \
            echo "installing $lang.gmo as $dir/avant-window-navigator.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/avant-window-navigator.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/avant-window-navigator.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/avant-window-navigator.mo.m; \
            echo "installing $lang.gmo.m as $dir/avant-window-navigator.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/avant-window-navigator.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/avant-window-navigator.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing en_GB.gmo as /usr/local/share/locale/en_GB/LC_MESSAGES/avant-window-navigator.mo
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/po'
Making install in avant-preferences
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
sed -e "s|\@PKGDATADIR\@|/usr/local/share/avant-window-navigator|g" avant-preferences.in.py > avant-preferences.py
/usr/bin/install -c -m 755 avant-preferences.py /usr/local/bin/avant-preferences
test -z "/usr/local/share/applications" || mkdir -p -- "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'avant-preferences.desktop' '/usr/local/share/applications/avant-preferences.desktop'
test -z "/usr/local/share/avant-window-navigator" || mkdir -p -- "/usr/local/share/avant-window-navigator"
 /usr/bin/install -c -m 644 'window.glade' '/usr/local/share/avant-window-navigator/window.glade'
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'


sgtmattbaker@sgtmattbaker:~/Desktop/avant-window-navigator-0.1.1$ sudo make uninstall
Making uninstall in src
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
 rm -f '/usr/local/bin/avant-window-navigator'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/src'
Making uninstall in data
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
Making uninstall in active
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
 rm -f '/usr/local/share/avant-window-navigator/active/glow.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow2.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow3.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow4.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow5.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow6.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow7.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow8.png'
 rm -f '/usr/local/share/avant-window-navigator/active/glow9.png'
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data/active'
make[2]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
 rm -f '/usr/local/share/applications/avant-window-navigator.desktop'
 rm -f '/usr/local/share/avant-window-navigator/avant-window-navigator.svg'
 rm -f '/usr/local/share/avant-window-navigator/avant-window-navigator-24.png'
 rm -f '/usr/local/share/avant-window-navigator/avant-window-navigator-48.png'
 rm -f '/etc/gconf/schemas/avant-window-navigator.schemas'
make[2]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/data'
Making uninstall in po
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/po'
if test -n ""; then \
          linguas=""; \
        else \
          linguas="en_GB"; \
        fi; \
        for lang in $linguas; do \
          rm -f /usr/local/share/locale/$lang/LC_MESSAGES/avant-window-navigator.mo; \
          rm -f /usr/local/share/locale/$lang/LC_MESSAGES/avant-window-navigator.mo.m; \
        done
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/po'
Making uninstall in avant-preferences
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
 rm -f '/usr/local/share/applications/avant-preferences.desktop'
 rm -f '/usr/local/share/avant-window-navigator/window.glade'
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1/avant-preferences'
make[1]: Entering directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'
make[1]: Nothing to be done for `uninstall-am'.
make[1]: Leaving directory `/home/sgtmattbaker/Desktop/avant-window-navigator-0.1.1'
sgtmattbaker@sgtmattbaker:~/Desktop/avant-window-navigator-0.1.1$

---

### Post by taurus on 2007-02-20
Looks like it's removing avant stuff from your system.  Reboot and see the avant stuff is still on your desktop!

---


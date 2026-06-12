---
title: "need help in gdm3-theme.gresource cusomization"
date: 2020-04-17
forum: General Help
---

### Post by dion-g3 on 2020-04-17
looking for a way to customize my login screeen in ubuntu 20.04 , as far as i know its this file "/etc/alternatives/gdm3-theme.gresource"

i use to be css file where editing is easier but with this gresource file i cant get it to work.

i ry to extract and regenrate the gresource file again but it doesn't work

---

### Post by dion-g3 on 2020-04-17
i used this script to extract the data :

```
#!/bin/sh
gst=gnome-shell-theme.gresource
workdir=./shell-theme

for r in `gresource list $gst`; do
    r=${r#\/org\/gnome\/shell/}
    if [ ! -d $workdir/${r%/*} ]; then
      mkdir -p $workdir/${r%/*}
    fi
done

for r in `gresource list $gst`; do
        gresource extract $gst $r >$workdir/${r#\/org\/gnome\/shell/}
done
```

---

### Post by dion-g3 on 2020-04-17
then i generate gnome-shell-theme.gresource.xml

then i run this command 

```
$ glib-compile-resources gnome-shell-theme.gresource.xml
```

but nothing changed

---


---
title: "Error compiling Kazehakase"
date: 2007-03-04
forum: General Help
---

### Post by raul_ on 2007-03-04
When I try to compile Kazehakase 0.4.4 i get this error:

```

......
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gawk... (cached) mawk
configure: error: no mozilla installation found

```

Although it is, because I have the version in the repositories (a stone age version btw) that has mozilla as a dependency. How can I specify the path? I read the instructions but can't find anything regarding this

---

### Post by The Noble on 2007-03-04
I am having the same errors, but with 4.3, so it isn't the package version. I am guessing it is pointing to the wrong place for mozilla, but I have no clue how to fix it.

---

### Post by Rui Pais on 2007-03-04
hi,
when ./configure outputs that kind of error it means that it looked for some header files (.h) and didn't find it. 
That usually means that they are not available, not that the path for them are not defined. 

On debian based installations the header files are installed with -dev packages. 
In these case just do:

```
sudo apt-get install mozilla-dev
```
;)

---

### Post by raul_ on 2007-03-04
> **Rui Pais said:**
> hi,
when ./configure outputs that kind of error it means that it looked for some header files (.h) and didn't find it. 
That usually means that they are not available, not that the path for them are not defined. 

On debian based installations the header files are installed with -dev packages. 
In these case just do:

```
sudo apt-get install mozilla-dev
```
;)

Yes Rui, thanks. I forgot to post the solution. if i used the flag --with-gecko-engine=firefox , a "firefox-xpcom not installed" error would appear, so a search for xpcom in synaptic lead me to 
the solution.

I dumped kazehakase though. I was hoping that this version would have a lot more improvements. I'll stick with iceweasel for now :)

---

### Post by Rui Pais on 2007-03-04
great :)

i didn't know kazehakase until i reply to this thread.

i made a deb for the latest version and install it, with a lot of curiosity. I'm always looking for a browser faster and lighter then ff or ff-based ones. 

kazehakase is definitely better then dillo, but a little "brute" and ugly. Pages load in a weird way. They takes a lot of time before the rendering of the page and a suddenly it appeared very fast... don't know if i can get used to that.

anyway ff get me addicted of 3 or 4 extensions and i always start to look for it in any other browse i use (precisarei de uma desintoxicação ;) talvez...)

have fun.

---

### Post by raul_ on 2007-03-08
I removed it, and now i'm trying to compile it again. Weirdly enough, now it's a different error. Check this out:

```
$ sudo make
make  all-recursive
make[1]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
Making all in po
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
Making all in src
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
../src/kz-marshalers.list --header --prefix=_kz_marshal > kz-marshalers.h
/bin/bash: ../src/kz-marshalers.list: Permissão negada
make[2]: ** [kz-marshalers.h] Erro 126
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
make: ** [all] Erro 2
raul@osiris:~/Desktop/kazehakase-0.4.4.1$ chmod ugo+x s
src/      stamp-h1  
raul@osiris:~/Desktop/kazehakase-0.4.4.1$ chmod ugo+x src/
raul@osiris:~/Desktop/kazehakase-0.4.4.1$ sudo make
make  all-recursive
make[1]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
Making all in po
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
Making all in src
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
(cd . && \
          include_headers="" && \
          for h in kazehakase.h kz-app.h kz-embed.h kz-embed-event.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h kz-ext-impl.h; do \
            include_headers="${include_headers}#include \"${h}\"\n"; \
          done && \
           \
            --fhead "#include \"kz-enum-types.h\"\n${include_headers}" \
            --fprod "\n/* enumerations from \"@filename@\" */" \
            --vhead "GType\n@enum_name@_get_type (void)\n{\n  static GType etype = 0;\n  if (etype == 0) {\n    static const G@Type@Value values[] = {"        \
            --vprod "      { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
            --vtail "      { 0, NULL, NULL }\n    };\n    etype = g_@type@_register_static (\"@EnumName@\", values);\n  }\n  return etype;\n}\n" \
            kazehakase.h kz-app.h kz-embed.h kz-embed-event.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h kz-ext-impl.h) > tmp-kz-enum-types.c && \
        (cmp -s tmp-kz-enum-types.c kz-enum-types.c || \
          cp tmp-kz-enum-types.c kz-enum-types.c ) && \
        rm -f tmp-kz-enum-types.c && \
        echo timestamp > stamp-kz-enum-types-c
/bin/bash: line 6: --fhead: comando não encontrado
make[2]: ** [stamp-kz-enum-types-c] Erro 127
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
make: ** [all] Erro 2

```

---

### Post by Rui Pais on 2007-03-09
hi,
sorry never saw that before... didn't look like a broken dependency.

How do you remove it previously? maybe some files still there conflicting somehow...

Have you tried to do make clean before recompiling?

---

### Post by raul_ on 2007-03-09
Yeap i checked the dependencies. I removed it by making "make uninstall". Maybe some depedency is broken but for example, if i try to install the .deb file, it says that the dependency "libfontconfig1" is not satisfiable. But i have the latest version in the repositories, so if that wasn't an issue then, i can't understand why it is an issue now. 

I'll just wait for Feisty, with the updated repositories :)

---

### Post by Rui Pais on 2007-03-12
> **raul_ said:**
> Yeap i checked the dependencies. I removed it by making "make uninstall". Maybe some depedency is broken but for example, if i try to install the .deb file, it says that the dependency "libfontconfig1" is not satisfiable. But i have the latest version in the repositories, so if that wasn't an issue then, i can't understand why it is an issue now. 

I'll just wait for Feisty, with the updated repositories :)

sorry, forget to answer :(

i sometimes have problems with the make uninstall. 
It seems that not always clean all files, that can interfere on future recompilations.

I always try first made a deb with checkinstall. Thats much easy to uninstall later, besides appears as an installed packages, so one don't forget all that trial stuff that we install on our systems ;)

check if there are some lost files on /usr/local/lib/kazehakase/ or /usr/local/bin/kazehakaze.

Try too, the:
```
make clean
```
before recompile it, or remove the source folder and get a new fresh one to be shore that all is clean.

hth

---

### Post by raul_ on 2007-03-12
Nope...same thing...:( 

I already think it's weird that i have to change the permissions to kz-marshalers.list...the error is

```


--fhead : command not found


```

definitely a dependency...but which one? i'm running 0.3.8 (the version in the repositories) just fine, and i was able to install 0.4.4.1 some time ago...

---


---
title: "Autocomplete - I want files not directories"
date: 2007-12-14
forum: General Help
---

### Post by farbror_ace on 2007-12-14
I recently installed ee (easy editor) to use as a shell editor.
The problem is that it only autocompletes on directories not files, which is kinda useless for a text editor...

Where do I change this?

F ex. Im stadning in my home folder and it contains the following:

.
..
file.txt
directory

Typing:
x@x:~/$ ee<space><tab>
suggests 'directory' not 'file.txt'.

---

### Post by geraldm on 2007-12-14
autocompletion is specific to the kind of shell being used.
tcsh allows completion when either uppercase or lowercase letters match.
bash requires the exact case of letters to autocomplete.
You did not identify your shell.  dash ? 
You wanted a file beginning with "ee", there was apparently none in the current directory but
a directory was found, so look for a file beginning "ee" in that directory ?
Looks OK so far.

Gerald

---

### Post by farbror_ace on 2007-12-20
Thanks for replying but you misunderstood me.
ee is the command (its a texteditor) just like pico/joe/vi etc.

The problem is that bash only autocompletes directories after ee which is kind of useless.

---

### Post by LaRoza on 2007-12-20
bash does files, what happens if you press:

```

ee /etc/f<tab>

```

(You should get fstab)

---

### Post by stylishpants on 2007-12-20
Actually ee only completes files that have the extensions of populare image formats, for some reason.

```
fhanson@fhanson:~$ grep '\<ee\>' /etc/bash_completion 
complete -f -X '!*.@(gif|jp?(e)g|miff|tif?(f)|pn[gm]|p[bgp]m|bmp|xpm|ico|xwd|tga|pcx|GIF|JP?(E)G|MIFF|TIF?(F)|PN[GM]|P[BGP]M|BMP|XPM|ICO|XWD|TGA|PCX)' ee display
```

You're seeing it complete dir names only because you don't happen to have any files named like that lying around.  This does look like a bug.  Presumably somewhere there is an image viewer program whose executable has the same name.

To fix it, you should add a custom bash completion command just for ee.  Create this file:

     /etc/bash_completion.d/ee

And put this inside it (copied from the entry for 'vim' in /etc/bash_completions)

```
complete -f -X '*.@(o|so|so.!(conf)|a|t@(ar?(.@(Z|gz|bz?(2)))|gz|bz?(2))|rpm|zip|ZIP|gif|GIF|jp?(e)g|JP?(E)G|mp3|MP3|mp?(e)g|MPG|avi|AVI|asf|ASF|ogg|OGG|class|CLASS)' ee

```

This is better than editing /etc/bash_completion directly because that file gets replaced when you upgrade your system.



geraldm:
bash can also complete in a case-insensitive way, it just isn't the default.  To get this behaviour, add this line to your ~/.inputrc:
```
set completion-ignore-case On

```

---

### Post by farbror_ace on 2008-01-08
Thanks that did it :)

---

### Post by dagnabit dang doohickey on 2008-01-08
The ee line in bash_completion is probably intended for Electric Eyes image viewer.

If you like ee (easy editor), another text editor you may be interested in is [aee]("http://mahon.cwx.net/") (advanced easy editor) which also run native in X as xae.

---


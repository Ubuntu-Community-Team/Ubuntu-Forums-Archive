---
title: "Quod LIbet will not run -- ImportError: No module named formats/oggvorbis"
date: 2007-06-18
forum: General Help
---

### Post by brian g on 2007-06-18
```
brian@bertha:~$ quodlibet
Supported formats: mod, mp3, mpc, trueaudio, wav, wavpack, xiph
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 301, in <module>
    main()
  File "/usr/bin/quodlibet", line 33, in main
    library = load_library()
  File "/usr/bin/quodlibet", line 255, in load_library
    lib = library.init(const.LIBRARY)
  File "/usr/share/quodlibet/library/__init__.py", line 38, in init
    library.load(cache_fn, skip=True)
  File "/usr/share/quodlibet/library/_library.py", line 124, in load
    try: items = pickle.load(fileobj)
ImportError: No module named formats/oggvorbis
```

i thought it was supposed to support ogg out of the box
i also notice there is no flac listed under the supported formats.

can someone give me a push?

---

### Post by urukrama on 2007-07-17
I don't know if you still need help with this, but I had the same problem and came accross this thread. You'll need to update python-mutagen by installig a later version, and all should be fine.

---

### Post by brian g on 2007-07-18
to which version exactly?

why can't it just work since they're all in the repository together already anyway

---

### Post by hugmenot on 2007-07-19
Have you ever installed QL by hand, i.e., from scripts? Then yes, there could be files gone lying around. If not, it's perhaps a packaging bug.

EDIT: I have packages here: [http://ubuntuforums.org/showpost.php?p=2596985&postcount=201](http://ubuntuforums.org/showpost.php?p=2596985&postcount=201)

---

### Post by brian g on 2007-07-19
I'm installing everything straight out of the ubuntu repositories.

---

### Post by brian g on 2007-08-30
removing the .quodlibet folder from my home got it running

---


---
title: "Cannot open alsamixer"
date: 2016-02-18
forum: General Help
---

### Post by sascha7 on 2016-02-18
Hey all,

I just installed alsa-base and alsa-utils. The command *alsamixergui* opens a window but the mixer looks incredibly rudimentary (just a volume control for Master and Capture) and nothing like the previews. The command *alsamixer* does not work.

When I look for the directory it gives 
    ```

    $ which alsamixer
    /usr/bin/alsamixer
   
```

When I try accessing it:
```

    $ /usr/bin/alsamixer
    cannot open mixer: No such file or directory

```

Also:

```
$ ls -l /usr/bin/alsamixer 
-rwxr-xr-x 1 root root 65456 Jan 17  2014 /usr/bin/alsamixer

```

I already tried editing the .conf-file like [here]("https://justus.berlin/2015/05/no-sound-on-ubuntu-linux-cannot-open-mixer-no-such-file-or-directory-solved/") but that didn't change anything.

So... any help is highly appreciated.

**EDIT: **I solved it. Had to add myself to the audio group via 

```

sudo addgroup <username> audio
```

---


---
title: "apt broken by packages from the repositories!"
date: 2013-05-27
forum: General Help
---

### Post by tornadof3 on 2013-05-27
Hello

I tried installing a Nintendo 64 emulator using the software centre. The mupen64plus-ui-console package installed OK, but didn't appear to do anything. Then I tried installing other similar titled mupen64plus- packages via the software centre. These installs appear to have failed but are clogging up apt so that nothing else will install either. I have followed several tutorials about running sudo apt-get clean etc and also sudo apt-get -f install but my APT is broken! Here is an example of the error:

```
$ sudo apt-get upgrade all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 mupen64plus-audio-sdl : Depends: mupen64plus-audio-abi-2
                         Depends: mupen64plus-config-abi-2.2
 mupen64plus-input-sdl : Depends: mupen64plus-config-abi-2.2
                         Depends: mupen64plus-input-abi-2
 mupen64plus-rsp-hle : Depends: mupen64plus-rsp-abi-2
 mupen64plus-rsp-z64 : Depends: mupen64plus-rsp-abi-2
 mupen64plus-ui-console : Depends: mupen64plus-config-abi-2.2
                          Depends: mupen64plus-frontend-abi-2.0.1
 mupen64plus-video-arachnoid : Depends: mupen64plus-config-abi-2.2
                               Depends: mupen64plus-gfx-abi-2.1
                               Depends: mupen64plus-vidext-abi-2
 mupen64plus-video-glide64 : Depends: mupen64plus-config-abi-2.2
                             Depends: mupen64plus-gfx-abi-2.1
                             Depends: mupen64plus-vidext-abi-2
 mupen64plus-video-rice : Depends: mupen64plus-config-abi-2.2
                          Depends: mupen64plus-gfx-abi-2.1
                          Depends: mupen64plus-vidext-abi-2
 mupen64plus-video-z64 : Depends: mupen64plus-config-abi-2.2
                         Depends: mupen64plus-gfx-abi-2.1
                         Depends: mupen64plus-vidext-abi-2
E: Unmet dependencies. Try using -f.

```

I just want to nuke these irritating packages so I can get my system back. Any ideas?!!

---

### Post by tornadof3 on 2013-05-27
I fixed this by getting the list of offending packages and then runnig

sudo dpkg --purge packagename

one-by-one (it would not take wildcard characters, which was my previous error).

---


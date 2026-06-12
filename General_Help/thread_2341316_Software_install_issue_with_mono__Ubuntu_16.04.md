---
title: "Software install issue with mono | Ubuntu 16.04"
date: 2016-10-26
forum: General Help
---

### Post by abhi.au9 on 2016-10-26
Hello all,

no matter what software I try to install I get similar error about mono.

I tried several solutions suggested in forums, like purging mono, autoremove, apt-get upgrade, but none worked.

```
abc@abc-l:~$ sudo apt-get install pdfmodReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mono-runtime-common : Depends: mono-gac (= 4.2.1.102+dfsg2-7ubuntu4) but it is not going to be installed
 pdfmod : Depends: mono-runtime (>= 3.0~) but it is not going to be installed
          Depends: libgconf2.0-cil (>= 2.24.0) but it is not going to be installed
          Depends: libglib2.0-cil (>= 2.12.10-1ubuntu1) but it is not going to be installed
          Depends: libgtk2.0-cil (>= 2.12.10-1ubuntu1) but it is not going to be installed
          Depends: libmono-cairo4.0-cil (>= 3.2.1) but it is not going to be installed
          Depends: libmono-corlib4.5-cil (>= 3.2.8) but it is not going to be installed
          Depends: libmono-posix4.0-cil (>= 3.2.3) but it is not going to be installed
          Depends: libmono-system-core4.0-cil (>= 3.2.8) but it is not going to be installed
          Depends: libmono-system-drawing4.0-cil (>= 3.0.6) but it is not going to be installed
          Depends: libmono-system-xml4.0-cil (>= 3.2.1) but it is not going to be installed
          Depends: libmono-system4.0-cil (>= 3.2.8) but it is not going to be installed
          Depends: libmono-i18n-west4.0-cil but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

please suggest.

---


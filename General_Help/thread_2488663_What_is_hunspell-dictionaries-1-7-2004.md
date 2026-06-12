---
title: "What is hunspell-dictionaries-1-7-2004 ?"
date: 2023-07-11
forum: General Help
---

### Post by fury99 on 2023-07-11
Hi,

I was investigating the list of installed snaps on my computer and stumbled upon

hunspell-dictionaries-1-7-2004 added in the Snapstore by "&#26519;&#21338;&#20161;(Buo-ren, Lin) (brlin)"

Where is this coming from? Is this safe? Can I remove it?


Thanks

---

### Post by #&amp;thj^% on 2023-07-11
It's perfectly safe:
```
apt show  hunspell
Package: hunspell
Version: 1.7.2+really1.7.1-2
Priority: optional
Section: universe/text
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 225 kB
Depends: hunspell-en-us | hunspell-dictionary | myspell-dictionary, libc6 (>= 2.34), libgcc-s1 (>= 3.3.1), libhunspell-1.7-0, libncursesw6 (>= 6), libreadline8 (>= 6.0), libstdc++6 (>= 5.2), libtinfo6 (>= 6)
Suggests: unzip
Homepage: https://hunspell.github.io/
Task: ubuntustudio-publishing
Download-Size: 66.9 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: spell checker and morphological analyzer (program)
 Hunspell is a spell checker and morphological analyzer library and program
 designed for languages with rich morphology and complex word compounding or
 character encoding. It is based on MySpell and features an Ispell-like
 terminal interface using Curses library, an Ispell pipe interface and an
 OpenOffice.org UNO module.
 .
 Main features:
  - Unicode support (first 65535 Unicode characters)
  - morphological analysis (in custom item and arrangement style)
  - Max. 65535 affix classes and twofold affix stripping (for agglutinative
    languages, like Azeri, Basque, Estonian, Finnish, Hungarian, Turkish, etc.)
  - Support complex compoundings (for example, Hungarian and German)
  - Support language specific algorithms (for example, handling Azeri
    and Turkish dotted i, or German sharp s)
  - Handling conditional affixes, circumfixes, fogemorphemes,
    forbidden words, pseudoroots and homonyms.
 .
 This package contains the program with the Ispell-like terminal and pipe
 interfaces.

```

---

### Post by fury99 on 2023-07-11
> **1fallen said:**
> It's perfectly safe:
```
apt show  hunspell
Package: hunspell
Version: 1.7.2+really1.7.1-2
Priority: optional
Section: universe/text
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 225 kB
Depends: hunspell-en-us | hunspell-dictionary | myspell-dictionary, libc6 (>= 2.34), libgcc-s1 (>= 3.3.1), libhunspell-1.7-0, libncursesw6 (>= 6), libreadline8 (>= 6.0), libstdc++6 (>= 5.2), libtinfo6 (>= 6)
Suggests: unzip
Homepage: https://hunspell.github.io/
Task: ubuntustudio-publishing
Download-Size: 66.9 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: spell checker and morphological analyzer (program)
 Hunspell is a spell checker and morphological analyzer library and program
 designed for languages with rich morphology and complex word compounding or
 character encoding. It is based on MySpell and features an Ispell-like
 terminal interface using Curses library, an Ispell pipe interface and an
 OpenOffice.org UNO module.
 .
 Main features:
  - Unicode support (first 65535 Unicode characters)
  - morphological analysis (in custom item and arrangement style)
  - Max. 65535 affix classes and twofold affix stripping (for agglutinative
    languages, like Azeri, Basque, Estonian, Finnish, Hungarian, Turkish, etc.)
  - Support complex compoundings (for example, Hungarian and German)
  - Support language specific algorithms (for example, handling Azeri
    and Turkish dotted i, or German sharp s)
  - Handling conditional affixes, circumfixes, fogemorphemes,
    forbidden words, pseudoroots and homonyms.
 .
 This package contains the program with the Ispell-like terminal and pipe
 interfaces.

```

I'm more worried about the snap maintainer as it's not someone official with a checkmark. Also, can you shed some light on how it got installed in the first place? Maybe it was required by some other snap? Also, not fully sure, but your command seems to output info about a package in the regular repositories (I would have no problem with those), whereas I'm worried about the snap and its maintainer.

Thanks

---

### Post by DuckHook on 2023-07-11
> **fury99 said:**
> &#8230;can you shed some light on how it got installed in the first place?
An impossible ask since we don't know what you have installed.
> Maybe it was required by some other snap?
If you are fine letting us know what snaps you have, post results of:
```
snap list
```
> &#8230;I'm worried about the snap and its maintainer&#8230;
A legitimate concern IMO. Let's see what the results of the "list" command reveals.

---

### Post by Holger_Gehrke on 2023-07-12
How about looking at 'snap info hunspell-dictionaries-1-7-2004' ? It says it only contains the dictionaries without any program (that should be easy enough to check ... just look in the relevant subdirectory of /snap where the contents are mountedd) and is meant for other snaps that have hunspell compiled in as a library. That way you don't have to bring along several MB of dictionaries with each snap that could use them. There's also a link in the description to a description of the content-interface for snaps which is what makes this work.

Holger

---


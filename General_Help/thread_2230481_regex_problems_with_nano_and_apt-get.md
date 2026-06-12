---
title: "regex problems with nano and apt-get"
date: 2014-06-19
forum: General Help
---

### Post by luis-rosety on 2014-06-19
I am having error messages from apt-get and nano that seem to come from a general regex library or installation problem.

Example apt-get:
```
[FONT=courier new]$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Invalid regular expression '\.dpkg-[a-z]+$' in configuration option 'Dir::Ignore-Files-Silently' will be ignored.
W: Invalid regular expression '\.dpkg-[a-z]+$' in configuration option 'Dir::Ignore-Files-Silently' will be ignored.
W: Invalid regular expression '\.dpkg-[a-z]+$' in configuration option 'Dir::Ignore-Files-Silently' will be ignored.
W: Invalid regular expression '\.dpkg-[a-z]+$' in configuration option 'Dir::Ignore-Files-Silently' will be ignored.
[/FONT]
```
Example nano:
```
[FONT=courier new]$ nano

Error in /usr/share/nano/c.nanorc on line 4: Bad regex "\<[A-Z_][0-9A-Z_]+\>": Invalid collation character
Error in /usr/share/nano/c.nanorc on line 12: Bad regex "'\\(([0-3]?[0-7]{1,2}))'": Invalid collation character
Error in /usr/share/nano/c.nanorc on line 12: Bad regex "'\\x[0-9A-Fa-f]{1,2}'": Invalid collation character
Error in /usr/share/nano/debian.nanorc on line 7: Bad regex "^deb(-src)? ((http|file|ftp):/[^ ]+|cdrom:\[[^\]]+\]/|cdrom:\[[-a-zA-Z0-9\._\(\) ]+\]/) [^ ]+ .+$": Invalid collation character

Error in /usr/share/nano/debian.nanorc on line 9: Bad regex "^deb(-src)? ((http|file|ftp):/[^ ]+|cdrom:\[[^\]]+\]/|cdrom:\[[-a-zA-Z0-9\._\(\) ]+\]/) [^ ]+": Invalid collation character

Error in /usr/share/nano/debian.nanorc on line 14: Bad regex "cdrom:\[[-a-zA-Z0-9\._\(\) ]+\]/": Invalid collation character
Error in /usr/share/nano/gentoo.nanorc on line 13: Bad regex "\$\{?[a-zA-Z_0-9]+\}?": Invalid collation character

Error in /usr/share/nano/gentoo.nanorc on line 16: Bad regex "\<QA_((TEXTRELS|EXECSTACK|WX_LOAD)(_[a-zA-Z_0-9]+)?|DT_HASH|PRESTRIPPED)\>": Invalid collation character
Error in /usr/share/nano/gentoo.nanorc on line 18: Bad regex "\<use(_(with|enable))?\> [!a-zA-Z0-9_+ -]*": Invalid collation character
Error in /usr/share/nano/gentoo.nanorc on line 42: Bad regex "[[:space:]]+\+?[a-zA-Z0-9_-]+": Invalid collation character
Error in /usr/share/nano/gentoo.nanorc on line 43: Bad regex "[[:space:]]+-[a-zA-Z0-9_-]+": Invalid collation character
Error in /usr/share/nano/php.nanorc on line 9: Bad regex "\<[a-z_]*\(": Invalid collation character
Error in /usr/share/nano/tcl.nanorc on line 14: Bad regex "\$\{?[0-9A-Z_!@#$*?-]+\}?": Invalid collation character
Error in /usr/share/nano/tex.nanorc on line 4: Bad regex "\\.|\\[A-Z]*": Invalid collation character
Error in /usr/share/nano/man.nanorc on line 3: Bad regex "\.[1-9]x?$": Invalid collation character
Error in /usr/share/nano/groff.nanorc on line 9: Bad regex "\\s(\+|\-)?[0-9]": Invalid collation character
Error in /usr/share/nano/groff.nanorc on line 24: Bad regex "\\\\\$[1-9]": Invalid collation character
Error in /usr/share/nano/perl.nanorc on line 4: Bad regex "^#!.*/perl[-0-9._]*": Invalid collation character
[/FONT]
```
Any ideas?
Thanks

---

### Post by slickymaster on 2014-06-19
Hi luis-rosety, welcome to the forums.

I've edit your post, adding the missing code tags. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to make the posts clean, compact and more appealing, thus getting more attention from readers.

---

### Post by luis-rosety on 2014-06-22
Muito obrigado!

---

### Post by bapoumba on 2014-06-22
Anything in your apt.conf ?
```
The Ignore-Files-Silently list can be used to specify which files APT
       should silently ignore while parsing the files in the fragment
       directories. Per default a file which end with .disabled, ~, .bak or
       .dpkg-[a-z]+ is silently ignored. As seen in the last default value
       these patterns can use regular expression syntax.
```

---


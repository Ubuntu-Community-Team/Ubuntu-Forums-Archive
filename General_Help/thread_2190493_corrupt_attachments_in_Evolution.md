---
title: "corrupt attachments in Evolution"
date: 2013-11-27
forum: General Help
---

### Post by jmr59 on 2013-11-27
For various reasons I'm running Evolution on Kubuntu. I'd rather not change this if possible. Large numbers of attachments are arriving apparently corrupt. When trying to open them I receive error messages such as (in Okular)

```
Could not open /home/[username]/.cache/evolution/tmp/evolution-[path-to-temp-directory]/[filename].pdf
```

or (in LibreOffice)

```
The file '[filename].docx' is corrupt and therefore cannot be opened. LibreOffice can try to repair the file.

The corruption could be the result of document manipulation or of structural document damage due to data transmission.

We recommend that you do not trust the content of the repaired document.
Execution of macros is disabled for this document.

Should LibreOffice repair the file?
```

clicking 'no' results in the following:

```
The file '[filename].docx' could not be repaired and therefore cannot be opened.
```

followed by a repetition of the original error message and the question of whether LibreOffice should repair the file.

clicking yes results in

```
The file '$(ARG1)' could not be repaired and therefore cannot be opened.

```
[username], [filename] etc. are my redactions; $(ARG1) is not.

followed by

```
General Error
```

The only other reference I've found to a similar looking problem is [http://ubuntuforums.org/showthread.php?t=2112735](http://ubuntuforums.org/showthread.php?t=2112735), which is unresolved and doesn't provide enough information to be helpful.

I'm running:
Evolution 3.8.4
KDE 4.11.2
Kubuntu 13.10 Saucy

Forwarding emails of which I can't open the attachments results in attachments that the recipient cannot open (and also that I cannot open by any other means).

I can open the same attachments without any problem on the same computer using e.g. a webmail interface. And also using (other versions of) Evolution / KDE on other computers, e.g. one running Evolution 3.2.3 / KDE 4.8.5 / Ubuntu 12.04.

Any help would be much appreciated.

---


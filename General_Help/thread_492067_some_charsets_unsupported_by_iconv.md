---
title: "some charsets unsupported by iconv"
date: 2007-07-04
forum: General Help
---

### Post by edcrfv on 2007-07-04
Some charsets presented on the [libiconv website]("http://www.gnu.org/software/libiconv/") aren't supported. It's the case for most of the mac encodings.

Since my webhost's Debian has the same limitations I wonder if it's meant like that...

Concretely, I'd like to convert some text from MacCentralEurope to UTF-8. I can do it with recode but my webhost only has iconv. I could also do it with the[ ConvertCharset class]("http://mikolajj.republika.pl/") but it's much slower...

---


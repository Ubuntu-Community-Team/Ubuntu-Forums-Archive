---
title: "Problem downloading files"
date: 2014-01-18
forum: General Help
---

### Post by jacatone on 2014-01-18
I'm using Ubuntu 12.04. It seems when ever I try downloading a file, when it completes the download it just says "Failed" and there's no copy of the file anywhere. Anyone know a fix for this? Thanks.

---

### Post by oldos2er on 2014-01-18
What program are you downloading files with? And downloading to where? ~/Downloads/ ?

---

### Post by jacatone on 2014-01-19
Sorry, I should have been more specific. I mean files, I'm downloading through Firefox 24 from various download sites. Programs, videos, etc.

---

### Post by carl4926 on 2014-01-19
I suggest you try a new profile
Close firefox
rename your current .mozilla folder to .mozilla-bak

Try firefox as it is and report back

Or another option, just install another browser such as midori and see how that works

---

### Post by spencer the great on 2014-01-19
If you have the direct link to the file (e.g. [http://foo.com/bar.zip](http://foo.com/bar.zip)), does downloading it with wget or curl work?
```
$ wget http://foo.com/bar.zip
$ curl -L -o bar.zip http://foo.com/bar.zip
```

AND NO, that isn't a real link, just one that I made up.  Don't click on it, because it might actually be a real link with very bad malware. And I forgot to disable url parsing.

---

### Post by jeanjd63 on 2014-01-19
Hello
You can verify if you have some space  free on your disk.
[B]df  -h
df  -i[/B]

---

### Post by Dave_L on 2014-01-19
> **spencer the great said:**
> AND NO, that isn't a real link, just one that I made up.  Don't click on it, because it might actually be a real link with very bad malware. And I forgot to disable url parsing.

There are some "safe" domain names reserved for use as examples or in documentation, such as "example.com".
Reference: [http://tools.ietf.org/rfcmarkup?doc=2606](http://tools.ietf.org/rfcmarkup?doc=2606)

---


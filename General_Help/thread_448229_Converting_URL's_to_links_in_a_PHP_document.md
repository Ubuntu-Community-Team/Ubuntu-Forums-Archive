---
title: "Converting URL's to links in a PHP document"
date: 2007-05-18
forum: General Help
---

### Post by hellomynameisphil on 2007-05-18
I have a php document filled with URL's interspersed with other stuff. I'd like to convert the URL's to links of the form:

```

<a href="URL">URL</a>

```

so that, for example,

```

http://www.anamolousdisturbances.com/

```

becomes:

```

<a href="http://www.anamolousdisturbances.com/">http://www.anamolousdisturbances.com/</a>

```

What is a good way to do this without having to go through the tedious process of doing it manually for each and every URL in the document? I know it will probably entail the use of regular expressions, but I don't know anything about them. 

I imagine it could be done in the shell (perhaps using sed?). Any ideas on that?

Or perhaps, as I'm using the bluefish editor, perhaps there's a way to use find and replace to do this. Could I get some tips on how that would be done?

Thanks in advance for any advice!

---

### Post by bunker on 2007-05-18
PHP itself actually does that kind of stuff quite neatly using PCRE:

```
$ php -r 'echo preg_replace("/http:\/\/[^\s]*/", "<a href=\"\\0\">\\0</a>", file_get_contents("oldfile"));' > newfile
```

(Though I'm sure sed would be just as good, and you could run it on more than one file at a time)

You might want to try something like /(http:\/\/|[www.)](www.))[^\s]*/ as the pattern if they don't all have http:// in front of them.

---

### Post by bashologist on 2007-05-18
This might work in some cases:
```
sed -n 's/.*\(http[^" ]*\).*/\1/p' filename.php | while read line; do echo "<a href=\"$line\">$line</a>"; done
```

---


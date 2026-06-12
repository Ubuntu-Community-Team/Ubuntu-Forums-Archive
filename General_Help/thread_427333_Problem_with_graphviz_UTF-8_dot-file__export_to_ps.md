---
title: "Problem with graphviz: UTF-8 dot-file / export to ps"
date: 2007-04-29
forum: General Help
---

### Post by ortsanfang on 2007-04-29
I have a dot file containing a German umlaut (Ö) which leads me into trouble when I run dot to create a PostScript file.

example.dot
```

digraph test {
a -> b -> c;
A -> b;
a [label="Ökologie"];
b [label="Wertesystem"];
}

```

After running ```
dot -Tps example.dot -o example.ps
``` the label "Ökologie" isn't shown correctly. All non ASCII characters seem to make problems. My exemple.dot is UTF-8 encoded and I think graphviz uses unicode as default. I get correct png or pdf output files, only ps files can't handle the German umlaut. Does anybody know how to solve this issue?

---

### Post by kittekat on 2007-06-08
hello,

I run into the same problem. After some research in the web I found a hint:

[https://mailman.research.att.com/pipermail/graphviz-interest/2004q2/001490.html](https://mailman.research.att.com/pipermail/graphviz-interest/2004q2/001490.html)
in this mail a graphiz developer confirms, that the ->ps output can't handle utf-8 strings, but only latin-1 ones.

so as work around we can convert the utf-8 string to latin-1, eg: for perl as indicated in [http://perl-xml.sourceforge.net/faq/#encoding_conversion](http://perl-xml.sourceforge.net/faq/#encoding_conversion)

use Unicode::String;
$ustr = Unicode::String::utf8($string);
$latin1 = $ustr->latin1();

this solved the challenge :)

---


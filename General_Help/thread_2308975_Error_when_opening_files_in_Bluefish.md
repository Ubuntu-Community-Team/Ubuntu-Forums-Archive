---
title: "Error when opening files in Bluefish"
date: 2016-01-07
forum: General Help
---

### Post by Hardeep_Asrani on 2016-01-07
Hi,

I'm new here so this might now be the right place to post this question, so I apologize in advance.

Anyway, I'm getting the following error when trying to open files in Bluefish using this command:

```
bluefish /var/www/html/index.php
```

I also tried using -p, sudo and gksudo, but it's not working. 

Here's the error:

```
hardeep@the-dearth-star:/var/www/html$ bluefish -p index.php
Possible error in language file nameless-context / nameless-context / group / nameless-tag / c.html.css.main / group / }: id - / pattern } has ends_context=2, but has only 2 parent contexts
Possible error in language file nameless-context / nameless-context / group / nameless-tag / c.html.css.main / e.css.lbrace / nameless-context / </style>: id - / pattern </style> has ends_context=3, but has only 3 parent contexts
Possible error in language file nameless-context / nameless-context / group / nameless-tag: id </style> already exists
Possible error in language file nameless-context / nameless-context / group / ' / c.html.attrib.style.inner / ': id - / pattern ' has ends_context=2, but has only 2 parent contexts
Possible error in language file nameless-context / nameless-context / group / ' / c.html.attrib.style.inner / ": id - / pattern " has ends_context=2, but has only 2 parent contexts
Possible error in language file nameless-context / nameless-context / group / t.html.script / nameless-context / // / nameless-context / </script>: id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file nameless-context / nameless-context / group / t.html.script / nameless-context / e.html.js.blockcomment / nameless-context / </script>: id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file nameless-context / nameless-context / group / t.html.script: id </script> already exists
Language statistics for PHP from /usr/share/bluefish/bflang//php.bflang2
reference size          942.40 Kbytes
largest table 32354 (  8088.50 Kbytes)
total tables  97266 ( 24316.50 Kbytes)
contexts        342 (    16.03 Kbytes)
matches       15756 (   861.66 Kbytes)
blocks           14 (     0.44 Kbytes)


```

Any help will be appreciated. New to Ubuntu, and I'm loving this!

Regards,
Hardeep

---

### Post by sergio53 on 2016-01-07
Try oppenning with different applications such as gedit or geany to see if the file is corrupted.

---

### Post by Hardeep_Asrani on 2016-01-07
Already did, it's working fine with Gedit.

---

### Post by claracc on 2016-01-07
Instead of using commands to open the file, have you tried with the menu in the proper window of bluefish program?.

perhaps, this guide: [http://bluefish.openoffice.nl/manual/ch05s03.html](http://bluefish.openoffice.nl/manual/ch05s03.html) can help

---


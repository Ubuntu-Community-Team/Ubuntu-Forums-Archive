---
title: "Geany color schemes: explanation of terms?"
date: 2013-10-31
forum: General Help
---

### Post by vasa1 on 2013-10-31
I'm using Geany 1.23.1 from the software center.

I've downloaded additional color schemes from [https://github.com/kugel-/geany-themes](https://github.com/kugel-/geany-themes) and placed them in ~/.config/geany/colorschemes as specified by the installation instructions.

I've compared the various color schemes and am in the process of making my own but I'd appreciate help in understanding the terms used in the colorscheme file.

For example, here's a part of a colorscheme, gedit.conf:

```

# Programming languages
#-------------------------------------------------------------------------------

comment=#00f
comment_doc=comment
comment_line=comment
comment_line_doc=comment_doc
comment_doc_keyword=comment_doc,bold
comment_doc_keyword_error=comment_doc,italic

number=#f0f
number_1=number
number_2=#a52a2a;;true

type=#2e8b57;;true
class=number
function=default
parameter=function

keyword=number_2
keyword_1=keyword
keyword_2=keyword_1
keyword_3=keyword_1
keyword_4=keyword_1

identifier=default
identifier_1=identifier
identifier_2=identifier_1
identifier_3=identifier_1
identifier_4=#008a8c

string=number
string_1=string
string_2=string_1
string_3=;;true;false
string_4=;;false;true
string_eol=string_1,italic

```

By trial and error, I figured out what some of them do. I replace the right-hand part of each line with a unique color and see where that pops up in a variety of different filetypes. Filetypes I looked at include .markdown, .css, .xml/html, .js, .py, .rc, .sh, and .svg.

But my question is this: is there any technical resource to explain when,say, **identifier** would be used as opposed to **identifier_1**, or **identifier_2**, or **identifier_3**, or **identifier_4**. 

I looked at file:///usr/share/doc/geany/html/index.html but that doesn't have the information I'm looking for.

---


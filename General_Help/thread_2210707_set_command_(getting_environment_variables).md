---
title: "set command (getting environment variables)"
date: 2014-03-12
forum: General Help
---

### Post by shestero on 2014-03-12
In my Ubuntu 12.04 LTS the "set" command after printing environment variables write some long source code.
It begins so:
_ImageMagick () 
{ 
    local cur prev;
    _get_comp_words_by_ref cur prev;
    case $prev in 
        -channel)
            COMPREPLY=($( compgen -W 'Red Green Blue Opacity \
                Matte Cyan Magenta Yellow Black' -- "$cur" ));
            return 0
        ;;
.............

---

### Post by Lars Noodén on 2014-03-12
The excerpt you show there would be a [function](http://tldp.org/LDP/abs/html/functions.html).  A function can be called the same way that an alias can be.  However, I vaguely recall reading somewhere that functions are preferable to aliases.

---

### Post by shestero on 2014-03-12
Yes. There are also many other functions. The question is why are they there.
I expect "set" returns only the list of current environment variables.

---


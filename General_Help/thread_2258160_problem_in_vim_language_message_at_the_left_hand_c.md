---
title: "problem in vim language message at the left hand corner"
date: 2014-12-25
forum: General Help
---

### Post by richard_lee on 2014-12-25
[COLOR=#333333][FONT=Ubuntu]My left hand corner language message cannot display.
I have try to edit /ETC/VIM/VIMRC and add the following code.However it don't work. [/FONT][/COLOR]
source $VIMRUNTIME/delmenu.vim
language messages zh_TW.utf-8
[ATTACH=CONFIG]258783[/ATTACH]

Anyone can help for this?

---

### Post by schragge on 2014-12-25
On a pristine vim installation when you invoke vim without a file name to edit there's no messages in the bottom left corner at all, at least in the en_US.UTF-8 locale. Do you still get it when invoking vim like this?
```
LC_ALL=C vim
```
If that message is specific to your locale you probably should ask about it at [http://www.ubuntu-tw.org](http://www.ubuntu-tw.org)

---

### Post by richard_lee on 2014-12-29
For example,when you press "I" to insert the text.The left corner should display something.

---

### Post by schragge on 2014-12-29
Ah understood. So, when pressing "I" you expect to see something like "-- &#25554;&#20837; --".
I suppose your ~/.vimrc should contain something like (found on the Net)
```

set nocompatible 
                                
"&#35774;&#23450;&#25991;&#20214;&#32534;&#30721;&#31867;&#22411;&#65292;&#24443;&#24213;&#35299;&#20915;&#20013;&#25991;&#32534;&#30721;&#38382;&#39064;
scriptencoding utf-8
set encoding=utf-8
set fileencodings=ucs-bom,utf-8,chinese,taiwan,latin1
set fileencoding=utf-8
let &termencoding = &encoding

"&#36741;&#21161;&#26174;&#31034;
set showcmd 
set showmatch
set showmode

```

---


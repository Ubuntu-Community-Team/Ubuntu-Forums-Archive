---
title: "Key mapping with several command in vim"
date: 2013-02-20
forum: General Help
---

### Post by Cyril4133 on 2013-02-20
Hi,

I want my code to be saved and then be build after pressing F2, but if I type:

```
:map <F2> :wa <CR><esc> | :make <CR><CR>
```

I face the following message

```
/bin/bash: -c: line 0: syntax error near unexpected token `<'
/bin/bash: -c: line 0: `make <CR> <CR> 2>&1| tee /tmp/vYcfR5W/0'

shell returned 1

```

Thank you

---


---
title: "Cannot use read from zsh: -p: no coprocess"
date: 2015-09-16
forum: General Help
---

### Post by CkDGTAT on 2015-09-16
Hi,

I am not able to use read with the -p option in zsh, though it works with bash. Can you explain why? 

Thank you.

```


#!/bin/bash

function fun(){

 read -e -p "name: " -i name
 read -e -p "id: " -i id
 read -e -p "phone: " -i phone
sudo echo $name $id $phone >> ~/file
}

$ fun
$ fun:read:2: -p: no coprocess




```

---

### Post by steeldriver on 2015-09-16
Because the builtin 'read' command in zsh is different from the builtin 'read' command in bash?

bash:
```

      -p prompt output the string PROMPT without a trailing newline before
                attempting to read

```

zsh
```

     -p 
            Input is read from the coprocess. 

```

---

### Post by CkDGTAT on 2015-09-19
```
read variable_name\?"prompt: "
```

---


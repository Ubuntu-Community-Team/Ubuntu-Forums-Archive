---
title: "How can I source a bash function named by its filename?"
date: 2015-09-22
forum: General Help
---

### Post by CkDGTAT on 2015-09-22
Hi,

I would like to source a file ```
function_name.sh
``` with a function ```
source_that_function
``` that would directly create an alias ```
function_name
``` without necessarily using the  function instantiation syntax in it

That is,

```

$ cat function_name.sh

#!/bin/bash

echo ok

$  source_that_function function_name.sh
$ function_name
ok
$
```

---

### Post by sudodus on 2015-09-22
Like you do with simple 'one-line' aliases, you can enter the function code in **~/.bashrc**

Run ```
source ~/.bashrc
``` or start a new terminal window, and you can use the function by its name, just like an alias.

You can also make a temporary function like  the following example (in a terminal window)

```
function hi-there { echo "hello $USER"; }
```

and run it with

$ [COLOR="#0000FF"]hi-there[/COLOR]

Just a simple example. Of course, you would make something much more complicated that is written with several program lines :-)

---


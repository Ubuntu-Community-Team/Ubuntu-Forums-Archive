---
title: "Bash: one liner works, not in function"
date: 2023-11-27
forum: General Help
---

### Post by brent on 2023-11-27
I've found a wonderful bash one liner to search in pdf files, but once I put it in a functionin bashrc I get errors.
Works:
```
find . -iname '*.pdf' -exec sh -c 'pdftotext "{}" - | grep --with-filename --label="{}" --color -i "*een string*"' \; }
```
Doesn't:
```
zpdf() { find . -iname '*.pdf' -exec sh -c 'pdftotext "{}" - | grep --with-filename --label="{}" --color -i "*een string*"' \; }
```
I suspect the terminator, but e.g. ending the line with ```
\; ;}
``` doesn't result in a correct solution.

Bonusquestion: how should I pass a string to grep here? Normally I'd pass```
"*$@*"
```, but due to the subshell that won't work.

---

### Post by dragonfly41 on 2023-11-27
An alternative I like for content searching is ripgrep .. for multiple types ..

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

---

### Post by MAFoElffen on 2023-11-27
Try it written as
```

function zpdf() { 
    find . -iname '*.pdf' -exec sh -c 'pdftotext "{}" - | \
        grep --with-filename --label="{}" --color -i "*een string*"'
}

```
The "/" character in Bash is interpreted as a continuation character. ";" as a line termination character. 

In commandline, you push to get all in a single line, instead of multiple commands. In scripts, I push to expand things out for readability

---


---
title: "Combining sed and head/tail commands in bash script."
date: 2013-05-01
forum: General Help
---

### Post by Peterinall on 2013-05-01
Hello great folks,
  
     As the title says i want to join 2 or more sed and head/tail command in a script. How should i do it ?
I have ```
#!/bin/sh

for file in ./*.htm
    do echo $file
    sed -r 's_<font color="#800000">&nbsp;<a name="([1-9]|[1-4][0-9]|50)"></a>|\[([1-9]|[1-4][0-9]|50)\] \[<a href="#top">[A-Za-z. ]+</a>\]__g' "$file" >"$file"_new
    done

exit
```

Want to add
```
#!/bin/sh

for file in ./*.htm
    do echo $file
    tail -n +35 "$file" | head -n -11 > "$file"_new
    done

exit
```

I may have to add more so looking forward to grab the base idea.

Thanks in advance for any kind of help and suggestions.

---

### Post by Vaphell on 2013-05-01
something like this?
```
tail  -n +35 "$file" | head -n -11 | sed -r 's_...__g' > "$file"_new
```

---

### Post by Peterinall on 2013-05-01
Sorry for the silly question but can i add more sed commands to the line like
 ```

tail  -n +35 "$file" | head -n -11 | sed -r 's_...__g' -re 's_..._g' and so on..... > "$file"_new
```

Thanks you very much.

---

### Post by Vaphell on 2013-05-01
you can pipe as many commands as you wish
*cmd1 | cmd2 | sed | sed | sed *
though in case of sed you can indeed run multiple expressions at once
eg
*cmd1 | cmd2 | sed 's/.../.../g; s/.../.../g; s/.../.../g'*
-e does the same i think (i don't know if there is a functional difference between these 2 in some special cases, i usually go with the ; version)

example:
```
$ echo $'abc def ghi\naabcc ddeff gghii'
abc def ghi
aabcc ddeff gghii
$ echo $'abc def ghi\naabcc ddeff gghii' | sed -r 's/abc/#/g; s/def/@/g; s/ghi/%/g'
# @ %
a#c d@f g%i
$ echo $'abc def ghi\naabcc ddeff gghii' | sed -re 's/abc/#/g' -e 's/def/@/g' -e 's/ghi/%/g'
# @ %
a#c d@f g%i
```

---

### Post by Peterinall on 2013-05-01
Thank you very much for your time n help.

Regards

---


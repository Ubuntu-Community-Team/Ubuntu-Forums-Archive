---
title: "Invalid syntax"
date: 2022-08-31
forum: General Help
---

### Post by raleigh3 on 2022-08-31
When I run this, I get

 File "<string>", line 1
    print(1661967937.887067896 - )
                                 ^
SyntaxError: invalid syntax


```
end=$(date +%s.%N)    
runtime=$(python -c "print(${end} - ${start})")
##echo "Backup time was $runtime"
echo 'Backup time was $runtime' > /home/andy/Downloads/Backup_Times.txt
```

---

### Post by &amp;KyT$0P# on 2022-08-31
You didn't define [FONT=Courier New]${start}[/FONT] anywhere, so the shell substitutes the empty string in its place, which results in invalid Python code.  To fix that you need to define [FONT=Courier New]start[/FONT] as a numerical value in the shell portion of that script.

---

### Post by raleigh3 on 2022-08-31
Thanks. I added this.

```
start=$(date +%s.%N)
```

---

